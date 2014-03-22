PiRSClock-Full
==============

PiRSClock-Full is a Raspberry Pi Radio Studio Clock written in python using pygame with studio indicators for microphones, telephones etc... on widescreen (16:9) monitors, displays and TVs.

This was designed specifically for the Raspberry Pi. This version includes configurable indicators for microphones, telephones etc... for use in a radio studio.

## Development Status
PiRSClock-Full is currently stable and ready for use.


## Hardware Requirements

Pins 11, 12, 13 and 15 (top indicator to bottom) on main GPIO header light up the corresponding indicators when connected to pin 6 (Ground). 

More info on the header can be found here: [http://elinux.org/RPi_Low-level_peripherals](http://elinux.org/RPi_Low-level_peripherals)

**EXERCISE CAUTION WHEN HANDLING ELECTRICITY**

# Installation for Raspberry Pi
It's recommended to use Raspberry Pi OS for this project and a 4GB or more SD Card.
For reliability I recommend to only use this Pi for the clock.

> Note: The Pi will have the most accuracy in time keeping when it has a constant connection to the internet.

## 1. Download the Raspberry Pi Imager for your OS and install the Raspberry Pi OS directly on your SD-Card.
https://www.raspberrypi.org/downloads/
After installing on your SD-Card you can directly connect the Raspberry Pi to power and the System will start up.

## 2. Setup up your Localization, Time-Zone and Network
It's recommended to use the official Raspberry Pi OS config

    sudo raspi-config

## 3. Updates
Once you have rebooted and logged in lets make sure everything is up to date:

    sudo apt-get update
    
Then

    sudo apt-get upgrade
    
Then install the pip for python version 3 from

    sudo apt install python3-pip

After that, we have to install build-essential for python-dev

    sudo apt-get install build-essential python-dev

Now we need to get setuptools:

    sudo apt-get install python-setuptools
    
And finally we install PiRSClock-Full:

    sudo python /usr/lib/python2.7/dist-packages/easy_install.py PiRSClock-Full
    
and there we have it!

# Running it

All we have to do is:

    sudo pirsclockfull
    
To quit just hold down keys Q and T at the same time.

## Custom configuration
Firstly you type:

    sudo nano /usr/local/lib/python2.7/dist-packages/PiRSClock_Full-2.0-py2.7.egg/EGG-INFO/scripts/pirsclockfull

To set colours of the indicators, change the numerical values in ind1colour - ind4colour.

The values are standard RGB

The First value is RED, the second is GREEN and the third is BLUE. The max value is 255 and the min is 0

Example:

    ind1colour = (255, 0, 0)
    
would make the first indicator red in this example.

To change the text in the indicators, change the word in the "quotes" in ind1txt - ind4txt

Example:

    ind1txt = indfont.render("HELLO",True,bgcolour)

This would change the text to HELLO on the first indicator in this example.

Once you are done press Ctrl and O together

Then Enter

Ctrl and X together

# Making it startup automatically when you plug in the Pi

Firstly:

    sudo crontab -e
    
And add this to the bottom of the file:

    @reboot /usr/local/bin/pirsclockfull &
    
Press Ctrl and O keys together to save.

Then press Enter.

Then Ctrl and X to exit

    sudo reboot
    
To test it.
    
It should now automatically display after you reboot and every time you turn it on. Remember hold Q and T to get back to the command line if needed.
