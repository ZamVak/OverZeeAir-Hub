# OverZeeAir - Version History

## v1.4.0 (2025-08-19) - Added Auto Update and Improved WiFi Stability along with some bug fixes and enhancements
**Stage:** stable

**Changes:**
- **Added:**
  - Auto Check for updates after regular intervals has been implemented with default check Interval of 10 minutes
  - The user can set the Update check interval through the serial monitor using command-> setUpdateInterval <minutes> where minutes are valid from 1 to 1440. These changes are retained in the NVS using 'Preferences'
  - The System also runs the Update Check process each time the WiFi connection is re-established
  - Added WiFi.onEvent() for better WiFi Events handling, allowing system to retry connection as soon as WiFi disconnects

- **Fixed:**
  - Fixed the issue where the system was failing to start WiFi rescan process after losing connection which was resulting in infinite connection loss.

- **Improved:**
  - The system tracks the duration for which the WiFi is disconnected and last connection retry was attempted, if no retries are detected within a certain timeframe, the system will automatically restart WiFi therefore restarting the scanning process.
  - The system now turns off LocalOTA for the time when Github OTA processes are taking place therefore ensuring no OTA clashes occur.
  - The system now does 2 additional continuous retry attempts at 300ms, 600ms delay in case it fails to fetch JSON on the 1st attempt during the Update Check process.
  - The Code has been modularized into functions for better readability and maintainability.

---

## v1.3.0 (2025-08-10) - Added Local OTA for easy Development and Testing
**Stage:** testing

**Changes:**
- **Added:**
  - Local OTA functionality added for easy development and testing
  - New code can be uploaded to the device wirelessly via the local network over a network port visible in the Arduino IDE
  - This eliminates the need for uploading buggy firmwares to GitHub for testing
  - Once testing is done then the stable firmware binary can be uploaded to GitHub

---

## v1.2.0 (2025-08-10) - Added the feature of Dynamic Wi-Fi Credentials
**Stage:** testing

**Changes:**
- **Added:**
  - Dynamic Wi-Fi Credentials feature added
  - The system now supports dynamic Wi-Fi credentials, allowing users to reset Wi-Fi credentials via serial monitor input
  - The user-entered Wi-Fi credentials are now stored in non-volatile memory using 'Preferences.h' so as to retain them even after power loss or restart.

---

## v1.1.2 (2025-08-10) - Fixed the HTTP error code -5 during firmware download
**Stage:** Stable

**Changes:**
- **Fixed:**
  - Fixed the HTTP error code -5 during firmware download caused by the use of WiFiClient instead of WiFiClientSecure

- **Improved:**
  - The update progress is now visualized on the serial monitor in the form of '[OTA] Progress x%' prints.

---

## v1.1.1 (2025-08-07) - Refactored the JSON parsing for the updated update.json file
**Stage:** unstable

**Changes:**
- **Fixed:**
  - Fixed JSON parsing functionality to ensure it works correctly with the the new update.json structure

---

## v1.1.0 (2025-08-07) - Completed OTA firmware update functionality
**Stage:** unstable

**Changes:**
- **Added:**
  - Complete OTA firmware update functionality
  - The system now auto downloads and flashes itself with the latest firmware
  - LED Breathing added in loop function to test and indicate successful OTA update

---

## v1.0.0 (2025-08-07) - Initial Release with groundwork for OTA firmware updates
**Stage:** Stable

**Changes:**
- **Added:**
  - OTA new firmware availability check
  - Version checking and display on serial monitor
  - Fetching firmware url from Github if update is available