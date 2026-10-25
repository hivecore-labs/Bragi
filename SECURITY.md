# Security and verification — AJA Bragi 0.1.6

## English

The installed release was confirmed fully functional on **24 October 2026**. This document describes the security controls and verified scope of the Community release.

### Review scope

The review covers the packaged application, compressed Python code, first-party source correspondence, native libraries, supplied dependency SBOMs, local IPC, voice import, model loading, installation and archive metadata/integrity. Package records are supplied in `BUILD_INFO.json`, `SBOM.cdx.json`, `DEPENDENCY_REVIEW.json` and `SHA256SUMS`.

Dependency review includes runtime Python packages, vendored components, Rust wheel SBOMs and native payloads. **228 OSV package/version queries** are dated **24 October 2026**; selected native NVD lookups are dated **21 October 2026**. Database results depend on ecosystem and advisory coverage. Apple system frameworks are supplied and maintained by macOS.

### Corrections and verified safeguards

- **Certificate trust:** certifi is pinned to **2026.10.19** with a verified wheel hash. The bundled trust store excludes the certificate identified in [certifi's advisory](https://github.com/certifi/python-certifi/security/advisories/GHSA-6q48-6c7w-9gw2).
- **Model transport:** native Xet transport is excluded; explicit model downloads use the reviewed Hub HTTP path. Normal synthesis loads pinned local model snapshots.
- **Local control:** private authenticated IPC, bounded requests and allowlisted controls protect the reading queue. Status exposes state/counts rather than selected text or reference transcripts. There is no application TCP listener.
- **Input and installation:** reference WAVs are format/size/duration checked and privately copied; settings use locking and atomic writes. Services input uses a bounded private pipe. Direct `--install` is rejected; shell/XML argument handling is escaped where applicable.
- **Reading lifecycle:** session history is cleared when the complete queue ends or **Stop & Clear Queue** is selected. The synthesis process is terminated and reaped, with pipes closed. Diagnostic logs use fixed technical events rather than arbitrary worker messages.
- **Packaging:** archive checks cover AppleDouble/Finder sidecars, serialized macOS metadata, unsafe paths/symlinks, file permissions, recognized secret patterns, private publisher identifiers, CRC, checksums and strict code signatures.

### Dependency applicability

The package retains **eleven advisory IDs** with documented applicability assessments. These include Windows-specific findings, reviewed APIs outside Bragi's inspected execution paths, and a compile-time maintenance notice. Safetensors/PyO3/memmap2 and tokenizers/Tokio matches remain disclosed alongside their scoped source/path assessments in `DEPENDENCY_REVIEW.json`.

These assessments are not upstream patches or a formal proof of whole-binary unreachability. Changes to dependencies, loaders, inputs or native descriptor/network APIs require renewed assessment. No zero-vulnerability claim is made.

### Verification boundary

- **122 source regression tests**, including **17 reading-lifecycle cases**. Those 17 also pass against the exact embedded first-party bytecode.
- Real pinned-model generation checks verify finite PCM and lifecycle cleanup. Automated PCM results do not certify pronunciation for every voice or language.
- Package/source correspondence, archive confidentiality/structure, checksums and strict signatures are verified. No confirmed publisher credentials or private system identifiers were found; pattern searches cannot prove every arbitrary or obfuscated secret absent.
- Local installation and functionality are confirmed as of **24 October 2026**. Verification applies to the reviewed local macOS/Apple Silicon environment.
- The Community build is **ad-hoc signed**, without Apple Developer ID or notarization. HiVEGrid attribution and same-source checksums do not independently authenticate an Apple-verified publisher.
- This is a bounded source/package/runtime review, not a security certification. No live network capture or forensic operating-system erasure validation is claimed.

### Privacy by Design

Speech synthesis processes text locally; generated audio is not saved to files. Reading history exists only within the active queue and is cleared at completion or Stop & Clear Queue. Missing-model unplayed text can remain explicitly paused for resume; Clear discards it. Imported reference WAVs and transcripts are intentionally saved local voice settings until profile deletion.

Cached synthesis works offline. Explicit model downloads contact the provider, disclose ordinary connection/repository/client metadata and can use existing Hugging Face credentials or configuration. No selected-text or reference-WAV upload was found in the reviewed synthesis path. macOS memory, swap, audio buffers, backups and source documents/clipboard are outside Bragi's application-level deletion guarantee.

### AJA Voice

**Awaiting licensing approval from ElevenLabs.**

## Deutsch — kurz

Die installierte Release-Fassung wurde am **24. Oktober 2026 als voll funktionsfähig bestätigt**. Geprüft sind Anwendung und komprimierter Code, Abhängigkeiten, lokale Kommunikation, Referenzimport, Modell-/Installationspfade und Paketintegrität. 122 Quelltests und 17 Prüfungen am eingebetteten Code sowie Modell-, Datenschutz-, Prüfsummen- und Signaturnachweise liegen vor. Elf Abhängigkeitshinweise bleiben mit begrenzter Anwendbarkeitsbewertung dokumentiert; eine pauschale Schwachstellenfreiheit wird nicht zugesichert.

Synthese lokal, erzeugtes Audio nur im Speicher, Verlauf nur während der aktiven Warteschlange; Löschung bei deren Ende oder Stopp/Leeren. Eigene Stimmprofile bleiben bis zur Profillöschung gespeichert. Modelldownloads erzeugen normale Verbindungsdaten; Betriebssystem- und Ursprungsdaten sind von der Löschzusage ausgenommen. Ad-hoc-Signierung ohne Developer ID/Notarisierung. **AJA Voice: Lizenzfreigabe von ElevenLabs ausstehend.**
