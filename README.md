<div align="center">
  <img src="https://img.shields.io/badge/Version-1.0-blue?style=for-the-badge&logo=arduino" />
  <img src="https://img.shields.io/badge/Chip-ESP32_%2B_BW16-black?style=for-the-badge&logo=espressif" />
  <img src="https://img.shields.io/badge/Status-PREMIUM-success?style=for-the-badge" />
  <br><br>
  <img src="https://img.shields.io/badge/🛡️_Educational_Purpose_Only-IMPORTANT-red" />
</div>

<h1 align="center">⚡ AETHERNET PRO</h1>
<p align="center">
  <b>Advanced Multi-Vector WiFi & Bluetooth Security Audit Tool</b><br>
  <i>Dual modules to stress-test the resilience of 2.4GHz, 5GHz, and Bluetooth networks.</i>
</p>

<hr>

<h2>🎯 Feature Details</h2>

<h3>📡 WiFi Attacks (2.4GHz & 5GHz)</h3>
<ul>
  <li><b>Smart Deauth Attack:</b> Selectively disconnects targets using BW16, forcing devices to automatically connect to our fake network (Evil Twin).</li>
  <li><b>Evil Twin & Captive Portal:</b> 100% identical network cloning (Including SSID & Channel). Supports Custom HTML for highly realistic phishing pages.</li>
  <li><b>Rogue AP:</b> Creates a standalone fake Access Point with login pages (Google/Facebook style) to capture credentials.</li>
  <li><b>Beacon Spam:</b> Floods the area with hundreds of fake SSIDs (Customizable up to 50 different names).</li>
  <li><b>Password Auto-Verify:</b> When a victim enters a password on the phishing page, it automatically verifies its correctness against the real router in real-time.</li>
</ul>

<h3>📻 Bluetooth Attacks</h3>
<ul>
  <li><b>Dual Channel BT Jammer:</b> Uses 2x NRF24L01 (HSPI & VSPI) to perform Continuous Wave Jamming on BT frequencies, testing the vulnerability of Bluetooth IoT devices.</li>
</ul>

<h3>🖥️ Interface & Control</h3>
<ul>
  <li><b>Dark Web Dashboard:</b> Futuristic web interface, mobile-responsive, equipped with a color theme system.</li>
  <li><b>3D OLED Menu:</b> Physical navigation using 4 buttons with a 3D Scroll style menu and custom icons.</li>
  <li><b>File Manager:</b> Upload/Edit phishing HTML templates directly from the browser.</li>
  <li><b>BW16 Auto-Link:</b> Automatically detects and synchronizes with the BW16 module.</li>
</ul>

<hr>

<h2>🛠️ Detailed Hardware & Pinout Specifications</h2>
<p><b>⚠️ STRICT WARNING:</b> This firmware is hard-coded specifically for the pinout below. Using different pins will cause immediate malfunction or permanent hardware damage. Ensure strict adherence to this wiring diagram.</p>

<h3>1. OLED Display (SSD1306 128x64 - I2C)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>OLED Pin</th>
    <th style="text-align: center;">ESP32 Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>SDA</td><td style="text-align: center;"><b>GPIO 4</b></td><td>Data Line</td></tr>
  <tr><td>SCL</td><td style="text-align: center;"><b>GPIO 5</b></td><td>Clock Line</td></tr>
  <tr><td>VCC</td><td style="text-align: center;"><b>3.3V</b></td><td>DO NOT use 5V</td></tr>
  <tr><td>GND</td><td style="text-align: center;"><b>GND</b></td><td>Common Ground</td></tr>
</table>
<p><i>* I2C Address must be set to <b>0x3C</b>.</i></p>

<h3>2. BW16 Deauther Module (RTL8720DN - UART1)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>BW16 Pin</th>
    <th style="text-align: center;">ESP32 Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>PB1 (RX)</td><td style="text-align: center;"><b>GPIO 25</b></td><td>ESP32 TX → BW16 RX</td></tr>
  <tr><td>PB2 (TX)</td><td style="text-align: center;"><b>GPIO 26</b></td><td>ESP32 RX ← BW16 TX</td></tr>
  <tr><td>GND</td><td style="text-align: center;"><b>GND</b></td><td>Common Ground (CRITICAL)</td></tr>
