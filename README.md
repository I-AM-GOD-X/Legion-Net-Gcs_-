# Legion Net GCS

Ground Control Software for viewing, replaying, recording, and analyzing telemetry from rockets and aerospace systems.

Created by **Удай**.

---

# ⚠️ Display & Resolution Notice

Legion Net GCS is designed and tested primarily for:

* Display scaling: **100%**
* Resolution: **1920 × 1080 (1080p)**

If UI gaps, oversized panels, or alignment issues appear, your display scaling is likely above 100%. Set scaling back to 100% for correct layout.

---
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ad9f61fc-c71f-4b8e-98bc-a38d6110c63f" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7a79106d-9766-450d-af01-d14e539815c2" />

➡ New user? See [QUICK_START.md](QUICK_START.md)

# 🧭 Interface Layout Overview

The interface is divided into two major parts:

* **Top Section** → Real-time flight visualization and situational awareness
* **Bottom Section** → Connection, control, playback, launch verdicts, and raw telemetry

---

# 🚀 TOP SECTION

## 📊 Telemetry Graph Grid (Top Left)

A **3 × 2 grid** displays six core telemetry graphs:

1. Altitude
2. Vertical Speed
3. Acceleration
4. Gyroscope
5. Temperature
6. Link Quality

Each graph has a squiggly-line toggle icon.

### Graph Modes

* **Complete Graph Mode**

  * Full mission timeline
  * Squiggly icon shown in cyan

* **Time Frame Mode**

  * Displays only a selected time window
  * Window controlled by the slider near the connection panel
  * Adjustable from **1 second to 60 seconds**

### Data Contents

**Altitude**

* GPS altitude
* Barometric altitude

**Vertical Speed**

* GPS vertical velocity
* Barometric vertical velocity

**Acceleration**

* X, Y, Z axes

**Gyroscope**

* Angular rate (X, Y, Z)

**Temperature**

* BMP sensor
* MPU sensor

**Link Quality**

* Packet integrity visualization

Upper graph:

* Lifetime CRC failed
* Total CRC statistics

Lower graph:

* Current / last-second CRC pass vs fail percentage

---

## ⏱️ Telemetry Indicators

Additional flight values:

* FC Time (flight computer internal clock)
* Peak Altitude
* Link RSSI / Link Quality

---

## 🧱 Orientation Panel

Located to the right of the graph grid.

Features:

* Real-time 3D rocket model
* Freehand rotation (click and drag)
* Global axes (X, Y, Z)
* Rocket body axes
* Ground plane reference (blue rectangle)
* FPS counter (top-right)

### Calibration

Allows current physical rocket orientation to be set as reference.

### Background Toggle

Switch between multiple environments.

### Future Expansion

* Custom 3D rocket models selectable by user.

---

## 🧭 Course Panel

Located below the orientation panel.

* Displays GPS-derived course heading.

---

## 🗺️ Map Panel

Right-side map display.

Features:

* Default night-vision map
* Toggle button cycles map types
* Zoomable and pannable
* Auto-centers when GPS data is detected

---

## 🛰️ Satellite Animation

Above the map panel:

* Rotating 3D satellite display
* Shows active satellite count.

---

# 🧩 BOTTOM SECTION

## 🔌 Connection Panel

Main control area for communication and data handling.

Functions include:

* COM port selection
* Baud rate selection
* Connect toggle
* 3D Plot window toggle
* Save telemetry
* Import telemetry
* Time-frame slider (graph window control)

---

## 🔋 Status Panels

### Battery Panel

* Flight computer battery percentage.

### HDOP Panel

* GPS horizontal dilution / accuracy indicator.

### Link RSSI Panel

* Signal strength shown in dB.

---

## 🩺 System Health Panel

Displays readiness of subsystems:

* BMP health
* MPU health
* GPS / location active
* Stable satellite lock
* SD card enabled
* Ejection charge enabled

---

## 🧮 Launch Verdict Panel

Provides final launch decision logic.

Purpose:

* Designed for analog camera setups using DVRs.

Displays:

* Mission elapsed time
* Satellite count
* Link quality
* Battery percentage
* Final verdict (GO / NO-GO)

### NO-GO Reasons

All blocking conditions are listed clearly so the operator knows why launch is restricted.

