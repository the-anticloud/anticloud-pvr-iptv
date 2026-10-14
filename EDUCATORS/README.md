# Educators — PVR_IPTV

**Project:** PVR_IPTV  
**Category:** CONSUMER_ELECTRONICS  
**Upstream:** see BENCH.json  
**Pinned commit:** `see BENCH.json`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `4f82b021723be16ca259afb3555eb169a5f8f6081b2fe7119c77bd4864ba1373`  
**Date:** October 2026

## Teaching with PVR_IPTV

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `4f82b021723be16ca259afb3555eb169a5f8f6081b2fe7119c77bd4864ba1373` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
