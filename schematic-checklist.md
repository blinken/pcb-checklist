# Schematic review checklist

## General

* [ ] CAD ERC 100% clean. If some errors are invalid due to toolchain quirks, each exception must be inspected and signed
off as invalid.
* [ ] Verify pin numbers of all schematic symbols against datasheet or external interface specification document (if not yet board proven).
* [ ] Schematic symbol matches chosen component footprint
* [ ] Thermal pads are connected to correct power rail (may not always be ground)
* [ ] Debug interfaces are not power gated in sleep mode

## Passive components
* [ ] Power/voltage/tolerance ratings specified as required
* [ ] Ceramic capacitors appropriately de-rated for C/V curve
* [ ] Polarized components specified in schematic if using electrolytic caps etc
* [ ] Filters: component footprint is large enough for rated current, and appropriate for RF characteristics

## Power supply

### System power input

* [ ] Reverse voltage protection at system power inlet
* [ ] Fusing at system power inlet
* [ ] EMI common mode/low-pass filtering at power inlet (if needed)
* [ ] Check total input capacitance and add inrush limiter (if needed)
* [ ] Low pass filter included after main buck regulator (if needed)

### Regulators

* [ ] Under/overvoltage protection configured correctly if used
* [ ] Verify estimated power usage per rail against regulator rating
* [ ] Current-sense resistors on power rails after regulator output caps, not in switching loop
* [ ] Remote sense used on low voltage or high current rails
* [ ] Linear regulators and voltage reference ICs are stable with selected output cap ESR
* [ ] Confirm regulator strap pin configuration against datasheet
* [ ] Confirm power rail sequencing against device datasheets (if needed)

### Decoupling
* [ ] Decoupling present for all ICs
* [ ] Decoupling meets/exceeds vendor recommendations if specified
* [ ] Bulk decoupling present at buck/boost regulators (input and output)
* [ ] RF boards: standard 0402 decoupling cap selected for frequency of interest and used at every IC

### General
* [ ] All power inputs fed by correct voltage
* [ ] Analog rails filtered/isolated from digital circuitry as needed

## Signals

### Digital

* [ ] Signals are correct logic level for input pin
* [ ] Pullups on all open-drain outputs
* [ ] TX/RX wired correctly for UART, SPI, MGT, etc
* [ ] Enable pins: Active high/low polarity correct

### Analog/RF

* [ ] RC time constant for attenuators sane given ADC sampling frequency
* [ ] Verify frequency response of RF components across entire operating range. Don't assume a "1-100 MHz" amplifier has the
same gain across the whole range.
* [ ] Verify polarity of op-amp feedback
* [ ] Cages/shields selected for each schematic block

### Clocks

* [ ] All oscillators meet required jitter / frequency tolerance. Be extra cautious with MEMS oscillators as these tend to have higher jitter.
* [ ] Correct load caps provided for discrete crystals
* [ ] Crystals only used if IC has an integrated crystal driver

### Strap/init pins
* [ ] Pullup/pulldowns on all signals that need defined state at boot
* [ ] Strap pins connected to correct rail for desired state
* [ ] JTAG/ICSP connector provided for all programmable devices
* [ ] Config/boot flash provided for all FPGAs or MPUs without internal flash

### External interface protection

* [ ] Power outputs (USB etc) current limited
* [ ] ESD protection on data lines going off board

### Debugging / reworkability

* [ ] Use 0-ohm resistors/solder jumpers vs direct hard-wiring for strap pins when possible
* [ ] Provide multiple ground clips/points for scope probes
* [ ] Multimeter + U.FL test points on all power rails
* [ ] Dedicated ground in close proximity to test points
* [ ] Test points on interesting signals which may need probing for bringup/debug

## Thermal

* [ ] Power estimates for all large / high power ICs
* [ ] Thermal calculations for all large / high power ICs
* [ ] Specify heatsinks as needed

