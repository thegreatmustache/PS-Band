# PS-Band
Repo for COMP3710 - IoT BIT tour
## READ ME

### Documentation

Our artefact is called PS Band, short for 'Party Safe Band'. PS Band is a sort of tracker (like Fitbit, for example) but instead of tracking your steps, it tracks your Blood Alcohol Content (BAC). It is basically a battery powered ESP32 microcontroller which is connected to a alcohol sensor. The idea is that everyone in the group wears a PS Band, which is connected to their phone and sends the wearer’s BAC information over Bluetooth. Therefore, after implementing the server, everyone will be able to monitor their own and additionally, their friends’ BAC values.

### Software

- MacOS 10.0 or above; or Linux;
- Flutter mobile application development
- Android Studio 3.0 or later
- Espressif Integrated Development Framework (ESP-IDF): v3.1.2
- Any text editor (We used VSCode)
- Xtensa architecture specific toolchain (follow the ESP-IDF installation instructions)
- Make command line utility (We used v4.1)

Follow the instructions [here](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html#setup-toolchain) to setup the toolchain for ESP32 on your preferred OS

You might also have to add the IDF-PATH to user profile. Follow the instructions [here](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/add-idf_path-to-profile.html#add-idf-path-to-profile-linux-macos) for more instructions.

Follow the instructions [here](https://flutter.dev/docs/get-started/install) for installing Flutter and [here](https://flutter.dev/docs/get-started/editor) for setting up Android Studio to get the app development framework for this project.

After opening the flutter_app_myapp directory in Android studio, run "flutter packages get" to download the depenancies for this app.

**macOS only**

For macOS, you might have to set the port that the file will be uploaded to. This can be changed via the commnand "make menuconfig" 

![Set upload USB port](dependencies/USB2.png)

After the above the screen appears, go to "Serial flasher config" and then change the USB port in "Default Serial Port". You only have to do it once for the project. The list of USB devices can be found by entering "ls /dev/cu.* " in the terminal.

![Set upload USB port](dependencies/USB1.png)

The project is majorly split into two parts - the ESP-IDF backend and the Flutter front end development. ESP-IDF backend is contained in the folder gatt_server_adc. The main BLE-Gatt-With-Phone.c file is contained in gatt_server_adc -> main. Simply, connected your ESP32 microcontroller and navigate to this folder and run 'make flash monitor' to upload the code.

### Hardware

- 1 x ESP32 microcontroller (We used NODEMCU-32S)
- 1 x Arduino microcontroller (To provide 5.0 V input to the alcohol sensor)
- 1 x MQ-3 (Alcohol sensor)
- 3 x Jumper Cables

The Arduino is used to power the sensor as the sensor requires an input of 5.0V and the NODEMCU-32S only provides 3.3V. In light of this, our current setup is:

![Current Hardware Setup](dependencies/Hardware_Setup.jpg)

Here, the wires connect:

- Indigo: MQ3 Sensor *GND* $\iff$ *GND* ESP32–earthing the sensor
- Red: Arduino *5V Output* $\iff$ *VCC* MQ3 Sensor–powering the sensor
- Yellow: MQ3 Sensor *Analog output* $\iff$ *Pin 34* ESP32–Pin 34 is connected to an analog-digital converter on the ESP32.
- Purple: Arduino *GND* $\iff$ *GND* ESP32–connecting grounds on both boards ensures voltage readings are consistent

### Licensing 

Please refer to a file named 'LICENSE' in the root directory for the licensing details.

### Contact and Contributions

There's still so many ways we could improve this project! We're still looking to sort out the server to mobile app connection. We could also use help improving the overall UI.

If you are interested in this project and would like to contribute, please get in contact with us at chinmay.garg@mail.com