---

## ⏲️ Optimal Launch Window System

Commercial FPV DVRs commonly record in **5-minute clips (300 seconds)**.

The system:

* Tracks recording time after ejection-charge arming
* Shows optimal launch window
* Recommended launch time = first 30 seconds of each 5-minute interval

Includes:

* Timeline indicator bar
* 300-second timer display

Launch window countdown appears only when all systems show GO status.

---

## 🔐 Supervisor Override

If launch must proceed despite warnings:

* Supervisor override available
* Default PIN: **1111**
* PIN customization planned in future versions.

---

## 🎙️ Voice System

Integrated voice announcements provide status awareness.

Includes:

* System status calls
* Altitude updates
* Battery level alerts
* Link quality
* Vertical speed
* Apogee
* Max altitude
* Landing calls

Options:

* Select different voices
* Disable voice via checkbox.

---

## 🌐 Data Stream (Future Feature)

Planned expansion for cloud-based streaming:

* Telemetry streamed to server infrastructure
* Shared launch platform displays
* Integrated with ICERA Universe ecosystem.

---

## 🚦 Flight State Indicator

Displays current rocket state:

* Idle
* Ascent
* Descent
* Landed

Visual indicator provides quick mission awareness.

---

## 🎞️ Timeline & Playback

Timeline is fully scrubbable.

Capabilities:

* Jump to any time position
* Playback imported data
* Live mode return

Controls:

* Play
* Live
* 1X / 2X playback speed

---

## 📄 Live CSV Footer

Footer displays live raw telemetry stream.

Purpose:

* Quick confirmation that data is being received
* Every field labeled
* Useful for debugging or detailed inspection.

---

# 🧊 Hidden Feature: 3D Plot Window

Opened via **3D Plot** button in connection panel.

Features:

* Separate movable 3D environment
* Rocket fixed at origin
* GPS and altitude data draw full flight trajectory
* Phase/state changes visually differentiated.

### Camera Modes

* Follow (tracks rocket)
* Top view
* Side view
* Free camera exploration

### Additional Features

* Data import for trajectory playback
* Scrubbable timeline
* Background/environment toggles

### Future Expansion

* Globe / Earth view
* Custom 3D models for both visualization windows
* UI updates and enhancements.



# ⚙️ Installation & Usage Guide

## 📥 Installation

1. Go to the **Releases** section of this repository.
2. Download the latest available **EXE** build.
3. Run the installer and complete installation.

After installation, Legion Net GCS is ready to receive telemetry data.

---

## 📄 Telemetry Data Requirement (CSV Structure)

Legion Net GCS expects telemetry input in a **comma-separated (CSV) data format**.

### Basic Rules

* Follow the provided CSV field structure exactly.
* Fields not used by your system may remain **0**.
* Any radio or receiver system may be used (LoRa, custom RF, etc.).
* Your receiving device must reformat incoming telemetry into the required CSV format.
* The formatted CSV data should be printed or forwarded through **Serial output**.

Reference the provided CSV structure file / parameter list for exact field order.

---

# 📄 CSV Telemetry Structure

Legion Net GCS expects telemetry data as a **comma-separated (CSV) serial stream**.

Each telemetry frame must follow the exact order below.

# 🚦 Flight Phase ID Table

