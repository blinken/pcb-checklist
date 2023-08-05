# Layout review checklist

## General setup

* [ ] [Schematic review](schematic-checklist.md) complete and signed off, including pin swaps done during layout
* [ ] CAD design rules configured with fab's minimum tolerances, or better
* [ ] 2-3 standard via sizes chosen (signal, power) & well within fab tolerances
* [ ] 2-5 standard trace sizes chosen (small signal, small power, main power) & well within fab tolerances
* [ ] Align one standard trace size to 50ohm coplanar waveguide/stripline width (if used)
* [ ] Zone clearance set appropriately for coplanar waveguides
* [ ] Cage/shield footprints placed before layout starts

## Decoupling

* [ ] Decoupling caps as close to power pins as possible
* [ ] Low inductance mounting used for decoupling (prefer ViP if available, otherwise "[]8" shaped side vias

## DFM / yield enhancement

* [ ] Layout DRC 100% clean
* [ ] Controlled impedance, design stackup, thickness, plating and any other parameters recorded in text block on Fab layer
* [ ] Confirm impedance calculations include soldermask, or mask removed from RF traces
* [ ] Stackup verified with manufacturer and specified in fab notes
* [ ] If panelizing, add panel location indicators for identifying location-specific reflow issues
* [ ] Layer number markers on each layer copper to ensure correct assembly
* [ ] Fiducials present (on both sides of board) if targeting automated assembly
* [ ] Fiducial pattern asymmetric to detect rotated or flipped boards
* [ ] Soldermask/copper clearance on fiducials respected
* [ ] Panelization specified if required

## Footprints

* [ ] Confirm components are in stock in the selected package
* [ ] Confirm components (especially connectors and power regulators) are capable of desired current in the selected package
* [ ] Verify schematic symbol matches the selected package (confirm datasheet pins vs PCB copper wiring)
* [ ] Confirm pinout diagram is from top vs bottom of package
* [ ] 3D models obtained (if available); board reviewed in 3D to check for courtyard/assembly issues
* [ ] Soldermask apertures on all SMT lands and PTH pads
* [ ] Soldermask fingers between all IC pads

## Differential pairs
* [ ] Routed differentially
* [ ] Skew matched
* [ ] Correct clearance to non-coupled nets

## High-speed signals

* [ ] Sufficient clearance to potential aggressors
* [ ] Length matched if required
* [ ] Minimize crossing reference plane splits/slots or changing layers, use caps/stitching vias if unavoidable
* [ ] Confirm fab can do copper to edge of PCB for edge launch connectors
* [ ] Double-check pad width on connectors and add ground plane cutouts if needed to minimize impedance discontinuities
* [ ] Add stitching vias to ground plane in large top layer ground pads (SMA etc) to avoid resonances

## Power
* [ ] Power planes are not broken by closely-spaced fence vias
* [ ] Unbroken ground planes beneath all high-current traces
* [ ] Sufficient width for planes/traces for required current

## RF
* [ ] High-power outputs well separated from LNA inputs
* [ ] Large clearance around magnetic components (eg. circulators)
* [ ] LNA inputs clear of all other active components

## Sensitive analog
* [ ] All sensitive components under cages/shields
* [ ] Physically separated from high current SMPS or other noise sources
* [ ] Consider microphone effect on MLCCs if near strong sound sources

## Mechanical
* [ ] Confirm all connectors to other systems comply with the appropriate mechanical standard (connector orientation, key position, etc)
* [ ] LEDs, buttons, and other UI elements on outward-facing side of board
* [ ] Keep-outs around PCB perimeter, card guides, panelization mouse-bites, etc respected
* [ ] Stress-sensitive components (MLCC) sufficiently clear from V-score or mouse bite locations, and oriented to reduce
bending stress
* [ ] Clearance around large ICs for heatsinks/fans if required
* [ ] Clearance around pluggable connectors for mating cable/connector
* [ ] Clearance around mounting holes for screws
* [ ] Plane keepouts and clearance provided for shielded connectors, magnetics, etc
* [ ] Confirm PCB dimensions and mounting hole size/placement against enclosure or card rack design
* [ ] Verify mounting hole connection/isolation
* [ ] Components not physically overlapping/colliding
* [ ] Clearance provided around solder-in test points for probe tips

## Thermal

* [ ] Thermal reliefs used for plane connections (unless via is used for heatsinking)
* [ ] Solid connections used to planes if heatsinking
* [ ] Ensure thermal balance on SMT chip components to minimize risk of tombstoning

## Solder paste

* [ ] No uncapped vias in pads (except low-power QFNs where some voiding is acceptable)
* [ ] QFN paste prints segmented
* [ ] Small pads 100% size, larger pads reduced to avoid excessive solder volume
* [ ] No paste apertures on card edge connectors or test points

## Solder mask

* [ ] Adequate clearance around pads (typ. 50 um)
* [ ] Fingers between pads on small-pitch components

## Silkscreen

* [ ] Text size within fab limits & consistent across board
* [ ] Text not overlapping drills or component pads
* [ ] Text orientation consistent (within reason)
* [ ] Text removed entirely in, or moved outside of, high component/via density areas
* [ ] Unnecessary silkscreen removed for clarity
* [ ] Power connector polarity marked and verified
* [ ] LED colour marked (if hand assembly)
* [ ] LED/switch/connector purpose marked
* [ ] Spare GPIO headers marked with port name
* [ ] Design/assembly notes included where space permits (antenna dimensions/centre frequency, wiring notes, baud speed, assembly instructions/screw size)
* [ ] High voltage/heat/ESD safety warnings included (if appropriate)
* [ ] Link to project github included (open hardware designs)
* [ ] Traceability markings (revision, date, name, etc) provided and updated
* [ ] Silkscreen box provided for writing/sticking serial number
* [ ] Text mirrored properly on bottom layer
* [ ] Test points labeled if space permits

## Flex specific
* [ ] Components oriented to reduce bending forces
* [ ] Teardrops on all wire-to-pad connections

## CAM production
* [ ] KiCAD specific: rerun DRC and zone fills before exporting CAM files to ensure proper results
* [ ] Export gerber/drill files at the same time to ensure consistency
* [ ] Visually verify final CAM files to ensure no obvious misalignments
