# Resin Temperature Master (RTM) – User Guide

Welcome to the Resin Temperature Master! The RTM is a smart controller designed to monitor the temperature of your resin 3D printer and automatically control a heater to keep your resin at the perfect consistency for flawless prints.

This guide will walk you through how to read the display, control your heater, and troubleshoot common issues.

---

## 1. Reading the Display

Your RTM controller features an OLED screen that automatically cycles through four informational pages every 5 seconds:

* **QR Code / Control Panel:** Scan this with your smartphone camera to instantly open the web dashboard.
* **Network Info:** Displays your controller's IP address and the name of the Wi-Fi network (SSID) it is connected to. 
* **Temperatures:**
    * **Resin T:** The current temperature of the resin.
    * **Env T:** The temperature inside the printer's enclosure.
    * **Amb T:** The ambient (room) temperature outside the printer.
* **Status Page:** Shows any current system messages (like "All Ok" or "AP Active"), how long the device has been powered on (Uptime), and whether the heater relay is currently ON or OFF.

---

## 2. Accessing the Web Dashboard

The Web Dashboard is where you control the target temperature and configure your device. 

**How to connect:**
1. Ensure your smartphone or computer is on the same Wi-Fi network as the RTM.
2. Scan the QR code on the controller's screen, OR type the **IP Address** shown on the screen directly into your web browser (e.g., `192.168.1.50`).

### What if my Wi-Fi goes down?
If the RTM cannot find your home Wi-Fi network, it will create its own temporary Wi-Fi hotspot so you don't lose control.
* **Network Name:** Looks for a network starting with `ap_rtm_`. The end of the name includes part of your specific board's MAC address. This ensures that if you have multiple RTM devices in the same room, their hotspots won't collide.
* **Password:** `123123123`
* **Access Point IP Address:** `192.168.4.1`

Once connected to this hotspot, a window should automatically pop up on your phone allowing you to control the device or connect it to a new Wi-Fi network. If it doesn't pop up, simply type `192.168.4.1` into your web browser.

---

## 3. Using the Controller

Once you are on the Web Dashboard, you will see a few controls:

### Controlling the Heater
Look for the **Heater Controller**. This acts just like a household thermostat.
* Set your desired target temperature (between 10°C and 45°C).
* The system will automatically turn the heater relay **ON** when the resin falls below your target, and **OFF** when it reaches it.

### Assigning Sensors (Sensor ID Mapping)
Because temperature sensors all look the same to the computer, you need to tell the RTM which sensor is in the resin, which is in the enclosure, and which is measuring the room.
1. Scroll down to the **Configuration** section.
2. Look at the readouts for **Temp. Sensor 1, 2, and 3 ID**. These are the unique digital fingerprints of your plugged-in sensors.
3. Copy these IDs into the **Target ID** text boxes for Resin, Enclosure, and Ambient as desired.
4. Click the **Apply Sensor ID Mapping** button. The controller will briefly restart to save your new layout.

---

## 4. Resetting the Device

If you need to restart your controller or wipe its memory, you have a few options:

* **Soft Restart:** Click the **Restart Controller** button on the Web Dashboard. This simply reboots the device without losing any settings.
* **Factory Reset (Via Dashboard):** Click **Restart with Factory Default Settings**. This will wipe your Wi-Fi credentials and sensor mappings.
* **Physical Factory Reset:** If you cannot access the dashboard, you can force a factory reset manually using the power cable or the physical reset button on the board.
    

    
**Option A (Using the Reset Button):**
If your device has a reset button (usually the left button when looking at the board from the top with the USB port facing down), you can use it to trigger a reset:
1. Press and release the reset button.
2. Wait about 1 to 2 seconds, and press it again.
3. Repeat this exact process **5 times** in a row.
4. After the 5th press, let the device boot up normally. It will wipe itself and start fresh.

**Option B (Using the Power Cable):**
1. Unplug the power from the RTM.
2. Plug it in, wait about 1 to 2 seconds, and unplug it again.
3. Repeat this exact process **5 times** in a row. 
4. On the 6th plug-in, leave it connected. The device will wipe itself and start fresh.

---

## 5. Troubleshooting & Debugging

### The screen says "NAN" for a temperature.
"NAN" stands for *Not A Number*. This means the controller has lost communication with that specific temperature sensor. 
* **Fix:** Check the wires and connectors for the sensor. 
* *Safety Note:* If the Resin Sensor reads "NAN", the RTM will immediately force the heater OFF to prevent overheating your resin. 

### The heater relay isn't clicking on.
1. Check the Web Dashboard to ensure your target temperature is set *higher* than the current resin temperature.
2. Ensure the Resin Sensor isn't reading "NAN".
3. Check the Status Page on the screen to see if it says "Relay: ON". If the screen says ON but the heater isn't heating, check the physical power connections to your heating element.

### The screen says "AP Active".
This means the device has lost connection to your home Wi-Fi and is broadcasting its own emergency hotspot (see Section 2). Check your home router.

## 6. Updating the Firmware

Occasionally, new features or bug fixes may be released for your RTM. You can easily install updates directly through the Web Dashboard. 

**Note:** The update process is exactly the same whether you are connected normally via your home Wi-Fi or directly via the `ap_rtm_` emergency hotspot.

1. **Download the new firmware file:** This file will usually end in `.bin` (for example, `rtm_update_v1.2.bin`) and should be saved to your computer or phone.
2. **Open the Web Dashboard:** Connect to the controller as described in Section 2.
3. **Locate the OTA Update section:** Scroll to the very bottom of the web dashboard.
    


4. **Select the file:** Click the **Choose File** button and select the `.bin` file you downloaded earlier.
5. **Start the update:** Click the **Update** button. 
6. **Wait for completion:** **Do not unplug the device or close the browser window** while the update is running. Once it reaches 100%, the RTM will automatically restart and run the new firmware.