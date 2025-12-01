---
{"publish":true,"title":"Building a KMK Split Keyboard with RP2040 Dactyl Minidox (36-Key).","created":"2025-11-29","modified":"2025-11-29","tags":["keyboard","KMK","python","split-keyboard"],"cssclasses":"","socialImage":"https://img.ellie.wtf/i/1a4023009b55738bd5c8a9dbad4b855d7168308ff7782668a5df928e3ea7d0bf.jpg"}
---

This guide provides step-by-step instructions for hand-wiring a split-keyboard. A 36-key Dactyl Minidox keyboard using Raspberry Pi Picos(RP2040 ) and KMK Firmware.
This build uses a "Visual Flow" wiring technique, The right half of keyboard is wired as the left half flipped around. See the visual wiring matrix under. This allows the firmware to remain simple and identical on both sides.
 
## Prerequisites

### Materials

|                                      | Product                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Variant                             | Quantity        |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------- | --------------- |
| ![[Keyboard related/assets/Bill_of_Materials 9.jpg]]  | [3D Printed Case](https://ryanis.cool/dactyl/#manuform:CiQIBRAEGgp0aHJlZS1taW5pIgR6ZXJvKgJteDIGbm9ybWllOAASEAiMFRCEBxjCAyADKMYKMAAaCggAEgRub25lGAAiF1UAABBBGAAgAF0AAGBAZQAAAEBAAEgAMvkBlQMAACBAnQMAAIA/gAMBiAMBDQAAAAAVAAAAAB0zMzNAJQAA0MAtAACQwTUAAMBAPQAAAABFAAAAAE0AAMBAVQAAQMBdAADgQGUzM2HCbTMzLcJ1AAC8wXjnAoABzRiIAcgklQEzMxfCnQEzM13CpQFmZsrBqAGfC7ABmRe4AfwlxQEAAFDCzQEAANDB1QEAAEDB2AGcBOAB8xfoAZAc9QEAAOjB/QEAACTChQIAAFDBiAKbBJAC8xeYAuAhpQIAAAzCrQIAAHDBtQIAAADAuAKEB8AClRDIAoQH1QIAAEDB3QIAAIDB5QIAAEBA6AKEB/AClRD4AoQH) | Dactyl Minidox                      | 1 Left, 1 Right |
| ![[Keyboard related/assets/Bill_of_Materials 4.jpg]]  | Raspberry Pi Pico Board RP2040                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | TYPE-C/MICRO with pins              | 2 pcs           |
| ![[Keyboard related/assets/Bill_of_Materials 5.jpg]]  | Switches                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Type MX. Brown, blue or your choice | 40 pcs          |
| ![[Keyboard related/assets/Bill_of_Materials.jpg]]    | Keycaps                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Type MX                             | 2 pcs           |
| ![[Keyboard related/assets/Bill_of_Materials 3.jpg]]  | USB M-F Extension Cable                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | 5 cm,  male TYPE-C/ MICRO           | 2 pcs           |
| ![[Keyboard related/assets/Bill_of_Materials 10.jpg]] | Audio Jack Socket                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | PJ392A 3.5MM                        | 2 pcs           |
| ![[Keyboard related/assets/Bill_of_Materials 8.jpg]]  | 4 Pole TRRS Male to Male                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 3.5MM                               | 1 pcs           |
| ![[Keyboard related/assets/Bill_of_Materials 1.jpg]]  | 1N4148 Switching Diodes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                     | 100 pcs         |
| ![[Keyboard related/assets/Bill_of_Materials 2.jpg]]  | Dupont Jumper Wires                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 40 cm, female to female             | 20 wires        |
| ![[Keyboard related/assets/Bill_of_Materials 7.jpg]]  | High Temperature Heat Tape                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | 15 mm                               | 1 roll          |

### Tools
*   Soldering iron and solder
*   Wire strippers/cutters
*   Tweezers
*   Multimeter (optional, for debugging)
### Testing and preparing your Pi Picos(controllers)
Before you begin, I recommend to get your `Pi Picos` ready to rock.
Follow the instruction on the [KMK get started page](https://github.com/KMKfw/kmk_firmware/blob/main/docs/en/Getting_Started.md) to make sure you controllers are tested and up and running. Do the same procedure on both controllers before you start the assembly 

## Hardware Assembly

### 1. Wiring the Matrix
You will wire a **5-column x 4-row** matrix on each side.
<img src="assets/1._Wiring_the_Matrix.svg" style="max-width:100%;height:auto;display:block;margin:0 auto;">

**The Golden Rule of this Build:**
Wire the right half as the left half flipped around.  
#### Wiring Steps
1.  **Rows:** Solder the **diodes** to the **right** pin of every switch. Connect the other end of the diodes horizontally. I hope the picture under clarify more than this simple words. 
> [!Warning] Diode Direction
> The black band (cathode) must point **away** from the switch and **towards** the controller row wire.

Here the rows consist of diodes soldered together(Don't do as mee. It is easier to solder the "diode" rows before the columns)
![[Keyboard related/assets/Wiring_Steps 1.jpg]]

2.  **Columns:** Solder wires connecting the **left** pin of every switch vertically(Red, orange, yellow, green and blue colored wires on picture)
   ![[Keyboard related/assets/Wiring_Steps 4.jpg|300]]
3.  The rules for soldering rows and columns to switches, are the same for both sides of keyboard(The pictures shows the left side of the keyboard) 
	1. **Rows**: solder always on **left** pin of switch 
	2. **Columns**: solder always on **right** pin of switch
### 2. Connecting the Controller
Look at the picture above and under, the columns and rows are prepared with female `DuPont` wires, that makes it easy to connect to to a controller with pins. That makes it easy to reconnect rows/cols to controller if you do some mistakes. It also makes it easy to switch controller later on for an upgrade.
![[Keyboard related/assets/2._Connecting_the_Controller 1.jpg|600]]

Connect the matrix rows and columns to the Raspberry Pi Pico using the following pinout.

> [!note]
> This pinout applies to **BOTH** the Left and Right controller.

| Function  | Visual Position | Pico Pin |
| --------- | --------------- | -------- |
| **Col 1** | Pinky           | **GP2**  |
| **Col 2** | Ring            | **GP3**  |
| **Col 3** | Fuck you        | **GP4**  |
| **Col 4** | Pointer         | **GP5**  |
| **Col 5** | Inner Column    | **GP28** |
| **Row 1** | Top Row         | **GP6**  |
| **Row 2** | Home Row        | **GP7**  |
| **Row 3** | Bottom Row      | **GP8**  |
| **Row 4** | Thumb Cluster   | **GP9**  |

### 3. Split Communication (TRRS)

Connect the TRRS breakout boards to establish communication between the halves. We use a single-wire data connection (PIO).
> [!note]
> This pinout applies to **BOTH** the Left and Right TRRS connector/controller.

*   **Tip (T):** Connect to **VBUS** (any VBUS pin).
*   **Ring 1 (R1):** Connect to **GP1** (Pin 2).
*   **Sleeve (S):** Connect to **GND** (any GND pin).
If these terms on the TRRS connectors does not say nothing to you, just connect them on TRRS connectors that are the same on both sides of keyboard.

> [!danger] Electrical Hazard
> **NEVER** plug or unplug the TRRS cable while the USB is connected to the computer. This can short the power pin to the data pin and permanently destroy your Pico. Always unplug USB first.

### 4. Identity Jumper (Right Side Only)

To allow the code to automatically detect which side is which, you must add a physical "jumper" wire to the **Right Controller** only.
1.  **Right Pico:** Connect a female to female DuPont cable connecting **GP21** directly to a  **GND** pin of choice.
2.  **Left Pico:** Nothing to do here.
In the [documentation for KMK split keyboards](https://github.com/KMKfw/kmk_firmware/blob/main/docs/en/split_keyboards.md), there is described that you have to rename the drives for Circuit python, for both sides. That is not necessary with this build.   
## Firmware Configuration

### 1. Installing Circuit Python and KMK

1. I assume that you have done this already.
   Follow the instruction on the [KMK get started page](https://github.com/KMKfw/kmk_firmware/blob/main/docs/en/Getting_Started.md) to make sure you `Pi Picos` are tested and up and running. Do the same procedure on both `Pi Picos`
### 2. The Code (`code.py`)

Copy the code below into the file named `code.py`, overriding the test code you made in the previous step. Do it on **BOTH** drives, Left and right.
When using and testing the full keyboard. The USB cable could always be connected to the left keyboard half.

```python
import board
import digitalio

from kmk.kmk_keyboard import KMKKeyboard
from kmk.keys import KC
from kmk.scanners import DiodeOrientation
from kmk.modules.split import Split, SplitType, SplitSide
from kmk.modules.layers import Layers

keyboard = KMKKeyboard()
keyboard.modules.append(Layers())

# --- 1. JUMPER DETECTION ---
# Checks GP21 to decide if this is the Left or Right keyboard.
# Right Side: GP21 connected to GND.
# Left Side: GP21 is empty.
jumper = digitalio.DigitalInOut(board.GP21)
jumper.direction = digitalio.Direction.INPUT
jumper.pull = digitalio.Pull.UP

is_right = False
if jumper.value == False:
    is_right = True

# --- 2. SPLIT CONFIGURATION ---
split = Split(
    split_type=SplitType.UART,
    data_pin=board.GP1,
    use_pio=True,
    uart_flip=True
)

if is_right:
    split.split_side = SplitSide.RIGHT
else:
    split.split_side = SplitSide.LEFT

keyboard.modules.append(split)

# --- 3. PINS & MATRIX ---
# we use the SAME pin order for both sides.

col_pins = (board.GP2, board.GP3, board.GP4, board.GP5, board.GP28)

keyboard.col_pins = col_pins
keyboard.row_pins = (board.GP6, board.GP7, board.GP8, board.GP9)
keyboard.diode_orientation = DiodeOrientation.COL2ROW

# --- 4. KEYMAP ---
# Layout: 3x5 Grid + 3 Thumbs
keyboard.keymap = [
    [
        # Left Hand (Cols 0-4)                     # Right Hand (Cols 0-4)
        KC.Q,  KC.W,  KC.E,    KC.R,    KC.T,      KC.Y,   KC.U,    KC.I,    KC.O,   KC.P,    # Row 0
        KC.A,  KC.S,  KC.D,    KC.F,    KC.G,      KC.H,   KC.J,    KC.K,    KC.L,   KC.SCLN, # Row 1
        KC.Z,  KC.X,  KC.C,    KC.V,    KC.B,      KC.N,   KC.M,    KC.COMM, KC.DOT, KC.SLSH, # Row 2
        
        # Thumbs (Row 3)
        # Note: Pinky & Ring cols are empty (NO) on Dactyl Minidox thumbs
        KC.NO, KC.NO, KC.LCTL, KC.LSFT, KC.SPC,    KC.ENT, KC.BSPC, KC.LALT, KC.NO,  KC.NO,
    ]
]

if __name__ == '__main__':
    keyboard.go()