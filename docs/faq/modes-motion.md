# Modes & Motion

## Does Duilio support closed-loop control?
Closed-loop control is supported for positioning modes. Speed mode uses open-loop control with a speed limiter.

## How does the speed limiter work?
It computes the average speed of both wheels to ensure stable and coordinated motion.

## Is the speed limiter mandatory?
No. If the RPM input is not connected, the limiter is inactive.

## Can I use closed-loop speed control?
No. Speed mode is open-loop with a limiter.
