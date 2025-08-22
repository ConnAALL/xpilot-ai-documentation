# XPilot-AI Examples

### General

**Xpilot-AI** works by allowing a programmer to easily inject code within the framework of the game during the same time that the system would read user input and draw the current frame. We refer to this code that will be injected as the **AI loop**. There are many functions included in Xpilot-AI which allow a programmer to effortlessly read information from the XPilot client and send instructions to the ship in the same way a player could see the display and use the keyboard and mouse.

> **Important note:** If the Xpilot-AI libraries are not installed to your library path, then you will need to set the library path to where they are located.

For example, in **Ubuntu**, if the bots are located in the same folder as the library `.so`, as is the default method, the following line should be run once, before executing the bot:

```bash
export LD_LIBRARY_PATH=.
```

If you get errors about libraries, try that first!

### Server

The various XPilot clients and servers are, on the whole, compatible with one another. Our custom server adds `switchBase`, which is helpful for artificial learning systems.

We are working to bring our modified server code up to date, for now you can use the previous server.

This is how to run a basic server:

```bash
./xpilots -map maps/lifeless.xp -noQuit -switchBase 1
```

## Programming Languages

### C

**Spinner.c**

```c
#include "cAI.h" //This allows us to use the AI functions
AI_loop() { //This must be the name of the AI loop in C
  turnLeft(1); //Bot code goes here
}
int main(int argc, char *argv[]) { //Called when bot is run
  return start(argc, argv); //Starts Xpilot-AI
}
```

**To compile:**
```bash
gcc Spinner.c libcAI.so -o Spinner
```

**To run:**
```bash
./Spinner
```

### Java

**Spinner.java**

```java
class Spinner extends javaAI { //"extends" allows us to use the AI functions
        @Override //Tells Java to override the existing AI_loop
        public void AI_loop() { //This must be the name of the AI loop in Java
                turnLeft(1); //Bot code goes here
        }
        public Spinner(String args[]) { //Required for superclass javaAI
                super(args);
        }
        public static void main(String args[]) { //Called when bot is run
                String[] new_args = {"-name","Spinner"}; //Sets args
                Spinner spinner = new Spinner(new_args); //Starts Xpilot-AI
        }
}
```

**To compile:**
```bash
javac Spinner.java
```

**To run:**
```bash
java Spinner
```

### Python

**Spinner.py**

```python
import libpyAI as ai #This allows us to use the AI functions
def AI_loop(): #Our method to be called as AI_loop, can be anything
  ai.turnLeft(1) #Bot code goes here
ai.start(AI_loop,["-name","Spinner"]) #Starts Xpilot-AI
```

**No compilation necessary**

**To run:**
```bash
python3 Spinner.py
```

### Racket

**Spinner.rkt**

```racket
#lang racket
(require "rktAI.rkt") ;This allows us to use the AI functions
(start (lambda () (turnLeft 1)) '("-name" "Spinner")) ;Starts Xpilot-AI
```

**No compilation necessary**

**To run:**
```bash
racket Spinner.rkt
```
