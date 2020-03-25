
![PrusaSlicer logo](/resources/icons/PrusaSlicer.png?raw=true)

# PrusaSlicer 2.3.0 DRIBBLING V.B01

This is a Fork of the PrusaSlicer 2.3.0
You may want to check the [PrusaSlicer project page](https://www.prusa3d.com/prusaslicer/).
For information on PrusaSlicer check the [PrusaSlicer project page](https://www.prusa3d.com/prusaslicer/).
Prebuilt Windows, OSX and Linux binaries are available through the [git releases page](https://github.com/prusa3d/PrusaSlicer/releases) or from the [Prusa3D downloads page](https://www.prusa3d.com/drivers/).

PrusaSlicer takes 3D models (STL, OBJ, AMF) and converts them into G-code
instructions for FFF printers or PNG layers for mSLA 3D printers. It's
compatible with any modern printer based on the RepRap toolchain, including all
those based on the Marlin, Prusa, Sprinter and Repetier firmware. It also works
with Mach3, LinuxCNC and Machinekit controllers.

PrusaSlicer is based on [Slic3r](https://github.com/Slic3r/Slic3r) by Alessandro Ranellucci and the RepRap community.

See the [project homepage](https://www.prusa3d.com/slic3r-prusa-edition/) and
the [documentation directory](doc/) for more information.

## What are the PrusaSlicer's DRIBBLING features compared to the original PrusaSlicer?

PrusaSlicer DRIBBLING version **is capable to produce better filament tips during MMU2 filament change with wipe tower, and to handle transitions from materials with different melting temperatures in multicolor mode (e.g. PLA to PETG, PLA to ABS, etc.)**
I had developed it especially for PLA filaments, in order to use bad quality / low cost filaments spools with MMU2.

### Where are those features ?

On the `Print settings` tab, selecting Multiple Extruders on the left, you can find a new checkbox in Advanced group:

- **DRIBBLING MODE** (on/off) -> if you do not enable dribbling mode, it works exactly as the standard PrusaSlicer.
If Dribbling mode is enabled, during the MMU2S filament change, just before extracting the filament, it plays with the filament doing a sort of dribbling and each hit of the filament in the melting area shapes the head almost squared, limiting the strings and strange big balls shapes to the minimum.

On the `Filament settings` tab, there are 3 new fields in the Temperature group:

- **MANUFACTURER MIN TEMP° and MAX TEMP°** ->  Those are the manufacturer printing specification **temperature** (in C°) of the filament, normally printed on the roll.
Normally under the MIN TEMP the filament does not melt, and over the MAX TEMP the filament degrades or burn.

- **DRIBBLING TIP SHAPE** temperature -> This is the ideal **temperature** (in C°) at which the tip shaping comes better. It is a matter of experimentation, and each filament could be different.

On the `Filament settings` tab, selecting Advanced on the left, you can find a new parameter in Toolchange Parameters with single extruder MM printers group:

- **NUMBER OF DRIBBLING MOVES** -> This number represent how many times the filament is Dribbled up and down hitting the melted area to perform the perfect tip shape. A reasonable number is between 1 and 4. 

On the `Printer settings` tab, selecting Single Extruder MM setup on the left, you can find a new parameter:

- **MELTING DISTANCE** (do not change) -> It represents how many mm the filament is dropped down from the rest position to just hit the melted area. This should allow to just hit the melted surface and not going deep into it.


*See a close-up picture of some filament heads  I got during a MMU2 multicolour print.*
![heads](/heads.jpg?raw=true)
### What language is it written in?

All user facing code is written in C++, and some legacy code as well as unit
tests are written in Perl. Perl is not required for either development or use
of PrusaSlicer.

The slicing core is the `libslic3r` library, which can be built and used in a standalone way.
The command line interface is a thin wrapper over `libslic3r`.

### What are PrusaSlicer's main features?

Key features are:

* **multi-platform** (Linux/Mac/Win) and packaged as standalone-app with no dependencies required
* complete **command-line interface** to use it with no GUI
* multi-material **(multiple extruders)** object printing
* multiple G-code flavors supported (RepRap, Makerbot, Mach3, Machinekit etc.)
* ability to plate **multiple objects having distinct print settings**
* **multithread** processing
* **STL auto-repair** (tolerance for broken models)
* wide automated unit testing

Other major features are:

* combine infill every 'n' perimeters layer to speed up printing
* **3D preview** (including multi-material files)
* **multiple layer heights** in a single print
* **spiral vase** mode for bumpless vases
* fine-grained configuration of speed, acceleration, extrusion width
* several infill patterns including honeycomb, spirals, Hilbert curves
* support material, raft, brim, skirt
* **standby temperature** and automatic wiping for multi-extruder printing
* [customizable **G-code macros**](https://github.com/prusa3d/PrusaSlicer/wiki/Slic3r-Prusa-Edition-Macro-Language) and output filename with variable placeholders
* support for **post-processing scripts**
* **cooling logic** controlling fan speed and dynamic print speed

### Development

If you want to compile the source yourself, follow the instructions on one of
these documentation pages:
* [Linux](doc/How%20to%20build%20-%20Linux%20et%20al.md)
* [macOS](doc/How%20to%20build%20-%20Mac%20OS.md)
* [Windows](doc/How%20to%20build%20-%20Windows.md)

### Can I help?

Sure! You can do the following to find things that are available to help with:
* Add an [issue](https://github.com/prusa3d/PrusaSlicer/issues) to the github tracker if it isn't already present.
* Look at [issues labeled "volunteer needed"](https://github.com/prusa3d/PrusaSlicer/issues?utf8=%E2%9C%93&q=is%3Aopen+is%3Aissue+label%3A%22volunteer+needed%22)

### What's PrusaSlicer license?

PrusaSlicer is licensed under the _GNU Affero General Public License, version 3_.
The PrusaSlicer is originally based on Slic3r by Alessandro Ranellucci.

### How can I use PrusaSlicer from the command line?

Please refer to the [Command Line Interface](https://github.com/prusa3d/PrusaSlicer/wiki/Command-Line-Interface) wiki page.
