# Voice Assistant with AI
This project uses Rasberry Pi and ChatGPT to create a voice assistant. This voice assistant listens to voice commands and has an interaction with the user, also responding with a voice.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Rushil S. | Monta Vista High School | Computer Science | Incoming Sophomore |

<!--
**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**
-->

<!-- Figure out images later -->
![Headstone Image](/Rushil.jpg)


<!--
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

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

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/CaCazFBhYKs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project

# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
-->

# Starter Project

This project uses a pushbutton to toggle between two LED lights. The pushbutton is connected to a 5V pin, a ground through a resistor, and a digital pin. The digital pin allows for the pushbutton to be used as an input mechanism, as connecting the pushbutton to the digital pin allows for the pushbutton's state (pushed or not) to be continuously read. There are 2 LEDs which both have the same setup in terms of connection to the Arduino board. Each LED has a direct connection to a ground, and then through a resistor, connects to a digital pin. These digital pins allow the LED's state (on or off) to be controlled by the code. All of the cables, resistors, LEDs, and pushbuttons have been soldered into the protoshield. For items that aren't connected in the protoshield (which has specific rows and columns that are automatically connected due to metal lining), solder is used to form those connections between the items. There are pins soldered into the protoshield that extend all analog, digital, etc pins from the Arduino board. 

The code uses setup() to initialize the 2 LEDs as outputs and the pushbutton as an input. This is all done using their ports so the computer understands where the LEDs and pushbutton are. In loop() the button's current state is read, and if it is not pressed (which returns LOW in digitalRead()) then the first LED is turned on and the second LED is turned off. Otherwise, if it is pressed (which returns HIGH in digitalRead()), then the first LED is turned off and the second LED is turned on.
```c++
// constants because they are pin numbers
const int BUTTON_PIN = 7;  // the number of the pushbutton pin
const int LED_PIN =  9;   // the number of the LED pin
const int LED_PIN2 = 13; // number of LED pin # 2
bool isToggled = false; // checks which LED should be turned on (False -> LED 1, True -> LED 2)
bool alreadyRan = false; // checks if loop is running multiple times on one button press so lights don't continuously switch

// buttonstate changes
int buttonState = 0;   // variable for reading the pushbutton status

void setup() {
  // initialize the LED pins as outputs:
  pinMode(LED_PIN, OUTPUT);
  pinMode(LED_PIN2, OUTPUT);
  // initializing the pushbutton as an input device
  // the pull-up input pin will be HIGH when the button is pressed and LOW when the button is not pressed.
  pinMode(BUTTON_PIN, INPUT_PULLUP);
}

void loop() {
  // reads the state of button (pushed/not pushed) --> HIGH/LOW
  buttonState = digitalRead(BUTTON_PIN);
  
  // control LED according to the state of button
  if(buttonState == HIGH && !alreadyRan)         // If button is not pressed
  {
    isToggled = !isToggled; // swaps toggle to other side
    if (isToggled)
    {
      digitalWrite(LED_PIN2, HIGH); // turn on LED # 2
      digitalWrite(LED_PIN, LOW); // turn off LED # 1
    }
    else
    {
      digitalWrite(LED_PIN, HIGH); // turn on LED # 1
      digitalWrite(LED_PIN2, LOW); // turn off LED # 2
    }
    alreadyRan = true; // This will make it so if statement isn't entered multiple times in one button press
  }
  else if (buttonState == LOW)
  {
    alreadyRan = false; // Allows if to be entered again since button has been released now
  }
}
```
