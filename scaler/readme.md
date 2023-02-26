## Notes
**_Make sure you backup your bot_load.tin and start.tin files before making any changes._**

This module will only set scalers when stepping into the dungeon; it will not trigger if you manually walk in.

When making changes note that the last line in any {action} or {alias} should not have a trailing ;, e.g.
```
#alias {test} {
line1;
line2;
line3
}
```

## Setup
Place the charname_scalers.tin file into the .tt/3k/char/ folder and rename it to match your character, e.g. inix_scalers.tin. You do not need to manually edit the contents of this file, however you may do so if you wish.

Insert the following line to start.tin's load3k alias. Remember to add or remove ; where required.
```
#read .tt/3k/bots/bot_scale.tin;
```

Modify the '-' alias in bot_load.tin and insert the following line. Again, remember to add or remove ; where required.
```
#if {$scalers_enabled && $botscalers[%1]} { scaler $botscalers[%1] }
```
It should now look like this:
```
#alias {- %1} {
	#var no_home 0;
	#var no_loop 0;
	#var hardmode 0;
	#var vacuum 1;
	#if {"%1" == "miner"} {
		#read .tt/3k/craft/miner.tin
	} {
		#var bots[stepper] %1;
		#read .tt/3k/bots/%1.tin;
		#read .tt/3k/bots/bot_main.tin;
		#if {$scalers_enabled && $botscalers[%1]} { scaler $botscalers[%1] }
	}
}
```

## Usage
- 'scalers' to view your configured scalers
- 'scaleset <steppername> <level>' to set the scaler level for each stepper
- 'scalerem <steppername>' to remove the scaler level for the specified stepper
- 'scaleall <level>' to set all your scaler levels for any stepper which has previously been configured (it won't automatically add stepper names)
- 'scaleoff' to turn off the automatic scaling when starting a stepper
- 'scaleon' to turn on the automatic scaling when starting a stepper


Enjoy!
