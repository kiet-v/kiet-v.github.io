---
author: "Kiet Vu"
title: "★ Nixie Tube Display"
date: "2024-11-03"
description: "Building a nixie number randomizer"
FRtags: ["markdown", "css", "html", "themes"]
FRcategories: ["themes", "syntax"]
FRseries: ["Themes Guide"]
aliases: ["migrate-from-jekyl"]
ShowToc: true
TocOpen: true
weight: 5
---
<iframe width="800" height="480" src="https://www.youtube.com/embed/IyNu2J0NiTc?si=-T2R4KzOZgVSdeNV" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Design Musings
I have known about nixie tubes for a while, and it is great to finally make something with them myself! I went to Ebay and bought a couple of IN-12 tubes (there are larger variants such as IN-14 & IN-18, I happen to like the design of this one due to its compactness). I was planning to make a clock, but ended up making something slightly different for this iteration. 

This project into two separated parts: The shift register/control circuit and the high voltage boost converter. For IN-12 tube, the supply requirement is ~165VDC, ~5mA per tube. The voltage supply is a normal DC wall plug (12V, 1A). I set up my converter to be able to deliver up to 25 mA of current, which is sufficient to power all the tubes. 

For shift register circuit, I use HV5622 which is a high voltage serial-to-parallel converter that can support up to 230V output. The shift register is controlled by an Arduino Nano (through a 5-12 V level shifter). 

This is also my first project trying to use EasyEDA & JLCPCB assembly capability. I think it's usable and that the integrated library is certainly very convenient. 

You can find more information in the following sections, which include the schematics, code and test. 

# Schematics and PCBs
- Nixie Supply Board Schematic & Layout
<embed src="/images/nixie/Schematic_Nixie-Driver-v1.pdf" type="application/pdf" width="100%" height="525px" />
<embed src="/images/nixie/pwrboard_2d.png" width="100%"/>
<embed src="/images/nixie/pwrboard_3d.png" width="100%"/>
<br></br>
- Nixie S/R Board Schematic & Layout
<embed src="/images/nixie/Schematic_Nixie-SR-v1.pdf" type="application/pdf" width="100%" height="525px" />
<embed src="/images/nixie/sr_board_2d.png" width="100%" />

# Prototype Testing
Number cycling test (integration test of shift register and power supply)
<iframe src="https://www.dropbox.com/scl/fi/nlr2nv6076aqqs3yn0a2e/NixiePrototype.MOV?rlkey=bidid1dwio8k0830phsx8nluj&st=6wumedts&raw=1" height="480px" width="640px" allowfullscreen></iframe>

# Gallery 
<embed src="/images/nixie/nixie-front.png" width="100%"/>
<embed src="/images/nixie/nixie-side.png" width="100%"/>
<embed src="/images/nixie/nixie-top.png" width="100%"/>

