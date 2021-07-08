# SFE_MicroOLED for mbed OS 6

Driver and Graphics library for MicroOLED 0.66" (64x48 pixels) display with SSD1306 controller. Display can be obtained from Sparkfun or from diverse Chinese sellers (similar displays) via Aliexpress. Display is driven via SPI. The library can be very easily adapted to other OLED displays (up to 128x64 pixel) with SSD1306 controller by setting defines and changing controller init commands accordingly.

Small test-program that briefly shows the basic usage of the library:

```cpp
#include "mbed.h"
#include "SFE_MicroOLED.h"
 
DigitalOut myled(LED1);
SPI my_spi(p5, p6, p7);
MicroOLED my_oled(my_spi, p11, p10, p9);
 
int main() {
    my_oled.init(0, 8000000);
    my_oled.clear(ALL);
    my_oled.puts("Hello all!");
    my_oled.circle(16, 31, 16);
    my_oled.line(0, 9, 63, 47);
    my_oled.rectFill(33, 32, 8, 8);
    my_oled.display();
    while(1) {
        myled = 1;
        wait(0.2);
        myled = 0;
        wait(0.2);
    }
}
```
