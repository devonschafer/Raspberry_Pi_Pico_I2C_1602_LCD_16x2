# Raspberry_Pi_Pico_I2C_1602_LCD_16x2
Simple usage of the Pico with I2C 1602 LCD with MicroPython

I simplified other peoples work becuase I found this really confusing. Since the Pico is still so new I would like to help other people with this.

To start understand that I am using the Qapass 1602A with i2c backpack, like the picture, your LCD may vary. I was having trouble with my exact setup and I feel I am not alone.

I wired up mine just like the picture and this is important because one digit in this code (main.py) needs to be wired just like this.
main.py, line 14. '''i2c = I2C(0, scl=Pin(1), sda=Pin(0), freq=400000)'''
The zero after '''I2C( ''' is what I'm talking about. This zero means that you have SDA, SCL on 0, 1.( Like a default )

For the code setup. This is how I did it. 
I am using Thonny on a raspberry pi 4 to connect to my Pico.
You will need to copy esp8266_i2c_lcd.py, lcd_api.py and save them to the pico under the lib folder. If you do not have a lib folder save them to the pico's only folder and the pico should create the lib folder for you. If not just make a "lib" folder. ( Don't change any names unless you know what you're doing )

Now copy main.py and save it to your pico's main folder as main.py

After doing this you should have a working LCD screen running a test program.
---------------You don't have to go futher I am just listing my source below to give credit.--------------------------

To give credit, this is where I found the code. All this code in this repo is a bit heavy for a beginner, but here it is.
https://github.com/dhylands/python_lcd

I only used esp8266_i2c_lcd.py, lcd_api.py, esp8266_i2c_lcd_test.py( renamed to main.py ).

NOTE: My contrast on the screen was all wrong. I could see words on the screen, but they appeared a dark color(not too visible). I found out that the on board potentiometer was bad from factory. I cut it off and measuered to find that a 3.6k ohm resistor is perfect contrast for me. I didn't have a 3.6 k resistor so I soldered two 1k resistors in series to achieve 3k which was still suitable for me. 
How I soldered on the resistor (if you should have to). 
If you remove the pot and hold the screen exactly in the same orientation as the image in the repo. You will see three contacts. one is to the bottom left (closest to the micro chip), two is on the top middle, and the third is bottom right (closest to the VCC pin). I soldered the resistor between the top and bottom right contacts. Hope this helps.
