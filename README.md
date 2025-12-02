## WateringKart – Real-Time MQTT Heatmap (8×8 → 64×64)

This project visualizes live data from an 8×8 sensor array as a smooth 64×64 heatmap in the browser.  
Sensor frames are published via MQTT, and a lightweight HTML/JavaScript client subscribes to the data and renders it in real time using Plotly.

### How it works

- Devices publish frames to an MQTT broker (e.g. `test.mosquitto.org`) on topics of the form:
  `wateringkart/<MAC>/frame`.
- Each frame is a string containing:
  - A timestamp in microseconds.
  - 64 numeric values corresponding to an 8×8 matrix (row-major).
- The web client (hosted e.g. on GitHub Pages) connects to the broker via MQTT over WebSockets.
- Incoming 8×8 frames are upscaled to 64×64 using bicubic interpolation (Catmull–Rom) to produce a smoother heatmap.
- The resulting 64×64 grid is rendered with Plotly as a live, browser-based heatmap that anyone can access without installing anything.

### Features

- ✅ **Real-time visualization** of MQTT sensor data in the browser.  
- ✅ **No installation required** for viewers – just open the webpage.  
- ✅ **Cubic interpolation** to upscale 8×8 frames to a smooth 64×64 heatmap.  
- ✅ **Python simulator** to publish random test frames to the MQTT topic.  

This setup is ideal for quickly sharing live sensor data (e.g. thermal or moisture maps) with multiple users over the web using only free services.
