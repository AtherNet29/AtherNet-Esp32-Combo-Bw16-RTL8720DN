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
  <i>A single module to stress-test the resilience of 2.4GHz, 5GHz, and Bluetooth networks.</i>
</p>

<hr>

<h2>🌟 Why AETHERNET PRO is Different</h2>
<p>Most tools rely solely on the ESP32, which causes bottlenecks during heavy attacks. AETHERNET PRO utilizes a <b>Distributed Attack System</b>, combining the power of 3 distinct microcontrollers simultaneously:</p>
<ul>
  <li><b>ESP32:</b> Acts as the Master Controller, Web Server, and Password Capture engine.</li>
  <li><b>BW16:</b> Dedicated solely to handling Deauthentication attacks, providing extreme stability for both 2.4GHz & 5GHz networks.</li>
  <li><b>Dual NRF24L01:</b> Runs Continuous Wave Jamming to test Bluetooth frequencies without consuming the main CPU's resources.</li>
</ul>
<p><b>The result?</b> Attacks run smoothly, the UI remains highly responsive, and the success rate of credential capture is significantly higher.</p>

<hr>

<h2>🎯 Key Features</h2>

<h3>📡 WiFi Attacks (2.4GHz & 5GHz)</h3>
<ul>
  <li><b>Smart Deauth Attack:</b> Selectively disconnects targets using the BW16, forcing devices to automatically connect to our fake network (Evil Twin).</li>
  <li><b>Evil Twin & Captive Portal:</b> 100% identical network cloning (Including SSID & Channel). Supports Custom HTML for highly realistic phishing pages.</li>
  <li><b>Rogue AP:</b> Creates a standalone fake Access Point with login pages (Google/Facebook style) to capture credentials.</li>
  <li><b>Beacon Spam:</b> Floods the area with hundreds of fake SSIDs (Customizable up to 50 different names).</li>
  <li><b>Password Auto-Verify:</b> When a victim enters a password on the phishing page, the ESP32 automatically verifies its correctness against the real router in real-time.</li>
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
  <li><b>BW16 Auto-Link:</b> Automatically detects and synchronizes with the BW16 module via Serial.</li>
</ul>

<hr>

<h2>🛠️ Required Hardware Specifications</h2>
<p><b>⚠️ ATTENTION:</b> This firmware is hard-coded specifically for the pinout below. Using different pins will cause malfunction or hardware damage.</p>

<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>Component</th>
    <th style="text-align: center;">Qty</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>ESP32 DevKit V1</td>
    <td style="text-align: center;">1</td>
    <td>Master Controller</td>
  </tr>
  <tr>
    <td>BW16 (RTL8720DN)</td>
    <td style="text-align: center;">1</td>
    <td>Required for 5GHz/2.4GHz Deauth</td>
  </tr>
  <tr>
    <td>NRF24L01+</td>
    <td style="text-align: center;">2</td>
    <td>Required for Bluetooth Jammer</td>
  </tr>
  <tr>
    <td>OLED SSD1306 128x64</td>
    <td style="text-align: center;">1</td>
    <td>I2C Address: 0x3C</td>
  </tr>
  <tr>
    <td>Push Button</td>
    <td style="text-align: center;">4</td>
    <td>UP, DOWN, SELECT, BACK</td>
  </tr>
  <tr>
    <td>10uF Capacitor</td>
    <td style="text-align: center;">2</td>
    <td>Soldered on NRF24L01 VCC</td>
  </tr>
</table>

<h4>🔑 Key Wiring:</h4>
<ul>
  <li><b>OLED:</b> SDA -> GPIO 4 | SCL -> GPIO 5</li>
  <li><b>BW16:</b> TX -> GPIO 26 | RX -> GPIO 25</li>
  <li><b>NRF #1 (HSPI):</b> CE -> GPIO 16 | CSN -> GPIO 15</li>
  <li><b>NRF #2 (VSPI):</b> CE -> GPIO 22 | CSN -> GPIO 21</li>
  <li><b>Buttons:</b> UP -> GPIO 17 | DOWN -> GPIO 33 | SELECT -> GPIO 27 | BACK -> GPIO 32</li>
</ul>

<hr>

<div align="center">
  <h2>💎 Get the Full / Premium Version</h2>
  <p>The file available in this repository is a <b>Trial Version</b>, strictly limited to initial demonstration.</p>
  <p><b>Benefits of purchasing the Premium Version:</b></p>
  <p>
    ✅ No Time Limits (Trial is only 1 minute, Premium is Unlimited).<br>
    ✅ No EEPROM Locks (Can be upgraded to future versions).<br>
    ✅ Lifetime Updates (New features like Auto-Attack Sequence are in development).<br>
    ✅ Technical Support via Telegram (Troubleshooting and custom wiring assistance).
  </p>
  <br>
  <h3>🛒 Price: RP 50.000</h3>
  <br>
  <a href="https://t.me/AtherNet29">
    <img src="https://img.shields.io/badge/Buy_Now-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" />
  </a>
  <br><br>
  <i>Click the button above to chat directly with me on Telegram.</i>
</div>

<hr>

<h2>📸 Preview & Documentation</h2>
<p><b>Web Dashboard Interface:</b></p>
<p align="center">
  <!-- GANTI preview.jpg DENGAN NAMA FILE FOTO ANDA -->
  <img src="preview.jpg" width="800" alt="Dashboard Preview" />
</p>

<p><b>Module Wiring Diagram:</b></p>
<p align="center">
  <!-- GANTI wiring.jpg DENGAN NAMA FILE FOTO ANDA -->
  <img src="wiring.jpg" width="800" alt="Wiring Diagram" />
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
