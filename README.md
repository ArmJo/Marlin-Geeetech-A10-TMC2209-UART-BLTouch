# Marlin 3D Printer Firmware

My configuration of Marlin 2.0.x for the Geeetech A10 with support for TMC2209 and BLTouch.  
Check out my other [repository](https://github.com/Jonas2903/Geeetech-A10-TMC2209-UART) about it.

My Cura Start-G-Code:

```
M140 S{material_bed_temperature_layer_0} ; Set Heat Bed temperature
M190 S{material_bed_temperature_layer_0} ; Wait for Heat Bed temperature
M104 S160; start warming extruder to 160
G28 ; Home all axes
G29 ; Auto bed-level (BL-Touch)
G92 E0 ; Reset Extruder
M104 S{material_print_temperature_layer_0} ; Set Extruder temperature
G1 X0.1 Y20 Z0.3 F5000.0 ; Move to start position
M109 S{material_print_temperature_layer_0} ; Wait for Extruder temperature
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
; End of custom start GCode
```

My Cura Stop-G-Code:

```
G91 ;Switch to relative positioning
G1 E-1 ;Retract filament to lower pressure
G0 X0 Y200 ;Move hotend to left and bed forward
M104 S0 ;Cooldown hotend
G90 ;Switch to absolute mode
G92 E0 ;Set extruder to zero
M140 S0 ;Cooldown bed
M84 ; Disable steppers
```