</table>
<p><i>* BW16 requires its own separate Deauther firmware to function. Only connect TX to RX and RX to TX.</i></p>

<h3>3. NRF24L01 #1 - Bluetooth Jammer (HSPI Bus)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>NRF24L01 Pin</th>
    <th style="text-align: center;">ESP32 Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>CE</td><td style="text-align: center;"><b>GPIO 16</b></td><td>Chip Enable</td></tr>
  <tr><td>CSN</td><td style="text-align: center;"><b>GPIO 15</b></td><td>Chip Select</td></tr>
  <tr><td>MOSI</td><td style="text-align: center;"><b>GPIO 13</b></td><td>HSPI Default</td></tr>
  <tr><td>MISO</td><td style="text-align: center;"><b>GPIO 12</b></td><td>HSPI Default</td></tr>
  <tr><td>SCK</td><td style="text-align: center;"><b>GPIO 14</b></td><td>HSPI Default</td></tr>
  <tr><td>VCC</td><td style="text-align: center;"><b>3.3V</b></td><td>DO NOT use 5V</td></tr>
  <tr><td>GND</td><td style="text-align: center;"><b>GND</b></td><td>Common Ground</td></tr>
</table>

<h3>4. NRF24L01 #2 - Bluetooth Jammer (VSPI Bus)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>NRF24L01 Pin</th>
    <th style="text-align: center;">ESP32 Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>CE</td><td style="text-align: center;"><b>GPIO 22</b></td><td>Chip Enable</td></tr>
  <tr><td>CSN</td><td style="text-align: center;"><b>GPIO 21</b></td><td>Chip Select</td></tr>
  <tr><td>MOSI</td><td style="text-align: center;"><b>GPIO 23</b></td><td>VSPI Default</td></tr>
  <tr><td>MISO</td><td style="text-align: center;"><b>GPIO 19</b></td><td>VSPI Default</td></tr>
  <tr><td>SCK</td><td style="text-align: center;"><b>GPIO 18</b></td><td>VSPI Default</td></tr>
  <tr><td>VCC</td><td style="text-align: center;"><b>3.3V</b></td><td>DO NOT use 5V</td></tr>
  <tr><td>GND</td><td style="text-align: center;"><b>GND</b></td><td>Common Ground</td></tr>
</table>
<p><b>⚠️ IMPORTANT:</b> Solder a <b>10uF Capacitor</b> directly between the VCC and GND pins on <b>BOTH</b> NRF24L01 modules to prevent voltage drops and crashes during transmission.</p>

<h3>5. Physical Control Buttons</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>Function</th>
    <th style="text-align: center;">ESP32 Pin</th>
    <th>Connection</th>
  </tr>
  <tr><td>UP</td><td style="text-align: center;"><b>GPIO 17</b></td><td>Button → GND (Uses Internal Pull-Up)</td></tr>
  <tr><td>DOWN</td><td style="text-align: center;"><b>GPIO 33</b></td><td>Button → GND (Uses Internal Pull-Up)</td></tr>
  <tr><td>SELECT</td><td style="text-align: center;"><b>GPIO 27</b></td><td>Button → GND (Uses Internal Pull-Up)</td></tr>
  <tr><td>BACK</td><td style="text-align: center;"><b>GPIO 32</b></td><td>Button → GND (Uses Internal Pull-Up)</td></tr>
</table>

<h3>6. On-Board Components</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>Component</th>
    <th style="text-align: center;">Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>Built-in LED</td><td style="text-align: center;"><b>GPIO 2</b></td><td>Used for Status Indicators</td></tr>
</table>

<hr>

<h2>📦 How to Flash the Firmware (.bin)</h2>

<h3>1. Flashing the ESP32</h3>
<ul>
  <li>Make sure you have installed USB Serial Driver on your Windows PC or the COM port will not appear</li>
  <li>Open flash_download_tool (Windows) or ESP32_Flash App (Android)</li>
  <li>Select your board</li>
  <li>Erase the board first</li>
  <li>Load the file</li>
  <li>Set the offset to 0x0</li>
  <li>Flash</li>
  <li><b>ATHERNET SSID will appear shortly</b></li>
</ul>

