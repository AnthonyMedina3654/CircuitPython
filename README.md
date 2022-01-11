# CircuitPython
This repository will actually serve as a aid to help you get started with your own template.  You should copy the raw form of this readme into your own, and use this template to write your own.  If you want to draw inspiration from other classmates, feel free to check [this directory of all students!](https://github.com/chssigma/Class_Accounts).
## Table of Contents
* [Table of Contents](#TableOfContents)
* [Hello_CircuitPython](#Hello_CircuitPython)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_LCD](#CircuitPython_LCD)
* [NextAssignmentGoesHere](#NextAssignment)
---

## Hello_CircuitPython

### Description & Code
Goal is to make the neopixel change colors, at the end changing color after a specific amount of time. 


```python
Code goes here
import board
import neopixel
import time

dot = neopixel.NeoPixel(board.NEOPIXEL, 1)
print("Make it red!")

while True:
    dot.fill((0, 0, 255))
    time.sleep(.30)
    dot.fill((153, 0, 255))
    time.sleep(.30)
    dot.fill((255, 0, 0))
    time.sleep(.30)

```


### Evidence
<img src="https://user-images.githubusercontent.com/71345181/133625107-908011a3-f2ad-4a12-a524-92a9d155694c.jpg" alt="ledlightpic"/>

### Reflection
the color change wasnt an issue for me, but I could not quite get the timed change to work for a couple attempts. 



## CircuitPython_Servo

### Description & Code
This was the first time ive ever used compasative touch, and it was difficult to wrap my head around.
```python
 if touchA3.value:
        print("A3 Touch")
        for angle in range(0, 180, 5):
            my_servo.angle = angle
        time.sleep(0.3)
    if touchA4.value:
        print("A4 Touch")
        for angle in range(180, 0, -5):
            my_servo.angle = angle
        time.sleep(0.3)
```

### Evidence
![ezgif com-gif-maker (1)](https://user-images.githubusercontent.com/71341888/133626092-f7522970-bf4d-418d-9e07-07f4378ee65e.gif)
Image credit goes to [Graham Stevenson](https://github.com/Graham913/CI)

### Reflection

while the wiring was easy, learning python, especially compasitive touch, was kind of difficult. i still do not understand how the code is able to understand when the wire is touching something. 



## CircuitPython_Distance_Sensor
### Description & Code

have neopixel change color based on distance detected by sensor, neopixel fades on a 3 color pattern based on distance of object from sensor

```python
Code goes here
import time
import board
import adafruit_hcsr04
import neopixel
import simpleio

sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.D5, echo_pin=board.D6)
dot = neopixel.NeoPixel(board.NEOPIXEL, 1)
dot.brightness = 0.5

cm = 0
print("new code!")

while True:
    try:
        cm = sonar.distance
        print((cm,))

        if cm < 5:
            dot.fill((255, 0, 0))
        elif cm < 20:
            r = simpleio.map_range(cm, 5, 20, 255, 0)
            g = 0
            b = simpleio.map_range(cm, 5, 20, 0, 255)
            dot.fill((int(r), int(g), int(b)))
        else:
            r = 0
            g = simpleio.map_range(cm, 20, 35, 0, 255)
            b = simpleio.map_range(cm, 20, 35, 255, 0)
            dot.fill((int(r), int(g), int(b)))
    except RuntimeError:
        print("Retrying!")
    time.sleep(0.1)
```

### Evidence
<img src="https://user-images.githubusercontent.com/71345181/134514464-caa97a3e-3cad-4ae1-9206-1270b65ca029.gif" alt="ezgif com-gif-maker (1)"/>

Image credit goes to [Graham Stevenson](https://github.com/Graham913/CI)


### Reflection
the distance sensor was hard for me because i could not stay on task to save my life, but we're here now and finished. the old code i had available to me helped a lot.
