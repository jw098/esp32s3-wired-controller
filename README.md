# How to Build for Windows


## Install ESP-IDF
https://docs.espressif.com/projects/esp-idf/en/stable/esp32/get-started/windows-setup.html

On Windows, you can use the installer. I recommend ensuring that the Command Prompt Desktop shortcut is checked during installation.

## Build
1. Clone this repo.
2. Open ESP-IDF terminal (you may use the Desktop shortcut created during installation)
3. In the terminal, change the directory to the repo root:
4. Run in ESP-IDF terminal: `idf.py set-target esp32S3`
4. Run in ESP-IDF terminal: `idf.py build`

# Troubleshooting

## setup()/loop() vs app_main()
Type into terminal: `idf.py menuconfig`. Select `Arduino Configuration`. Ensure `Autostart Arduino setup and loop on boot` is checked if the main.cpp uses `setup()` and `loop()` functions. In contrast, if using `app_main()`, ensure it is unchecked

# Notes on dependencies

This repo requires the Arduino framework as well as TinyUSB. These dependencies should already be included in this repo.

See here for more information: https://docs.espressif.com/projects/arduino-esp32/en/latest/esp-idf_component.html

## Adding the Arduino Framework
Run command in ESP-IDF terminal: `idf.py add-dependency "espressif/arduino-esp32`

## Adding TinyUSB
Run command in git bash: 
```
git clone https://github.com/espressif/esp32-arduino-lib-builder.git esp32-arduino-lib-builder && \
git clone https://github.com/hathach/tinyusb.git esp32-arduino-lib-builder/components/arduino_tinyusb/tinyusb
```

In the project folder, edit CMakeLists.txt and add the following before the `project() line:

`set(EXTRA_COMPONENT_DIRS <path to esp32-arduino-lib-builder/components/arduino_tinyusb>)`

# Credits
The code was taken from here: https://github.com/esp32beans/switch_ESP32

Some changes were made so that the project could be built with ESP-IDF, instead of Arduino IDE.