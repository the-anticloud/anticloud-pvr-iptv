# Build and Test

**Project:** `PVR_IPTV`
**Upstream:** https://github.com/kodi-pvr/pvr.iptv
**License:** GPL

## Quick Start

```bash
git clone https://github.com/kodi-pvr/pvr.iptv
cd pvr.iptv
pip install -r requirements-anticloud.txt
python anticloud_main.py --offline --pax-local
```

## Anticloud Improvements Applied

1. PAX L5 Narrow L2 General 27B local product assistant replacing cloud voice/chat APIs
2. Single-binary firmware package with AIOSS-verified OTA integrity
3. AES-256 encryption for all on-device user data
4. Zero-cloud operation: full functionality without internet
5. GPU/CPU equalizer: inference scales to embedded ARM cortex or x86
6. Zero-telemetry mode: opt-in only, no passive data collection
7. AIOSS audit chain for all settings changes and firmware updates
8. Open API for third-party integrations replacing proprietary SDKs

## Benchmark Targets

| Metric | Target |
| --- | --- |
| Latency | Primary inference task: <5s on CPU, <1s on GPU |
| Throughput | Batch processing: >100 items/hour on single CPU server |
| Memory | <8GB RAM for standard deployment |
| Accuracy | Task-specific accuracy within 5% of cloud-API baseline |

## Build Status

Not yet measured. Run verified build and record actual figures above.
