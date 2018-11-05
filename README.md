# Blum-Goldwasser-cryptosystem
CSCI 4230: Cryptography and Network Security, Homework 3

Implementation of the Blum–Goldwasser asymmetric key encryption algorithm 



### The repository

This repository contains two implementations of the Blum–Goldwasser asymmetric key encryption algorithm:

- BG.py: this implementation simply uses libraries like random and numpy to make the calculations needed for the algorithm. It is a standalone and can be run anywhere
- BG-wolfram.py: this implementation uses the Wolfram Alpha API. I was not aware that pow can take in 3 arguments, the third of which is the modular base, and so I decided the best way to make calculations like (36858^289) mod 547. The first implementation simply uses the line pow(36858,289,547), while this implementation queries wolfram alpha to make the calculation for us.

### The wolframalpha API

The top of the code has the following:

```
try:
    import wolframalpha
    print('\nModule was installed')
except ImportError:
    print('\nThere was no such module installed')
    userInput = input("Would you like to install wolframalpha? It's needed for our calcalations? \n(y/n) ")
    yesOptions = ["y", "Y", "yes", "YES"]
    if userInput in yesOptions:
        os.system("pip install wolframalpha")
        import wolframalpha
    else:
        print("This script can't run without installing this package. Goodbye!")
        sys.exit() 
client = wolframalpha.Client("AppID")
```

This will check to see if the user has the wolfram alpha package already installed, and if not, will ask them if they want to install it. If they don't it will exit the program. If they do, it will install it and then run the program.



### Running the code

To run the code, simply pick which implementation you wish to choose. If you want the standalone implementation, simply type the following in a terminal:

```
python server.py
```

The same can be done with BG-wolfram.py, but with one thing to keep in mind: the API requires a Wolfram Alpha appID to create the client. This is designated in the code by the following line: 

```
client = wolframalpha.Client("AppID")
```

Simply create a user account on developer.wolframalpha.com, create a widget, and plug in your AppID into the designated spot.