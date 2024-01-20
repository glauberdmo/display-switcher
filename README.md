
## Description
I bring here two solutions to change the PC connected in a single display without needing a full KVM (with support a video inputs),  just a usb hub switcher is required.

 ## How it works?
 
This turns off the current input display for a few seconds, 
giving time to the display detects the another system.
In case of use through a button of switcher a service will
be created and will stay checking if the keyboard was
detected and disconnected, using it as trigger to run the display-manager.


 ## Requirements
- 2 systems running linux
- A monitor with 2 video inputs, each one already plugged in each system
- An usb hub switcher
 Example:
    - ![image.png](./assets/display-switcher.png)
- Any switch does works

 ## Switching through hotkeys
- Save the file `dspswitcher`  and use your key binding to run:

 ```
 usr/bin/bash <path for dspswitcher>
 ```

## Switching through button

 ### Steps
- Save the file `display-switcher` in any place
- Save the file `displayswitcher.service`  in `/etc/systemd/system/`
- edit this file adding the path for display-switcher shell script
- Reload the systemd daemon to read the new service unit file:
	    
 ```
  sudo systemctl daemon-reload
 ```
- Enable the service to start at boot:
 
 ```
 sudo systemctl enable displayswitcher.service
 ```
- Start the service:
    
 ```
 sudo systemctl start displayswitcher.service
 ```
		    
Now the display-switcher e will run automatically every time you start your PC.  

 ## Known issues
 ### xset not finding displays
- This happens in some cases running using service, make a pull request with you know a solution
