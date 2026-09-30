# Android-adb-Security-Lab
Practical Android security lab covering USB debugging, ADB, scrcpy, authentication, video streaming, USB security risks, and Android endpoint hardening.
## 🔬 Lab Phases

### Phase 1: Android & USB Debugging Setup

Enable **Developer Options** and **USB debugging** on the Android device, then connect the device to the Linux system using USB.

Verify the connection:

```bash
adb devices
```

If the device is authorized, ADB should display it with the status:

```text
XXXXXXXX    device
```

---

### Phase 2: ADB Authentication & Device Verification

Restart the ADB server if required:

```bash
adb kill-server && adb start-server
```

Then verify the Android device:

```bash
adb devices
```

The first connection may display an **"Allow USB debugging?"** prompt on the Android device. The user must explicitly authorize the connected computer.

This phase demonstrates the ADB authentication and trusted-host workflow.

---

### Phase 3: Launching the Remote Control Session

Start scrcpy:

```bash
scrcpy --max-fps 60 --video-bit-rate 16M --turn-screen-off
```

This configuration:

* `--max-fps 60` — limits screen streaming to 60 FPS.
* `--video-bit-rate 16M` — sets the video bitrate to 16 Mbps.
* `--turn-screen-off` — turns off the physical Android display while keeping the scrcpy session active.

### Video-Only Testing

To disable audio forwarding and test screen streaming independently:

```bash
scrcpy --no-audio
```

This starts scrcpy without forwarding Android audio to the computer.

### Remote Input Testing

In the controlled lab environment, test:

* Mouse input
* Keyboard input
* Touch interaction
* Screen responsiveness
* Remote screen control

Only perform these tests on devices you own or have explicit authorization to access.

---

## 🔐 Security Analysis

During the lab, document observations related to:

* ADB authentication and authorization
* Trusted computer/host keys
* USB debugging exposure
* Remote screen-control capabilities
* USB security risks
* Endpoint hardening
* Risks of leaving USB debugging enabled

## 🛡️ Defensive Recommendations

After testing:

1. Disable **USB debugging** when it is no longer required.
2. Do not authorize unknown computers.
3. Avoid connecting your device to untrusted computers.
4. Review and revoke unnecessary debugging authorizations.
5. Keep the Android device updated with security patches.
