# PC Assembly — Full Step by Step

Building the Cybersecurity Rig (Ryzen 7 5700X + RTX 3090 + Fractal Meshify C)

---

## Before You Start

```
[ ] Clear a large flat workspace (kitchen table works)
[ ] Phillips head screwdriver ready
[ ] Ground yourself before touching components
    → Touch a metal part of the case before handling CPU/RAM/GPU
    → Or wear an anti-static wrist strap ($5 on Amazon)
[ ] All parts unboxed and ready
[ ] Keep your motherboard manual nearby — it has diagrams for every connector
[ ] Keep all small screws from each box — they are different sizes, do not mix them
```

---

## Step 1 — Prepare the Motherboard (Outside the Case)

Lay the motherboard flat on top of the box it came in. The cardboard acts as insulation.

### Install CPU
```
[ ] Lift the lever on the AM4 socket on the motherboard
[ ] Find the gold triangle on the corner of the CPU
[ ] Line it up with the triangle marked on the socket
[ ] Drop the CPU in gently — it falls by gravity, do NOT push or force it
[ ] Lower the lever down to lock it in place
[ ] Never touch the gold pins on the bottom of the CPU
```

### Install RAM
```
[ ] Check MSI B550 Tomahawk manual for correct slots (use A2 and B2 for 2 sticks)
    — This is usually slots 2 and 4, not 1 and 2
[ ] Push the side clips on the slots open
[ ] Line up the notch on the RAM stick with the notch in the slot
[ ] Press down firmly on both ends at the same time
[ ] You should hear two clicks — one on each side
[ ] Clips snap back up automatically when seated correctly
```

### Install NVMe SSD
```
[ ] Find the M.2 slot on the motherboard (thin strip, usually below the CPU)
[ ] Remove the small screw at the end of the slot (comes with motherboard)
[ ] Insert the SSD at a 30-degree angle into the slot
[ ] Press it flat against the board
[ ] Screw in the small standoff screw to hold it down
```

---

## Step 2 — Install CPU Cooler (DeepCool AK400)

```
[ ] DeepCool AK400 comes with thermal paste pre-applied on the base
    → If pre-applied: use as-is. Do not add more paste.
    → If not pre-applied: place a pea-sized dot of paste in the center of the CPU

[ ] Attach the AM4 mounting bracket to the motherboard
    → Use the bracket labeled AM4 (for Ryzen 5700X)
    → Screws go through the motherboard from the back — use the backplate included

[ ] Lower the cooler onto the CPU, lining up the screw holes with the bracket

[ ] Tighten the screws in an X pattern (do not tighten one all the way before others)
    → Diagonal order: top-left, bottom-right, top-right, bottom-left
    → Snug is enough — do not overtighten

[ ] Plug the fan cable into the CPU_FAN header
    → Located near the top of the motherboard, labeled CPU_FAN
```

---

## Step 3 — Mount Motherboard in Case

```
[ ] Open the Fractal Meshify C left side panel (thumbscrews on back)

[ ] Install the I/O shield
    → The metal rectangle that came with the motherboard
    → Press it into the large rectangular hole at the back of the case
    → It only fits one way. The ports should face outward.
    → Press all edges until it snaps in fully

[ ] Install motherboard standoffs
    → Brass screws that thread into the case before the motherboard goes in
    → They hold the board up off the metal to prevent shorts
    → Check the case manual for ATX standoff positions
    → MSI B550 Tomahawk is ATX size

[ ] Lower the motherboard in
    → Back ports align with I/O shield holes
    → Motherboard holes line up with standoffs
    → Use the screws from the motherboard box to secure it
    → Tighten in a cross pattern, snug but not too tight
```

---

## Step 4 — Install PSU (Corsair RM850x)

```
[ ] The Fractal Meshify C has the PSU mount at the bottom of the case

[ ] Slide the PSU in with the fan facing DOWN
    → Fan pulls air in from the bottom of the case through the mesh
    → This is correct — do not face the fan upward

[ ] Screw in the 4 PSU screws from the back of the case

[ ] Route cables through the cable management holes in the case
    → Pass cables behind the motherboard tray when possible
    → Cleaner cable routing = better airflow = cooler temps
```

---

## Step 5 — Install GPU (RTX 3090)

