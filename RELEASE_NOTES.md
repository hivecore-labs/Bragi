# AJA Bragi 0.1.6 — HiVEGrid Community

## English

**HiVEGrid / Local TTS Engine · Apple Silicon · macOS 26.2 or later**

### Features

- Native **Bragi TTS** service and transparent menu-bar signet with live status and queue controls.
- **Previous**, **Pause / Resume**, **Next**, **Stop & Clear Queue** and F7/F8/F9 media keys.
- Persisted **English / German** interface; welcome speech follows the primary system language (German, otherwise English). Installation messages are English.
- Nine Qwen preset voices, with Ryan as the default. Fourteen male/female profiles cover German, English, French, Spanish, Italian, Portuguese and Russian. Accents vary; language selection does not translate text.
- **Bring Your Own Voice:** private reference-WAV import with an exact transcript and the necessary rights to the recording and voice for AI reference use.
- German pronunciation preparation for names, numbers, amounts, times, ordinals and named-month dates.

### Privacy by Design

Speech synthesis runs locally. Generated speech stays in memory; Bragi does not save audio files. Reading history exists within the active queue and is cleared at completion or **Stop & Clear Queue**, with the speech process terminated and reaped. Imported voice profiles remain private local settings until deleted. Synthesis works offline after the required models are cached.

Missing-model unplayed text may remain paused for download/resume; Clear discards it. Model-download metadata and operating-system/source-application deletion limits are described in [SECURITY.md](SECURITY.md).

### AJA Voice — Coming Soon

**Awaiting licensing approval from ElevenLabs.** Availability is subject to the necessary rights; no release date is promised.

**Your voice. Your machine. Your choice.**

### Verification and distribution

The installed release was confirmed fully functional on **24 October 2026**. Verification includes 122 source regression tests, 17 exact-frozen-code privacy tests, real model PCM checks, source correspondence, package confidentiality/integrity checks and strict signatures. Verification applies to the reviewed local macOS/Apple Silicon environment. Known dependency matches retain scoped applicability assessments; no vulnerability-free claim is made.

Community signing is ad hoc, without Apple Developer ID or notarization. Free binary use is covered by the included license; commercial redistribution or sale requires separate permission and source remains reserved. Third-party licenses apply independently. Verify the download with its matching `.zip.sha256` file.

## Deutsch — kurz

Bragi 0.1.6: native Menüleiste und **Bragi TTS**, Live-Status/Warteschlange, Zurück/Pause/Fortsetzen/Weiter, **Stopp & Leeren**, Medientasten und EN/DE-Oberfläche. Neun Presets plus je ein männliches/weibliches Profil für sieben europäische Sprachen sowie eigener WAV-/Transkript-Import mit erforderlichen Nutzungsrechten. **Privacy by Design:** lokale Synthese, Audio im Speicher, Vorleseverlauf nur innerhalb der aktiven Warteschlange, eigene Stimmprofile bis zur Profillöschung. Die installierte Release-Fassung wurde am **24. Oktober 2026 als voll funktionsfähig bestätigt**. **AJA Voice: Lizenzfreigabe von ElevenLabs ausstehend.** Ad-hoc-Community-Signierung, kostenlose Binärnutzung, kommerzieller Vertrieb nur mit Erlaubnis und Quellcode vorbehalten.
