# switchmap

A single-file browser app for mapping electrical receptacles, switches, lights and circuits onto a floorplan image.

## Features

- A built-in **sample house** (a fictional two-floor plan with about 80 devices already mapped) for trying the app out. It opens automatically on first run when there are no projects, and you can start a fresh copy from the projects page at any time.

- Upload a floorplan JPEG or PNG and draw a box around each floor to give it its own tab.
- Place receptacles (duplex, 20A, GFCI, AFCI/GFCI, USB, quad, weatherproof, 240V, floor box), switches (single-pole, 3-way, 4-way, dimmer, fan control, occupancy sensor, timer, smart main, smart companion, scene keypad, wireless remote), lights and fans, and other devices (smoke/CO alarms, panel, junction box, thermostat, data, doorbell, EV charger, hardwired appliances, hubs, sensors).
- Edit each device's room, label, status (existing / new / relocate / remove), circuit, switched half of a receptacle, GFCI protection chain, and smart details (role, protocol, brand, hub, scenes, neutral).
- **Link control** mode connects switches to the loads they control. Clicking a second switch shares the loads for 3-way and 4-way setups.
- **Circuit paint** mode is for mapping a panel breaker by breaker.
- **Test mode** dims the house so you can flip switches and see which lights glow, which fans spin and which outlets have power. 3-way and 4-way groups toggle from any location, and dimmers and fan speeds have sliders. Timers and occupancy sensors switch themselves off after a few seconds. Turning breakers off shows what loses power. Switch groups that aren't set up correctly are tested as series wiring and flagged. Nothing in test mode changes the project.
- **Checks** flags switch configurations that don't match the number of control locations, switched receptacles with no switch, and wet-location receptacles with no GFCI. These are planning hints, not code compliance.
- Colour the plan by type, status, circuit or smart; adjust symbol size; undo and redo.
- Outputs: annotated plan PNG (one floor or all floors), device schedule CSV, breaker directory (CSV and a printable panel card), smart home list CSV, a full printable HTML report, and three JSON exports:
  - **Project file with floorplan**: a complete backup you can import again on any device.
  - **Project file without image**: much smaller. When you import it, you're asked for the floorplan image, and positions are rescaled if the image size differs.
  - **Device data for other tools**: readable JSON listing floors, circuits (with summaries), every device (type, room, status, circuit, position, switch configuration, controls / controlled by, GFCI protection, smart details) and the current checks.

  Downloads use the Claude download prompt when the app is hosted as an artifact, and a normal browser download anywhere else. If neither works, a copy-to-clipboard fallback appears.

## Running

Open `index.html` in a browser. Outside the Claude artifact host, projects are saved to the browser's localStorage. Use **Export → Project file** to keep a portable copy.

When it's hosted as a Claude artifact, the page uses the platform's `db`, `assets`, `downloads` and `user` capabilities to sync projects to your account. It falls back to local storage when those capabilities aren't available.

## Keyboard

`V` select · `T` test mode · `L` link · `C` circuit paint · `Del` delete · `Ctrl+D` duplicate · `Ctrl+Z` / `Ctrl+Shift+Z` undo / redo · arrow keys nudge (Shift for larger steps) · `0` fit · `Esc` exit mode · hold Space to pan
