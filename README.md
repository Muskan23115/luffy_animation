# luffy_animation on arduino 

This project uses an Arduino Uno and a 128x64 I2C OLED display to create a looping, animated face (currently featuring Chibi Luffy!). It uses the `PROGMEM` feature to store custom image frames directly into the Arduino's flash memory, bypassing the Uno's strict RAM limitations.

## 🛠️ Hardware Requirements
* **Arduino Uno** (or compatible board)
* **0.96" I2C OLED Display** (128x64 resolution, SSD1306 Driver)
* **4 Jumper Wires** (Female-to-Male or Male-to-Male depending on your breadboard setup)
* Breadboard (Optional, but recommended)

## 🔌 Wiring Guide
Connecting the OLED display to the Arduino Uno is straightforward. You only need 4 pins:

| OLED Pin | Arduino Uno Pin | Function |
| :--- | :--- | :--- |
| **GND** | `GND` | Ground |
| **VDD / VCC** | `5V` | Power |
| **SCK / SCL** | `A5` | I2C Clock Line |
| **SDA** | `A4` | I2C Data Line |

*(Note: If your display uses `3.3V` logic, connect VDD to the `3.3V` pin instead of `5V`. Check your display's documentation!)*

## 💻 Software Setup (Arduino IDE)

To upload this code, you need to set up the Arduino IDE and install the necessary libraries so the Arduino knows how to talk to the screen.

### 1. Install Required Libraries
1. Open the **Arduino IDE**.
2. Go to **Sketch** -> **Include Library** -> **Manage Libraries...**
3. In the search bar, type `Adafruit SSD1306` and click **Install**.
4. The IDE will likely ask if you want to install missing dependencies (like the `Adafruit GFX Library`). **Click "Install All".**

### 2. Prepare the Board and Port
1. Plug your Arduino Uno into your computer using a USB data cable.
2. Go to **Tools** -> **Board** and select **Arduino Uno**.
3. Go to **Tools** -> **Port** and select the port that shows your Arduino (e.g., `COM3` on Windows, or `/dev/cu.usbmodem...` on Mac).

### 3. Upload the Code
1. Open the `.ino` file from this repository in your Arduino IDE.
2. Click the **Upload** button (the right-pointing arrow at the top left).
3. Wait for the "Done Uploading" message at the bottom. Your animation should start playing immediately!

## 🎨 How to Add Your Own Custom Animations
You can easily swap out the Luffy frames for your own custom animations or faces!

1. **Get your frames:** Find or draw a few frames of an animation (pure black and white works best, but manga-style shading works too).
2. **Crop and Size:** Make sure the images are exactly a `128x64` widescreen ratio.
3. **Convert to C++:** Go to the free browser tool [image2cpp](https://javl.github.io/image2cpp/).
    * **Canvas size:** `128` x `64`
    * **Draw mode:** Select `Dithering` (if the image has shading) or `Black and White` (if it's pure line art).
    * **Code output format:** `Arduino code`
    * **Draw mode (Output):** `Horizontal - 1 bit per pixel`
4. **Generate and Paste:** Click "Generate code". Copy the hex arrays it gives you and paste them over the existing `PROGMEM` arrays in the Arduino code.
