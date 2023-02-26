## Setup
Save the necropowers.tin file to the .tt/3k/guilds/ folder.

Add the following line to necromancer.tin to trigger the study:
```
#alias {studyall} {#class {necropowers} {read} {.tt/3k/guilds/necropowers.tin}; power}
```
This loads the code on demand and triggers the studying from the power command output.

## Usage
Simply type studyall while in your guild library room. If you have the envision VAF you can easily modify this module to suit.

## In Steppers
If using a guild run inix stepper, add studyall into the botpath and then add the following action in the stepper file to enable it to continue after the study completes:
```
#action {^The power, LASTPOWER, does not exist} {..}
```
This is necessary as the script waits for the output from the power command to parse your currently memorised powers.
