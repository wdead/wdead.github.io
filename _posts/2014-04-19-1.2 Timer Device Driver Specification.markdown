# 1.2 Timmer Device Driver Specification #

## 1.2.1 Configuring the Timer ##

1. Timer I/O port: defined in 410kern/lib/inc/timer_defines.h.
2. Timer internal rate: 1193182 Hz, defined in 410kern/lib/inc/timer_defines.h.
3. Requirement: configure the timer to generate interrupts every 10 milliseconds.

**Timer initialization**

1. Send TIMER_SQUARE_WAVE(defined in 410kern/lib/inc/timer_defines.h) to TIMER_MODE_IO_PORT.
2. Send number of timer cycles to TIMER_PERIOD_IO_PORT.
3. Timer IDT index: TIMER_IDT_ENTRY.

**Timer handler**

1. Should save and restore general purpose registers.
2. Tell PIC the most recent interrupt delivered by sending INT_CTL_DONE to PIC's I/O port INT_CTL_REG(defined in 410kern/lib/inc/interrupts.h).

**Timer Device Driver Interface**

void tick(unsigned int numTicks), declared in **inc/410_reqs.h**.
