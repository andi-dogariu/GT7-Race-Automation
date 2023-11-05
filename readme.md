# GT7 Race Automation for Daytona

====================================

This version is specialized for money grind using Daytona custom race in version 1.40.

I only tested with engine-swapped abarth 500. Time / handle may vary if you use different cars.

To make it work, you need to install older version of PS Remote Play, as the latest version does not take PyAutoGUI (see https://forum.psnprofiles.com/topic/142048-is-jump-script-method-even-possible-these-days/?do=findComment&comment=2752418). Further, WSL may not work - I had to use windows' version of python with PyAutoGUI installed, and run powershell as Administrator.

Script should be run with your cursor on "start" in the screen for the custom race, along with "Settings", "Exit", etc. on the right. After this the grinding will be automated.

====================================

The `main.py` script allows you to automate racing circular tracks using PyAutoGUI and PS Remote Play. Depending on the car and track you race, you can make 400K/hr or more. NOTE: The track must have unidirectional turns, meaning every turn should be either left or right. I think the script should work on any platform.

## Instructions

All you need to do is open PS Remote Play and then navigate to the race start screen for the track you want to automate. This is the screen with `Start`, `Settings`, and `Exit` buttons. Make sure that the remote play window is in the middle of your primary monitor because the script clicks the center of the screen to get the winow's focus.

Next, open a terminal with administrator privileges (I had to use administrator privileges, but you might not have to). Navigate to the directory containing this script and run it:

```bash
py main.py
```

Voila! You are now racing in circles.

By default this will race around a circular track with left turns for 200 seconds before navigating through the menus to restart the race. You can change the behavior by passing some command line arguments.

- To change the side of the track you hug, you can pass the flag `--direction=DIRECTION`. By default you hug the `right` rail. You can also simply pass `-left` or `-l` or `-right` or `-r`.
- You can change the duration with `--duration=DURATION`, where `DURATION` is the number of seconds that the race takes. You can also simply pass a number, like `200`. To get a sense for how long the race takes, start the script with a long duration, say `1000` seconds, and see how long it takes to navigate the course and then restart the script using the new duration (you should add some padding to account for collisions, maybe +10 seconds to be safe).

The following command will automate a 120 second race where you hug the left hand rail of the course:

```bash
py main.py --direction=left --duration=120
```

Another command that does the same thing:

```bash
py main.py -left 120
```

### Controller settings
It is necessary to map acceleration as well as left and right steering to the d-pad.
### In-game settings
- enable traction control
- decrease opponents strength in the top-left menu 'options' (will not affect prize money)

## Notes

Right now the script simply navigates through the menus for standard races and runs a race based on timing, meaning if you spin out or something the timing will likely be off.

If you want to automate a different event, say a championship series, you can edit the script with new menu navigation commands. These are self explanatory in the script.

