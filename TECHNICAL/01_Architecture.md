# Technical Architecture — PVR_IPTV

**Upstream:** [https://github.com/kodi-pvr/pvr.iptv](https://github.com/kodi-pvr/pvr.iptv)
**License:** GPL
**Category:** CONSUMER_ELECTRONICS
**Anticloud Integration:** PAX L5 Narrow L2 General 27B + AIOSS + Offline-First

## Upstream Description

IPTV client plugin for Kodi smart TV

## Anticloud Architectural Changes

1. PAX L5 Narrow L2 General 27B local product assistant replacing cloud voice/chat APIs
2. Single-binary firmware package with AIOSS-verified OTA integrity
3. AES-256 encryption for all on-device user data
4. Zero-cloud operation: full functionality without internet
5. GPU/CPU equalizer: inference scales to embedded ARM cortex or x86
6. Zero-telemetry mode: opt-in only, no passive data collection
7. AIOSS audit chain for all settings changes and firmware updates
8. Open API for third-party integrations replacing proprietary SDKs

## Integration Points

- **PAX Inference Socket:** Local HTTP endpoint at `127.0.0.1:11434/v1/chat` — same OpenAI-compatible API, zero cloud
- **AIOSS Hook:** Every write operation calls `aioss_append(event, payload)` before commit
- **Encryption Layer:** All file I/O routed through `anticloud_crypto.encrypt_at_rest()`
- **Single Binary Build:** `pyinstaller anticloud_pvr_iptv.spec` or `go build -o pvr_iptv`

## Deployment Modes

| Mode | Hardware | Notes |
| --- | --- | --- |
| Edge CPU | Raspberry Pi 4 / Intel NUC | Full feature set, PAX on CPU |
| Desktop GPU | RTX 3060 / A10 | PAX GPU inference, <1s latency |
| Server | 2× A100 | Full batch throughput |
| Air-gapped | Any x86/ARM | Zero network dependency |