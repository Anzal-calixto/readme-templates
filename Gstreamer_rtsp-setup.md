# RTSP Server Setup for EVK Streaming

This guide outlines the steps to set up an RTSP server and stream video from an Embedded Vision Kit (EVK) using GStreamer.

---

## 📡 1. Setting Up the RTSP Server

We'll use [**MediaMTX**](https://github.com/bluenviron/mediamtx), a lightweight and powerful RTSP server.

### Steps:

1. **Download MediaMTX:**

   Go to the [MediaMTX Releases Page](https://github.com/bluenviron/mediamtx/releases) and download the appropriate binary for your hardware.

   > 💡 Example: If you're using an **ARM64** architecture, download the file ending in `arm64.tar.gz`.

2. **Install MediaMTX:**

   Open a terminal and run the following:

   ```bash
   mkdir rtsp-server && cd rtsp-server
   wget https://github.com/bluenviron/mediamtx/releases/download/v1.12.3/mediamtx_v1.12.3_linux_arm64.tar.gz
   tar -xvzf mediamtx_v1.12.3_linux_arm64.tar.gz
   ```

   This will extract two files:
   - `mediamtx`
   - `mediamtx.yml` (configuration file)

3. **Start the RTSP Server:**

   To start the server with the default configuration:

   ```bash
   ./mediamtx mediamtx.yml
   ```

   To run it in the background:

   ```bash
   ./mediamtx mediamtx.yml &
   ```

   ✅ The server will now listen on `rtsp://<your-ip>:8554/`.

   > 🔄 For a more permanent solution, consider setting up MediaMTX as a systemd service.

---

## 🎥 2. Streaming Video Using GStreamer

You need to have **GStreamer** installed with all necessary plugins.

### Example Pipeline:

```bash
gst-launch-1.0 v4l2src device=/dev/video0 ! \
video/x-raw,format=YUY2,width=640,height=480,framerate=30/1 ! \
videoconvert ! jpegenc ! jpegparse ! \
rtspclientsink location=rtsp://localhost:8554/mystream
```

### Explanation:
- `v4l2src device=/dev/video0`: Uses your camera device.
- `video/x-raw...`: Sets resolution and frame rate.
- `videoconvert`: Converts to a compatible format.
- `jpegenc` + `jpegparse`: Encodes to JPEG for streaming.
- `rtspclientsink`: Sends the stream to the RTSP server.

> 🛠️ Tip: For better quality or different formats, you can tweak the pipeline (e.g., use `x264enc` instead of `jpegenc` if supported).

---

## ✅ Testing

Once both the server and stream are running, you can test it using an RTSP client such as **VLC**:

```
rtsp://<your-ip>:8554/mystream
```

Replace `<your-ip>` with the IP address of your device.

---

## 🔧 Additional Tips
- Make sure your firewall allows traffic on port **8554**.
- To auto-start the server on boot, configure it as a `systemd` service.
- You can customize the `mediamtx.yml` file for advanced configurations (authentication, logging, etc.).
