# ARM7-PLL
PLL (Phase Locked Loop) in ARM7 LPC2138 / LPC2148

1. Overview
PLL (Phase Locked Loop) is used to increase the internal clock frequency from the external crystal oscillator to a higher CPU clock frequency.
LPC2138 / LPC2148 have an on-chip PLL that can multiply the oscillator frequency to achieve faster operation for ARM7 core.

2. Why PLL is Used
External crystal frequency is often low (e.g., 12 MHz).
ARM7 core can run at a higher frequency (e.g., 60 MHz, 75 MHz).
PLL multiplies the crystal frequency without using high-frequency crystals.

Example:
Crystal frequency (Fosc) = 12 MHz
PLL multiplier = 5
CPU clock (CCLK) = 12 × 5 = 60 MHz

3. Registers for PLL (LPC2148)
Register	Purpose
PLLCON	PLL Control (enable/disable PLL)
PLLCFG	PLL Configuration (multiplier M, divider N)
PLLSTAT	PLL Status (locked, connected)
CCLKCFG	CPU Clock Divider (to generate CCLK from PLL output)

4. Key Points
PLLCFG:
Bits 0–4: Multiplier M (1–32)
Bits 5–6: Pre-divider N (1–4)
PLLCON:
Bit 0: Enable PLL
Bit 1: Connect PLL to CPU
PLLSTAT:
Bit 26: PLOCK → 1 when PLL locks to target frequency

CCLKCFG:
Divider to generate CCLK = PLL output / divider
