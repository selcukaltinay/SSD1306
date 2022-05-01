**How to use SSD1306 Oled Display?**

[General Description:]{.underline}

> SSD1306 is a single-chip CMOS OLED/PLED driver with controller for organic / polymer light emitting diode dot-matrix graphic display system. It consists of 128 segments and 64commons. This IC is designed for Common Cathode type OLED panel. The SSD1306 embeds with contrast control, display RAM and oscillator, which reduces the number of external components and power consumption. It has 256-step brightness control. Data/Commands are sent from general MCU through the hardware selectable 6800/8000 series compatible Parallel Interface, I2C interface or Serial Peripheral Interface. It is suitable for many compact portable applications, such as mobile phone sub-display, MP3 player and calculator, etc. [1][2]

1.  [First we need to include our libraries.]{.underline}

``` c
#include "ssd1306.h"
#include "i2c-lcd.h"
#include "fonts.h"
#include "bitmap_lcd.h"
```

2.  [If you want to add images with a bitmap file, you can use the links below. Otherwise, skip this step.]{.underline}

[Online Bitmap Converter](https://www.mischianti.org/images-to-byte-array-online-converter-cpp-arduino/)

[Online RGB to BW Converter](https://convertimage.net/online-photo-effects/black-and-white-photo-fx.asp?i=20220501-154138-rfuef)

3.  [Insert the code block for init.]{.underline}

    ``` c
    lcd_init ();
    check=SSD1306_Init();
    SSD1306_Fill(0);
    SSD1306_UpdateScreen();
    ```

4.  [Now you can use the write functions.]{.underline}

    ``` c
    SSD1306_GotoXY(0, 27);
    SSD1306_Puts(text, &Font_11x18, 1); 
    SSD1306_UpdateScreen();
    ```

5.  [To draw bit map.]{.underline}

    ``` c
    SSD1306_Fill(0);
    SSD1306_DrawBitmap(0, 0, selcuk,128, 64, 1); // this function draws my photo
    SSD1306_UpdateScreen();
    ```

    [***References***]{.underline}

> 1.  S. Systech, "SOLOMON SYSTECH SEMICONDUCTOR TECHNICAL DATA SSD1306 128 x 64 Dot Matrix OLED/PLED Segment/Common Driver with Controller," 2008, Accessed: May 01, 2022. [Online]. Available: <http://www.solomon-systech.com.>
> 2.  "Stm32 Oled Ekran Kullanımı
>     Nisan 25th, 2022."
>     <https://elektronikatolyem.com/2019/12/28/stm32-oled-ekran-kullanimi/> (accessed
>     May 01, 2022).
