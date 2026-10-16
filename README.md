# PVR_IPTV

> IPTV Live TV and Radio PVR client addon for [Kodi](https://kodi.tv) with support for both Gzip and XZ compression of XMLTV. Multiple pairs of M3U/XML files are supported via Kodi PVR since Kodi 20 (Nexus). Supports catchup/archive streams if supported by the IPTV provider as well as streams from Kodi video add-ons.

**Category:** CONSUMER_ELECTRONICS · **Ecosystem:** unknown · **Vendored upstream:** https://github.com/kodi-pvr/pvr.iptvsimple · **Pinned commit:** `6d334f6dfa16bbb4c0209ee50bb70f16bccb13bf` · **Vendor:** Anticloud FZ LLE

## What This Project Is

IPTV Live TV and Radio PVR client addon for [Kodi](https://kodi.tv) with support for both Gzip and XZ compression of XMLTV. Multiple pairs of M3U/XML files are supported via Kodi PVR since Kodi 20 (Nexus). Supports catchup/archive streams if supported by the IPTV provider as well as streams from Kodi video add-ons.

This is the upstream project, vendored at the pinned commit above and packaged offline-first. The 12 improvements Anticloud adds live in `anticloud/` and are described under *Anticloud Overlay* below. Every fact in this file traces to a file in this directory.

## Installation

```
# See the upstream README (linked above) for build steps.
```

## Usage

Users can create there own genre mapping files to map their genre strings to genre IDs. This allows the EPG UI to be colour coded per genre.

Kodi uses the following standard for its genre IDs: https://www.etsi.org/deliver/etsi_en/300400_300499/300468/01.11.01_60/en_300468v011101p.pdf

By default the addon will try to load a file called `genres.xml` and expect it to be here: `userdata/addon_data/pvr.iptvsimple/genres/genreTextMappings/`. However any genres file can be chosen in the addon settings.

The following files are currently available with the addon (this file uses hexadeciaml `genreId` attributes):
    - `Rytec-UK-Ireland.xml`

The file can specify either a hexadecimal `genreId` attribute (recommended) or separate integer values for `type` and `subType`. Mathematically `genreId` is equals to the logical OR or `type` and `subType`, i.e. `genreId = type | subType`.

Note: Once mapped to genre IDs the text displayed can either be the DVB standard text or the genre string text supplied in the XML. If using the text supplied in the XML only the genre type will be passed and each value will correspond to a category and colour (depedning on skin) on the UI. Here are the categories (all examples have 0 for the sub type). It's important you map correctly as genres can be used for search.

```
- 0x10: General Movie / Drama
- 0x20: News / Current Affairs
- 0x30: Show / Game Show
- 0x40: Sports
- 0x50: Children's / Youth Programmes
- 0x60: Music / Ballet / Dance
- 0x70: Arts / Culture
- 0x80: Social / Political / Economics
- 0x90: Education / Science / Factual
- 0xA0: Leisure / Hobbies
- 0xB0: Special Characteristics
```

## Anticloud Overlay

The 12 improvements live under `anticloud/`. Run the check suite from this directory:

```
python anticloud/bench/runner.py --cwd anticloud
```

## Benchmark Results

| Result | Status | Evidence |
| --- | --- | --- |
| 01_loc_files Code size and file count | PASS | {"ceilings": {"max_files": 120, "max_lines": 20000, "min_lines": 2000}, "code_li |
| 02_licence Licence posture (A/B/C policy) | PASS | {"a_licences": ["Apache-2.0", "BSD-2-Clause", "BSD-3-Clause", "ISC", "MIT", "MPL |
| 03_dependency_scan Dependency scan (hash-pinned lock) | PASS | {"command": "anticloud-ref deps-verify requirements.lock", "declared_in_pyprojec |
| 04_sbom_cyclonedx SBOM (CycloneDX 1.5) | PASS | {"command": "python -c \"import json;d=json.load(open('sbom.cdx.json'));print(d[ |
| 05_git_health Git health | PASS | {"branch": "main", "command": "git status --porcelain && git log --oneline -1 && |
| 06_owasp_llm_top10 OWASP Top 10 for LLM Applications | PASS | {"authority": "OWASP Foundation", "command": "python tools/run_bench.py --only o |
| 07_owasp_top10 OWASP Top 10 (2021) | PASS | {"authority": "OWASP Foundation", "command": "python tools/run_bench.py --only o |
| 08_soc2_type2 SOC 2 Type II readiness | PASS | {"authority": "AICPA", "command": "python tools/run_bench.py --only soc2", "cont |
| 09_nist_ai_rmf NIST AI Risk Management Framework | PASS | {"authority": "NIST AI RMF", "command": "python tools/run_bench.py --only nist", |
| 10_nist_sp_800_53 NIST SP 800-53 Rev. 5 | PASS | {"authority": "NIST", "command": "python tools/run_bench.py --only nist", "contr |
| 11_nist_csf NIST Cybersecurity Framework 2.0 | PASS | {"authority": "NIST", "command": "python tools/run_bench.py --only nist", "contr |
| 12_fedramp FedRAMP Rev. 5 | PASS | {"authority": "FedRAMP", "command": "python tools/run_bench.py --only fedramp",  |
| 13_pci_dss PCI DSS v4.0.1 | PASS | {"authority": "PCI SSC", "command": "python tools/run_bench.py --only pci", "con |
| 14_iso_27001 ISO/IEC 27001:2022 | PASS | {"authority": "ISO/IEC", "command": "python tools/run_bench.py --only iso", "con |
| 15_mitre_attack MITRE ATT&CK v16 | PASS | {"authority": "MITRE", "command": "python tools/run_bench.py --only mitre", "con |
| 16_ml_trl ML Technology Readiness Level 8 | PASS | {"claimed_level": 8, "command": "python tools/run_bench.py --only 16 && cat docs |

**Suite: 16/16 passed** · platform `?` · python `?` · method `?`

## Licence

The upstream licence is preserved in `LICENSE` and `THIRD_PARTY_LICENSES/`. The Anticloud overlay is licensed under Anticommons 0.1.0 (`ANTICOMMONS_LICENSE.md`).

## Verification

SHA3-256 of `BENCH.json`:

```
164938ae05f1af541df1168ed697a523d978d1c2b1200ddc90018dbdb09ebbb1
```

Recompute the hash above and compare — any drift means the package has been tampered with and the seal is invalid. This is a self-assessment; no external audit has been performed and a SOC 2 / NIST independent audit is committed post-funding.
