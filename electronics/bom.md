# OpenDIHM Electronics | Bill of Materials

- AC-DC Adaptor 5V
  - Input: 220V (EU)
  - Output: 5V
  - Output: min 2.5A
- CTRICALVER Laser Module Adjustable Focal Point
  - Output: 405nm Light
  - Input: 3V to 5V
  - Input: <130mA
  - https://www.amazon.de/-/en/dp/B0F5M1LW46
- 1k Resistor ($R_base$)
- $R_{limiting}$ Resistor - find the Calculation in following runbook.
- NPN BJT Transistor (2N2222)
- Raspberry Pi Zero 2W
- GPIO Headers (for RPi, you can also have RPi Zero 2WH)
- WAGO Connector (to split the 5V to Laser and Raspberry Pi)

## Runbook
### Calculation of $R_limiting$
If your laser comes in a housing (e.g., a brass cylinder) with an integrated driver board, it already limits its own current. If you are using a bare laser diode without an internal driver,
you must add a series current-limiting resistor. Without it, the transistor will allow too much current to pass, instantly burning out the diode.

The formula to use is:
$$R_{limiting} = \frac{V_{supply} - V_{laser} - V_{CE(Drop)}}{I_{target}}$$

* **$V_{Supply}$**: 5V (The main power supply/adapter).
* **$V_{Laser}$**: The operating forward voltage of the specific laser diode (e.g., 2.5V).
* **$V_{CE(Drop)}$**: The small voltage drop across the transistor when it is fully saturated/open (typically ~0.2V for a standard NPN like the 2N2222).
* **$I_{Target}$**: The maximum safe current the laser diode is rated to handle (e.g., 30mA, which is 0.03A).
