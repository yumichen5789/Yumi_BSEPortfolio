# Ultrasonic Theremin
Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!

You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Yumi C | High School for Dual Language and Asian Studies | Electrical Engineering | Incoming Senior

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/Gvu_VZZnCaM?si=l0y226hM3NC3DdzU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

In this milestone, I completed the basis of the project. I connected the ultrasonic sensor and buzzer to the arduino and added the code to Arduino IDE. Now the project works. How it works is you place your hand at different distances from the ultrasonic sensor and the buzzer will play different frequencies of sound. The sounds I chose were the notes C,D,E,F,G,A,B from the C major scale and I also added a high frequency of 800hertz inside the code to make the sounds more distinguishable. The first challenge I faced was not building the hardware correctly, after I fixed that I realized the hardware wasn’t connected to the software. Though they may be fundamentary steps on a project, as a beginner, these issues have taught me quite a bit in focusing on detail. The next challenge I encountered was in the code. The documentation I followed for this project has their pins set to 9 for their piezo buzzer however mine was smaller in size so it could only reach pin 11. The buzzer didn’t work because in the code the pins were still at pin 9 and after realizing and changing the pin to11, the buzzer worked. My plan for modifications is trying to make the buzzer play a short song.  


# Schematics 
![Headstone Image](Screenshot 2026-07-24 145705.png)
![Headstone Image](Screenshot 2026-07-24 145737.png) 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
const int trigger = 5;
const int echo = 4;


const int piezo = 11;


int distance = 0;
int distanceHigh = 0;


int lengthOfScale = 0;


int note = 0;


//C Major scale
int scale[] = {
  262, 294, 330, 349, 392, 440, 494, 800
};


void setup() {
  pinMode(trigger, OUTPUT);
  pinMode(echo, INPUT);


  while (millis() < 5000) {
    digitalWrite(trigger, HIGH);
    digitalWrite(trigger, LOW);
    distance = pulseIn(echo, HIGH);


    if (distance > distanceHigh) {
      distanceHigh = distance;
    }
  }


  for (byte i = 0; i < (sizeof(scale) / sizeof(scale[0])); i++) {
    lengthOfScale += 1;
  }
}


void loop() {
  digitalWrite(trigger, HIGH);
  digitalWrite(trigger, LOW);


  distance = pulseIn(echo, HIGH);


  note = map(distance, 250, distanceHigh, scale[0], scale[lengthOfScale - 1]);


  for (byte j = 0; j < (lengthOfScale); j++) {


    if (note == scale[j]) {
      tone(piezo, note);
      break;
    }
    else if (note > scale[j] && note < scale[j + 1]) {
      note = scale[j];
      tone(piezo, note);
      break;
    }
  }
  delay(30);
}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Arduino UNO | Connects the piezo buzzer, ultrasonic sensor and code | $27.60 | <a href="https://www.newark.com/arduino/a000066/dev-board-atmega328-arduino-uno/dp/78T1601?COM=ref_hackster&CMP=Hackster-NA-project-b56de4-Jul-26"> Link </a> |
| Buzzer, Piezo | Releases difference frequencies of sound | $25.29 | <a href="https://www.newark.com/moflash-signalling/ae20m-24fa/buzzer-piezo-cont-90db-2-9khz/dp/15P1093?COM=ref_hackster&CMP=Hackster-NA-project-b56de4-Jul-26"> Link </a> |
| Ultrasonic Sensor - HC-SR04 (Generic) | Detects how far a objects is away from the sensor | $5.25 | <a href="https://www.sparkfun.com/ultrasonic-distance-sensor-hc-sr04.html"> Link </a> |
| Jumper wires (generic) | Used in the adruino to connect the piezo buzzer and ultrasonic sensor to pins | $3.87 | <a href="https://www.newark.com/adafruit/759/wire-gauge-28awg/dp/88W2571?COM=ref_hackster&CMP=Hackster-NA-project-b56de4-Jul-26"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
