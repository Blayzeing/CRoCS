# Cobat Robotics Clock System (CRoCS)
CRoCs is a highly-configurable arduino-based clock and timer system for combat robotics events.
It's state-based with program-configurable lighting & count-down systems, designed for easy customisation and optional run-time configurable match lengths.

By default, the state control flow is as follows:

```mermaid
graph TD;
  PRE_FIGHT --start button pressed--> COUNTDOWN
  COUNTDOWN --3 seconds elapse--> FIGHTING
  COUNTDOWN --pause button pressed --> PRE_FIGHT
  COUNTDOWN --reset button pressed --> PRE_FIGHT
  FIGHTING --round time elapses--> CEASE
  FIGHTING --pause button pressed--> CEASE
  FIGHTING --reset button pressed--> PRE_FIGHT
  CEASE --round is resumed--> FIGHTING
  CEASE --reset button pressed--> PRE_FIGHT
```

While in the `FIGHTING` state, secondary timers can be configured to be activated for pinning, pits and other special events.
Each timer has the following state control flow:

```mermaid
graph TD;
  INACTIVE --activated-->COUNT_DOWN
  COUNT_DOWN --set time elapses-->INACTIVE
  COUNT_DOWN --cancelled-->INACTIVE
```