```
[ ] Remove PCIe slot covers from the back of the case
    → RTX 3090 is a 3-slot card — remove 3 covers (they unscrew or pop out)

[ ] Insert GPU into the top PCIe x16 slot
    → The longest slot on the motherboard
    → Line up the gold contacts with the slot
    → Push down firmly until you hear a click
    → The retention clip at the end of the slot snaps when fully seated

[ ] Screw the GPU bracket into the case from the back (2 screws)

[ ] Connect GPU power cables (RTX 3090 needs 3x 8-pin PCIe)
    → Use the cables labeled VGA or PCIe from the Corsair RM850x
    → All 3 connectors plug into the side of the GPU
    → They only go in one way — do not force them
    → Make sure all 3 are fully clicked in
```

---

## Step 6 — Connect All Cables

```
[ ] 24-pin main power
    → Largest connector, goes into the large port on the right side of the motherboard
    → Should click in firmly

[ ] CPU 8-pin power
    → Top left corner of the motherboard, labeled CPU or ATX12V
    → Route the cable from the PSU through the top cable management hole

[ ] GPU 3x 8-pin power
    → Already done in Step 5

[ ] Front panel connectors (bottom right corner of motherboard)
    → Check motherboard manual for exact pin locations
    → PWR_SW    → Power button
    → RESET_SW  → Reset button
    → PWR_LED+  → Power LED positive
    → PWR_LED-  → Power LED negative
    → HDD_LED   → HDD activity light

[ ] USB headers
    → USB 3.0 (blue, larger connector) → USB3_1 or USB3_2 header on board
    → USB 2.0 (smaller) → USB2 header on board

[ ] Case fans
    → Connect to SYS_FAN1, SYS_FAN2 headers on motherboard

[ ] Front audio
    → Small connector from case → AAFP header (bottom left area of board)
```

---

## Step 7 — First Boot (Before Closing the Case)

Double-check before powering on:
```
[ ] All power cables are firmly seated (24-pin, CPU 8-pin, GPU 3x 8-pin)
[ ] RAM is clicked in completely on both sides
[ ] GPU is clicked in with the retention clip
[ ] CPU cooler fan is plugged in
```

Power on:
```
[ ] Plug monitor into the GPU (HDMI or DisplayPort on the GPU, not the motherboard)
[ ] Plug in keyboard and mouse (USB)
[ ] Plug power cable into PSU
[ ] Flip PSU power switch to ON (back of case, I = on, O = off)
[ ] Press the power button on the case
```

### Expected Results
```
GOOD:
→ Fans spin up
→ GPU fans spin
→ Monitor shows BIOS/UEFI screen or motherboard logo
→ RGB lights up (if any)

IF NOTHING HAPPENS:
→ Check 24-pin power cable is fully seated
→ Check CPU 8-pin cable is connected
→ Check PSU switch is ON (I position)
→ Check power button front panel connector is on correct pins

IF IT BEEPS ONCE:
→ RAM not seated — push harder on both sides until both clips click

IF SCREEN IS BLACK BUT FANS SPIN:
→ Monitor plugged into motherboard instead of GPU — switch to GPU ports
```

---

## Step 8 — BIOS Setup

Enter BIOS by pressing **Delete** key repeatedly at startup (MSI boards).

```
[ ] Enable XMP Profile for RAM
    → Go to: OC section → XMP → Enable → Profile 1
    → This activates 3200MHz. Without it, RAM runs at 2133MHz (slower).

[ ] Verify everything is detected
    → CPU: "AMD Ryzen 7 5700X" ✓
    → RAM: 32768 MB at 3200 MHz ✓
    → Storage: Your NVMe SSD name ✓
    → GPU: Listed in PCIe section ✓

[ ] Set boot priority for OS install
    → Boot → Boot Device Priority → Set USB drive as first

[ ] Save and exit
    → Press F10 → Yes
```

---

## Step 9 — Close the Case

```
[ ] Route any loose cables behind the motherboard tray
[ ] Use zip ties or velcro straps to bundle cables
[ ] Reinstall the side panel
[ ] Connect monitor, keyboard, mouse, ethernet, and power
```

Assembly is complete. Proceed to `docs/06-linux-setup.md`.
