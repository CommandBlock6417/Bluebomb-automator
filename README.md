# Bluebomb-automator
#### Based on [Fullmetal5's bluebomb exploit](https://github.com/Fullmetal5/bluebomb/releases) and [twosecslater/urmum-69's bluebomb helper shell script.](https://git.snopyta.org/twosecslater/bluebomb-helper)
## Introduction:
  Bluebomb-automator is an automated frontend for the Bluebomb Wii bluetooth exploit designed for use on headless Raspberry Pi single board computers and mass Wii console softmodding. It requires little technical knowledge and some effort to setup but once that's done, you probably won't have to mess with it ever again!
## Parts required:
  * Raspberry Pi
    
    While the script was designed on a Pi4, any Pi with preferably 40pin gpio interface and bluetooth should work.
  * Raspbian
    
    While the script is tested in Raspbian Buster, old versions may work.
  * 16x2 or 20x4 LCD display
    
    Any monochrome LCD with a **detached** i2c adapter is required. Make sure the i2c module is not attached to your LCD as your LCD requires 5v operation and the raspberry Pi can only accept 3.3v input, so you will probably kill something.
  * 3 push buttons
     
    Any normally open momentary buttons will work, it is recommended that you get two matching colored ones for the Left and Right buttons and one different for the Select button.
      Left -> GPIO pin 23
      Select -> GPIO pin 24
      Right -> GPIO pin 25
      
  * Python v3
  
  * Internet access
  
    Only required for downloading the script and the required packages and ssh-ing in case a monitor is not used.
    
  * A USB Flash drive formatted as FAT32 of any reasonable size for initial setup.
    
    Used by the guide linked below for the HackMii installer.
    
  ## Assembly:
   To assemble the circuit follow either the Fritzing sketch or the png schematic image. Please note that wire colours **do not** matter.
  ## Setup:
   1. Download the repository to a folder from the terminal by using `git clone https://github.com/Devnol/Bluebomb-automator`. 
   1. Navigate to the folder where the executables are by typing `cd Bluebomb-automator`. 
   1. Run the setup script to install all the required packages by running `./setup.sh`.
   1. Edit the script to correspond to your configuration of screen size and i2c address (notes are in the script itself)
   1. Run the script (This and navigating to the correct directory are the only steps required every time you restart): `python3 Bluebomb-automator.py`
   #### To enable the i2c interface of your raspberry Pi follow [this guide](https://www.raspberrypi-spy.co.uk/2014/11/enabling-the-i2c-interface-on-the-raspberry-pi/)
   #### Warning! If you run the script on an ssh terminal such as PuTTY make sure to use `screen -S bluebomb` before running the above commands to create a virtual shell that won't close when you close the ssh connection and `screen -r bluebomb` to reconnect to the shell running the script, otherwise, terminating the ssh connection will stop the script.
  ## Usage:
  1. Follow Section II of [this guide](https://wii.guide/bluebomb) up to and including step 5.
  #### For the first time running the script, have the terminal connected so that you see if something goes wrong. After you have set up everything it should work every time. Generally, if `Bluebomb executed` appears without pressing the sync button or very shortly after (less than 10 seconds) there is definitely a problem with your Bluetooth adapter.
  1. Use the two side buttons to select the Console type Wii (RVL-001/RVL-101) or Wii mini (RVL-201) and the Select button to choose between them.
  1. Choose the Region or SysMenu version of the console using the two side buttons. That version can be found in the top-right corner of the settings menu of your Wii. If you have a Wii mini, 4.3U denotes an NTSC version and 4.3E denotes a PAL version. Then, press the Select button to choose.
  1. Make sure the selection is correct, if it isn't hold the Select button until the application restarts and shows the splash text `Bluebomb helper vX.X`. Then start again.
  1. Once you have selected the correct option, turn on the Wii console making sure **No controllers are connected** and repeatedly tap the sync button until the LCD screen displays `Bluebomb executed` (if nothing happens within a couple minutes login to the shell of your raspberry pi and check the error). Then release the sync button and choose what to do from [this guide](https://wii.guide/bluebomb) after step 10 (Either install The Homebrew Channel and BootMii for Wii consoles or just The Homebrew Channel for Wii mini consoles.
  1. Since this is designed for batch modding, the program will simply restart. To stop the program, connect back to the Pi via ssh and stop the program by pressing `Ctrl+C`
 ## Credits:
   * TeamTwiizers: HackMii installer developers
   * FullMetal5: Bluebomb exploit developer
   * TwoSecsLater/urmum-69: Bluebomb helper script authors
   * Devnol: Python script author
   * Terry A. Davis: Motivation
 ### For any questions, problems or requests, [Join the Wii mini hacking server](https://discord.gg/KGBqNRb) (recommended) or create an issue on github.
 ## To Do List:
 - [ ] Add option to quit script without having to enter the shell
 - [ ] Add option in setup.sh to make the program run on boot/remove it from boot if installed
 - [ ] Make a showcase video