The `phase` parameter (CSV field #1) represents the current flight state of the rocket.

Legion Net GCS uses this value to drive:

* State indicator visualization
* Voice announcements
* Timeline behavior
* Flight analysis logic

---

## 📊 Current Phase Definitions

| Phase ID | Name    | Description                                                         |
| -------- | ------- | ------------------------------------------------------------------- |
| **0**    | Idle    | System powered and waiting. No launch detected.                     |
| **1**    | Ascent  | Rocket is climbing after launch. Positive vertical motion expected. |
| **2**    | Descent | Rocket descending after apogee (parachute or ballistic).            |
| **3**    | Landed  | Rocket has landed and flight is complete.                           |

---

## 🔮 Future Expansion

Additional phase states may be added in future versions, but the current stable implementation uses **only Phase IDs 0–3**.

---

## 📌 Example

```csv id="hrv9y7"
1,125.4,48.2,...
```

This indicates the rocket is currently in **Ascent**.


⚠️ Order matters.
Unused fields may be set to `0`.

---

## 🔢 CSV Parameter Order

| # | Parameter  | Description             | Unit    | Typical Range |
| - | ---------- | ----------------------- | ------- | ------------- |
| 1 | `phase`    | Flight phase / state ID | integer | 0–5           |
| 2 | `altitude` | Barometric altitude     | meters  | -50 to 5000+  |
| 3 | `vSpeed`   | Vertical speed          | m/s     | -200 to +200  |

### Accelerometer

| # | Parameter | Description | Unit | Typical Range |
|---|---|---|---|---|
| 4 | ax | Acceleration X | m/s² | -50 to +50 |
| 5 | ay | Acceleration Y | m/s² | -50 to +50 |
| 6 | az | Acceleration Z | m/s² | -50 to +50 |

### Gyroscope

| # | Parameter | Description | Unit | Typical Range |
|---|---|---|---|---|
| 7 | `gx` | Gyro X | deg/s | -2000 to +2000 |
| 8 | `gy` | Gyro Y | deg/s | -2000 to +2000 |
| 9 | `gz` | Gyro Z | deg/s | -2000 to +2000 |


| #  | Parameter | Description              | Unit     | Typical Range |
| -- | --------- | ------------------------ | -------- | ------------- |
| 10 | `mosfet`  | MOSFET / ejection status | bool/int | 0 or 1        |

---

### GPS

| #  | Parameter | Description           | Unit    | Typical Range |
| -- | --------- | --------------------- | ------- | ------------- |
| 11 | `lat`     | Latitude              | degrees | -90 to +90    |
| 12 | `lon`     | Longitude             | degrees | -180 to +180  |
| 13 | `peakAlt` | Peak altitude reached | meters  | 0–10000+      |

---

### Orientation (Estimated)

| #  | Parameter | Description | Unit    | Typical Range |
| -- | --------- | ----------- | ------- | ------------- |
| 14 | `roll_i`  | Roll angle  | degrees | -180 to +180  |
| 15 | `pitch_i` | Pitch angle | degrees | -180 to +180  |
| 16 | `yaw_i`   | Yaw angle   | degrees | 0–360         |

---

### GPS Motion

| #  | Parameter   | Description          | Unit     | Typical Range |
| -- | ----------- | -------------------- | -------- | ------------- |
| 17 | `gpsSpd_i`  | GPS speed            | m/s      | 0–300         |
| 18 | `gpsVSpd_i` | GPS vertical speed   | m/s      | -200 to +200  |
| 19 | `gpsAlt_i`  | GPS altitude         | meters   | -50 to 5000+  |
| 20 | `course_i`  | GPS course heading   | degrees  | 0–360         |
| 21 | `hdop_i`    | GPS HDOP accuracy    | unitless | 0.5–10        |
| 22 | `sats`      | Number of satellites | count    | 0–30          |

---

### Temperatures

| #  | Parameter   | Description            | Unit | Typical Range |
| -- | ----------- | ---------------------- | ---- | ------------- |
| 23 | `bmpTemp_C` | BMP sensor temperature | °C   | -40 to 85     |
| 24 | `mpuTemp_C` | MPU sensor temperature | °C   | -40 to 85     |


---

## 🩺 Health Flags (Boolean)

Values are `0 = FALSE`, `1 = TRUE`.

| #  | Parameter       | Meaning                  |
| -- | --------------- | ------------------------ |
| 25 | `bmpOK`         | BMP sensor healthy       |
| 26 | `mpuOK`         | MPU sensor healthy       |
| 27 | `gpsFixOK`      | GPS fix available        |
| 28 | `gpsSatsOK`     | Sufficient satellites    |
| 29 | `ejectionDone`  | Ejection event completed |
| 30 | `sdEnabled`     | SD card logging active   |
| 31 | `ejectionArmed` | Ejection system armed    |

---

## 🔋 System Status

| #  | Parameter  | Description             | Unit  | Typical Range |
| -- | ---------- | ----------------------- | ----- | ------------- |
| 32 | `fcMillis` | Flight computer runtime | ms    | increasing    |
| 33 | `batteryV` | Battery voltage         | volts | 3.0–12.6      |
| 34 | `rssi`     | Link RSSI               | dB    | -120 to -20   |

---

## 📡 Link Quality / CRC

| #  | Parameter          | Description            |
| -- | ------------------ | ---------------------- |
| 35 | `rxTotalPackets`   | Total received packets |
| 36 | `rxCrcOkPackets`   | CRC passed packets     |
| 37 | `rxCrcFailPackets` | CRC failed packets     |
| 38 | `crcRatio`         | Packet success ratio   |

---

## 🧾 Example Frame

```csv
phase,altitude,vSpeed,ax,ay,az,gx,gy,gz,mosfet,lat,lon,peakAlt,roll,pitch,yaw,gpsSpd,gpsVSpd,gpsAlt,course,hdop,sats,bmpTemp,mpuTemp,bmpOK,mpuOK,gpsFixOK,gpsSatsOK,ejectionDone,sdEnabled,ejectionArmed,fcMillis,batteryV,rssi,rxTotal,rxCrcOK,rxCrcFail,crcRatio
```

---

## 📌 Notes

* Values are already scaled before transmission (divide-by-100 performed in firmware).
* Maintain constant column order.
* Missing sensors should output `0`.
* Send continuously via serial for real-time visualization.



## 🔌 Connecting the System

1. Connect your telemetry receiver or radio device to your laptop.
2. Open Legion Net GCS.
3. Select the correct **COM port**.
4. Select the proper **baud rate**.
5. Press **Connect**.

Once connected:

* Graphs should start updating immediately.
* If graphs are not moving, you are likely in scrub mode.

### If Data Is Not Updating

Click **LIVE** on the timeline to return to real-time mode.

---

## 🚀 During Operation

As telemetry arrives, you can monitor:

* Live graphs
* Orientation
* Map tracking
* Link quality
* Rocket state and launch verdicts

The system automatically updates all visual panels as data is received.

---

## 💾 Saving and Reviewing Data

After flight:

1. Click **Save** in the connection panel.
2. Store the telemetry session.

You can then:

* Scrub through the timeline
* Review altitude and velocity
* Analyze orientation
* Inspect map trajectory
* Study ascent and descent behavior

Playback works independently of live monitoring.

---

## 🖥️ Recommended Launch Station Setup

A **dual-monitor setup** is strongly recommended.

Reason:

* Open the **3D Plot Panel** from the connection panel.
* Move this window to a second screen.
* Monitor live trajectory while keeping main GCS controls visible.

Benefits:

* Better situational awareness
* Real-time trajectory visualization
* Easier mission monitoring

---

## 🧊 3D Plot Panel Usage

The 3D Plot window allows:

* Real-time trajectory visualization
* Free camera movement
* Viewing rocket path in three dimensions

### Additional Advantages

Even if GPS signal temporarily drops:

* The plotted trajectory helps estimate landing direction.
* Operators can infer likely descent path.

---

## ⏱️ Independent Timeline Scrubbing

The 3D Plot window has its own timeline.

This allows you to:

* Scrub through past trajectory data
* Review movement in 3D
* WITHOUT affecting live telemetry running in the main GCS window.

---

## 🧪 Current Version Notes

* Orientation in the 3D plot may currently be fixed in some cases.
* Minor bugs may exist during early releases.

If you encounter issues:

Please report bugs or contact the developer via repository contact details.

---

## 🔮 Upcoming Features (Planned)

Future versions will include:

* Rocket parameter input (weight, height, dimensions)
* Motor configuration input
* Wind speed and location modeling
* Predicted trajectory simulation
* Improved visualization and UI updates

These features are under development.

---

## 📌 Summary

Typical workflow:

1. Install from Releases
2. Feed properly formatted CSV telemetry via Serial
3. Connect COM port and baud rate
4. Monitor flight live
5. Save telemetry after mission
6. Replay and analyze data in 2D and 3D views

Legion Net GCS is designed for live launch operations, analysis, and mission review in a single interface.


---

Legion Net GCS provides:

* Real-time telemetry monitoring
* Launch readiness analysis
* Playback & data review
* 3D orientation and trajectory visualization
* Map-based tracking
* Automated launch window assistance
* Voice-assisted operation

This is the initial release version and will continue evolving with expanded visualization and streaming capabilities.