<h3>2. Flashing the BW16</h3>
<p><i>The BW16 module uses the Web Serial interface; ensure you are using the Google Chrome or Microsoft Edge browser.</i></p>
<ol>
  <li>Open your browser (Chrome/Edge) and visit the following website: <a href="https://nethercap-web-flasher-v2.vercel.app/">https://nethercap-web-flasher-v2.vercel.app/</a></li>
  <li>Connect the BW16 module to your PC using a USB cable (ensure the cable supports data transfer, not just charging).</li>
  <li>Put the BW16 module into Bootloader Mode (usually by pressing and holding the BOOT button, then pressing and releasing the RST/EN button, and finally releasing the BOOT button).</li>
  <li>On the website, click the "Connect" or "Select Port" button and choose the COM port corresponding to the BW16.</li>
  <li>Click "Choose File" and select the appropriate BW16 firmware file (.bin).</li>
  <li>Click the "Flash" button on the website and wait for the process to complete and display a success message.</li>
</ol>
<p>📥 <b>Download the required .bin files here:</b> <a href="https://github.com/AtherNet29/AtherNet-Esp32-Combo-Bw16-RTL8720DN/releases/tag/File_Upload">AETHERNET Firmware Releases</a></p>

<h3>❓ What if the SSID does not appear?</h3>
<ol>
  <li>The ESP32 is still on bootloader mode. Unplug then plug it</li>
  <li>The binary file does not match with your ESP32 Chip</li>
  <li>You set the configuration wrong</li>
  <li>You did not erase it before flashing</li>
</ol>

<hr>

<div align="center">
  <h2>💎 Get the Full / Premium Version</h2>
  <p>The file available in this repository is a <b>Trial Version</b>, strictly limited to initial demonstration.</p>
  <p><b>Benefits of purchasing the Premium Version:</b></p>
  <p>
    ✅ No Time Limits (Premium Unlimited/Permanent).<br>
    ✅ Get Latest Updates (Can be upgraded to newer versions later).<br>
    ✅ Each purchase includes 2 free updates. You can request it anytime if there is a newer release.<br>
    Contact me on Telegram if you are interested.<br>
    The price above is for 1 copy of the binary file and cannot be duplicated.<br>
    ✅ Technical Support via Telegram (Troubleshooting and custom wiring assistance).
  </p>
  <h3>🛒 Price: RP 50.000</h3>
  <br>
  <a href="https://t.me/+6283141852690">
  <img src="https://img.shields.io/badge/Buy_Now-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" />
  </a>
  </a>
  <br><br>
  <i>Click the button above to chat directly with me on Telegram.</i>
</div>

<hr>

<h2>📸 Preview & Documentation</h2>
<p><b>Web Dashboard Interface:</b></p>
<p align="center">
 <img src="https://raw.githubusercontent.com/AtherNet29/AtherNet-Esp32-Combo-Bw16-RTL8720DN/134ee7f6ee2d5a1805c25577202dfdea174c7670/HALAMAN%20DASHBOAR.jpg" width="250" alt="Dashboard Preview" />
</p>

<p><b>Module Wiring Diagram:</b></p>
<p align="center">
  <img src="https://raw.githubusercontent.com/AtherNet29/Esp32-Bw16-RTL8720DN-2.4-Ghz-dan-5Ghz-Deauther-Eviltwin-Jammer-Bluetooth/7c5dc59d85d41146c9d3b698d9b242c6fb308bc9/schematic.jpg" width="800" alt="Wiring Diagram" />
</p>

<hr>

<div align="justify" style="background-color: #ffcccc; padding: 15px; border-left: 5px solid #ff0000;">
  <h3>⚖️ Legal Disclaimer</h3>
  <b>STRICT WARNING:</b> This tool is created purely for <i>Penetration Testing</i> and <i>Educational Purposes</i> within the scope of network security. It is strictly forbidden to use this tool to attack, steal data, or disrupt networks that are NOT your property. Any form of abuse that violates your country's laws is <b>NOT</b> the responsibility of the Developer. By purchasing this firmware, you agree to these terms and conditions.
</div>

<div align="center">
  <br>
  <sub>Built with ❤️ by AETHERNET Developer Team</sub>
</div>
