# Audio Playback System Notes  

## DAC & DMA  
- Load audio using DAC  
- Use DMA to transfer data without CPU involvement (event-triggered)  
- Target MCU: STM32G0  

## Buffering  
- Use a double buffer: load one while playing the other  
- 16 sounds total  

## Storage  
- Use a microSD card  
- FATFS middleware  
- Create a dedicated folder for sounds  
- Raw data stored on SD card  
- Filenames are in hexadecimal  

## Playback Logic  
- Continuous playback when holding down a button → implement looping  

## Button Input  
- Button value comes from CAN (currently just a boolean)  
- 4 GPIOs for 4-bit input  
- Use interrupts to detect button presses  

## Audio Output  
- LM356 buffer to receive DAC signal for playback  
- Likely <1 gain op-amp (LM324, quad op-amp)  
- 3.5mm jack may introduce other voltage considerations  

## Additional Considerations  
- Use a timer for double buffer reading  
- Wavetable for testing  
- Power: 5V for everything  