# Code Logic 
```c
#define PIN_DATAIN_MASK (1 << 6)  // D7
#define PIN_CLOCK_MASK (1 << 7) // D6
#define PIN_LATCH_MASK (1 << 5) // D5

/*
Position: 
Arrangement: -> [1,2,3...9,0]
HV1 - HV10: IN1: minute smol -> [1,2,3...9,0]
HV11 - HV20: IN2: minute big  -> [1,2,3...9,0]
HV21 - HV30: IN3: hours smol -> [1,2,3...9,0]
HV31 - HV32: IN4: hours large - >[1,2]
Strat: 
Store each digit separatedly 
every 60000 milliseconds: 
bit shift HV 1 every cycle:
bit shift HV 2 if HV 1 is zero 


*/ 

void setup() {
  DDRD = DDRD | B11111100;  
  delay(350);
}

uint32_t time_array[4] = {0b01, 0b0000001000, 0b0000000001, 0b0000000001};
unsigned long interval = 1000; 
unsigned long interval_min = 5000;
unsigned long interval_max = 180000; 
unsigned long last = 0;
bool need_time_update = true; 
uint32_t value_to_SR = 1; 

void loop() {
  // put your main code here, to run repeatedly:
  unsigned long now = millis();
  
  // Check if the interval has passed
  if (now - last >= interval) {
    for (int index = 0; index < random(5,60); index++){
      random_update_sequence(false);
      delay(40);
    }
    randomSeed(analogRead(A4));
    random_update_sequence(false);
    last = now;
    interval = random(interval_min, interval_max);
}
}


void write_to_sr_uint32(uint32_t value) {
  // set value, clock up and down, then change value and repeat
  uint32_t shifted_val = value; 
  for (int i = 0; i<=31; i++){
    PORTD |= PIN_CLOCK_MASK; //set clock high
    delayMicroseconds(2); 
    bool bit_val = ((shifted_val & 1) == 1);
    if (bit_val == true) {
      PORTD |= PIN_DATAIN_MASK; // set the datain line to HIGH
    }
    else {
      PORTD &= (~PIN_DATAIN_MASK); // set the datain line to LOW
    }
    delayMicroseconds(2);

    PORTD &= (~PIN_CLOCK_MASK); //set clocl low. data stored.  
    delayMicroseconds(2);
    shifted_val = shifted_val >> 1; //shift for the next round 
  }
  
}

void set_latch_up(){
  PORTD |= PIN_LATCH_MASK;
}

void set_latch_down(){
  PORTD &= (~PIN_LATCH_MASK);
}

uint32_t update_time_value(uint32_t time_array[], size_t size){
  uint32_t time_array_old[size] = {time_array}; 
  uint32_t zero_bit_location = 1 << 9; // 
  uint32_t one_bit_location = 0b01; //location of digit 1
  time_array[3] <<= 1; // always shift this bit 
  if (time_array[3] == (1 << 10)){
    time_array[3] = one_bit_location;  
  } 

  
  //minute digit at zero position 1..9 -> 0. Increment the next one 
  if (time_array[3] == (zero_bit_location) && (time_array_old[3] != time_array[3])){
    (time_array[2] != (zero_bit_location)) ? (time_array[2] <<= 1) : (time_array[2] = one_bit_location); 
  } 
// minute digit at 'overflow' location 
  

  if (time_array[2] == (1<<5) && (time_array_old[2] != time_array[2]) ) { 
    time_array[2] = zero_bit_location;  
    (time_array[1] != (zero_bit_location)) ? (time_array[1] <<= 1) : (time_array[1] = one_bit_location); 
  } 

  if (time_array[1] == (zero_bit_location) && (time_array_old[1] != time_array[1])){
    (time_array[0] != (0b0)) ? (time_array[0] <<= 1) : (time_array[0] = one_bit_location); 
  } 
// minute digit at 'overflow' location 
  // if (time_array[1] == (1 << 10)){
  //   time_array[1] = one_bit_location;  
  // } 

  if (time_array[0] == (1<<2) && (time_array_old[0] != time_array[0])){
    time_array[0] = 0b0; 
  } 

  uint32_t return_val = 0 | time_array[3] | (time_array[2] << 10) | (time_array[1] << 20) | (time_array[0] << 30);
  return return_val;
}

uint32_t update_array_random(uint32_t time_array[], size_t size, bool multi_digit){
  if (multi_digit){
    time_array[3] = (1 << random(0,9)) | (1 << random(0,9));
    time_array[2] = (1 << random(0,9)) | (1 << random(0,9)); 
    time_array[1] = (1 << random(0,9)) | (1 << random(0,9));
    time_array[0] = (1 << random(0,2)) | (1 << random(0,2));  
  } 
  else {
    time_array[3] = (1 << random(0,9));
    time_array[2] = (1 << random(0,9)); 
    time_array[1] = (1 << random(0,9));
    time_array[0] = (1 << random(0,2));  
  }
  

  uint32_t return_val = 0 | time_array[3] | (time_array[2] << 10) | (time_array[1] << 20) | (time_array[0] << 30);
  return return_val;

}
uint32_t convert_array_to_digit(uint32_t time_array[]){
  uint32_t return_val = 0 | time_array[3] | (time_array[2] << 11) | (time_array[1] << 21) | (time_array[0] << 31);
  return return_val;
}

 void readBit(String direction, long counter) {

      Serial.print(direction + "Binary Number: ");

      //loop through each bit
      for (int b = 32; b >= 0; b--) {

        byte bit = bitRead(counter, b);

        Serial.print(bit);

      }

      Serial.print(" Decimal Number: ");

      Serial.println(counter);

    }

uint32_t reverse_bits(uint32_t value) {
    uint32_t reversed = 0;  // Store the result

    for (uint8_t i = 0; i < 32; ++i) {
        // Extract the rightmost bit from value
        uint32_t bit = (value >> i) & 1;
        
        // Set this bit in the reversed number at the correct position
        reversed |= (bit << (32 - i - 1));
    }

    return reversed;
}

void random_update_sequence(bool multi_digit){
  value_to_SR = update_array_random(time_array, sizeof(time_array), multi_digit); 
  write_to_sr_uint32(reverse_bits(value_to_SR));
  set_latch_up(); // latch down is when the data is shifted!
  delayMicroseconds(10); 
  set_latch_down(); //turn the shift register!
}
```

