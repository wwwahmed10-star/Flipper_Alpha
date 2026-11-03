# Flipper Alpha - KiCad Files

Files generated from the uploaded schematic and PCB images:
- `Flipper_Alpha.kicad_sch` — Complete schematic (KiCad 8)
- `Flipper_Alpha.kicad_pcb` — PCB layout ready for routing (KiCad 8)

The symbols and footprints are **embedded in the files themselves** — no external libraries are required.

## Pin Mapping

| Module | Signal | ESP32 (CYD) | Notes |
|---|---|---|---|
| PN532 (I2C) | SDA / SCL | GPIO21 / GPIO22 | 3.3V power |
| CC1101 (SPI) | SCK / MISO / MOSI | GPIO18 / GPIO19 / GPIO23 | Shared SPI |
| CC1101 | CSN / GDO0 / GDO2 | GPIO5 / GPIO2 / GPIO35 | |
| NRF24L01 (SPI) | SCK / MISO / MOSI | GPIO18 / GPIO19 / GPIO23 | Shared SPI |
| NRF24L01 | CE / CSN | GPIO26 / GPIO25 | |
| IR LED | Output | GPIO4 through a 220Ω resistor | LED to GND |
| TSOP (IR RX) | OUT | GPIO34 | |
| 433MHz RF | TX / RX | GPIO12 / GPIO13 | 5V power |
| GPS (UART) | TX / RX | GPIO16 / GPIO17 | UART2 |

## Important Assumptions (Review Before Manufacturing!)

1. Some connections in the original image are not completely clear. The most logical pin assignments were used (based on the conventional Flipper Zero layout).
2. The PCB is **unrouted**: the components are placed and the nets are defined. Open the board in KiCad and route the tracks manually or with FreeRouting.
3. Verify the exact pinout of your CYD-24325028 display version before fabrication.
4. J1–J4 (XH connectors) have been left unconnected. Assign them according to your firmware's button or expansion requirements.
5. The board dimensions are 125 × 85 mm, with four M3 mounting holes.

## KiCad Workflow

1. Open `Flipper_Alpha.kicad_sch` and run the ERC (Electrical Rules Checker).
2. Open `Flipper_Alpha.kicad_pcb`, press **B** to refill the copper zones, then route the nets.
