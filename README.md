The Xeryon Python Library:
Contains the Protocols the encoder controlling the grating uses to communicate with the computer. The Xeryon.py file contains all the protocols for all such devices so check this if there's any fundamental issues with connections. All the control code for our monochromator is implemented in 'monochrom_control_code_draft.py' in 'ourGUI'.

If you've got any issues with your control code trying to find the Xeryon.py file, we managed to fix it by putting it directly in our python site packages (probably not best practice, but it works). 
follow these steps:
1. in Command Prompt type,  python -m site
2. Find and go to directory ending in .../Lib/site-packages
3. Copy the Xeryon.py file into this directory

Better practice would be to set up a virtual environment containing all these packages for all software to do with the monochromator. Ask John Waiton how to do this lol.

ourGUI:
The "monochrom_control_code_draft.py" has all the functions that you'd need for any program controlling the monochromator. It calls the protocols from the Xeryon library and implements them into functions that make them more readable. E.g. step() moves in a specific direction by a given step size, goTo() moves the grating to a specified angle between -15 and 15. It also handles safety checks when the grating is moving, and handles safe bootup and disconection.

The program "monochrom interface draft.py" that connects to the monochromator and loads a user interface to control the grating position manually. We've found this to be a lot more reliable than the company's UI. It loads the control code above and uses the defined functions. This can be improved significantly: add a display that shows the wavelength that should be on the output slit for a given angle. Make it so the presaved angle positions don't reset when closing the program (they're currently just saved in a python list)

