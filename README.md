# AJA Bragi

**HiVEGrid / Local TTS Engine**

**Local AI Text-to-Speech for macOS. Custom Voices. Privacy by Design.**

Bragi is a local text-to-speech app for Apple Silicon Macs, with a native menu bar, macOS Services and private voice-reference import.

**0.1.6 Community · arm64 · macOS 26.2 or later.** Ryan is the default preset. This is a binary release; the first-party source code remains reserved.

## Features

- Select text in a compatible app and choose **Services → Bragi TTS**. The Bragi menu starts automatically.
- View live playback status, the active voice and queued sections in a compact panel.
- Use **Previous**, **Pause / Resume**, **Next** and **Stop & Clear Queue**, with F7/F8/F9 media-key support.
- Switch the complete interface between **English and German** with **EN / DE**.
- Choose nine Qwen presets or fourteen male/female language profiles for German, English, French, Spanish, Italian, Portuguese and Russian.
- Import a rights-cleared reference WAV with its exact transcript for a private custom voice.
- German text preparation covers names, numbers, amounts, times, ordinals and named-month dates such as `5. Oktober`. Pronunciation remains model-dependent.

## Privacy by Design — Your Voice. Your Data. Your Machine.

- **Local speech synthesis:** your text is processed on your Mac.
- **No saved generated speech:** Bragi processes generated audio in memory, without saving audio files.
- **No persistent reading history:** Previous works within the active queue. At the end of the complete queue, or on **Stop & Clear Queue**, Bragi clears the session's text/history and terminates and reaps the speech process.
- **Private custom voices:** reference recordings and transcripts stay in private local settings until you delete their profiles.
- **Offline speech:** synthesis works without Internet once the required models are cached. Model downloads are explicit and require Internet access.

If a model is missing, unplayed text can remain paused for download/resume; **Stop & Clear Queue** discards it. Downloads contact the model provider and can use existing Hugging Face configuration. Application-level cleanup does not guarantee forensic erasure from macOS memory, swap, audio buffers, backups or the source application/clipboard. See [security and verification boundaries](SECURITY.md).

## Bring Your Own Voice

The preset voices are a starting point; quality and accents vary. Bragi's strength is bringing your own voice: import a clear recording with its exact matching transcript for a personal, fully local TTS experience.

In **Voices → Add a reference WAV**, supply a name, recording, exact transcript and recording language (German or English). Supported recordings are **3–30 seconds**, uncompressed PCM WAV, **16/24/32-bit**, **16–96 kHz**, mono/stereo, up to **32 MB**. You must have the necessary rights to both the recording and the voice for AI reference use. **Save & use** creates a private local copy; no training or upload is performed.

Voice changes apply at the next section boundary. **Preview voice** appends a sample to the queue. Select another voice before deleting a custom profile. Profiles are stored under `~/Library/Application Support/AJA Bragi` with private permissions.

**Your voice. Your machine. Your choice.**

## Presets and languages

The nine presets are Ryan, Aiden, Vivian, Serena, Uncle Fu, Dylan, Eric, Ono Anna and Sohee. Fourteen language profiles provide **Male / Ryan** and **Female / Serena** for each of **German, English, French, Spanish, Italian, Portuguese and Russian**. These profiles select the output language and reuse the model's multilingual timbres; accents vary. Bragi reads text aloud and does not translate it. German number/date preparation applies when German is selected.

Presets use the pinned Qwen CustomVoice model; custom references use the pinned Base model. **Download / check voice models** explicitly downloads the required snapshots. Normal reading, status polling and reference import use local resources. Models are downloaded separately from the app.

## Install

1. Download `AJA-Bragi-0.1.6-arm64.zip` and its `.zip.sha256` file from **Releases**.
2. Verify them with `shasum -a 256 -c AJA-Bragi-0.1.6-arm64.zip.sha256`.
3. Extract the complete ZIP and run **Install_Mac.command**.
4. Review macOS approvals for the named Bragi component. Setup installs the app, loads the model, speaks a welcome in German or English according to the primary system language, and registers **Bragi TTS**.

Python and runtime libraries are included. Installation needs no separate Python, Homebrew or Xcode. Allow several GB for models and sufficient room for the staged app copy. See the [installation guide](INSTALLATION.md) for macOS approvals, storage and media-key troubleshooting.

## Playback

Select text → **Services → Bragi TTS**. Further selections join the queue. Click the menu signet for controls:

- **Previous / F7:** previous section within the active reading.
- **Pause or Resume / F8:** pause or continue.
- **Next / F9:** next section.
- **Stop & Clear Queue:** stop current speech and discard the queue and session history.

Depending on keyboard settings, also hold Fn. Assign a shortcut under **System Settings → Keyboard → Keyboard Shortcuts → Services → Bragi TTS**. Closing the panel keeps the icon; **Quit menu** closes the menu while reading continues independently. Status polling does not extend the engine's idle timer.

## AJA Voice — Coming Soon

**Awaiting licensing approval from ElevenLabs.** Availability is subject to the necessary rights; no release date is promised.

## Verification, signing and license

The installed release was confirmed fully functional on **24 October 2026**. Automated evidence includes 122 source regression tests, 17 exact-frozen-code privacy tests, real model checks, package/privacy checks and strict signature verification. Verification applies to the reviewed local macOS/Apple Silicon environment. See [verification status](RELEASE_STATUS.md) and [security scope](SECURITY.md).

The Community build is ad-hoc signed, without Apple Developer ID or notarization. HiVEGrid attribution and checksums do not independently authenticate an Apple-verified publisher. The installer keeps Gatekeeper and download quarantine in place.

Bragi is free to use under the [HiVEGrid Free Binary Use License](LICENSE.md). Commercial redistribution or sale requires separate permission; source remains reserved. This is not an OSI open-source release. Model and runtime terms are independent; see [third-party notices](THIRD_PARTY_NOTICES.md) and [license status](LICENSE_STATUS.md).

## Deutsch — kurz

Bragi 0.1.6 bietet lokale Sprachsynthese für Apple Silicon ab macOS 26.2: Text markieren → **Dienste → Bragi TTS**, Steuerung über Menü oder F7/F8/F9, **Stopp/Leeren** und umschaltbare EN/DE-Oberfläche. Neun Presets sowie je ein männliches/weibliches Profil für sieben europäische Sprachen; eigene WAV mit exaktem Transkript und den nötigen Nutzungsrechten importierbar. **Privacy by Design:** Synthese lokal, erzeugtes Audio nur im Speicher, Verlauf nur während der aktiven Warteschlange; eigene Stimmprofile bleiben bis zur Profillöschung gespeichert. Nach Modelldownload funktioniert Synthese offline. Betriebssystem- und Ursprungsdaten sind von der Löschzusage ausgenommen.

ZIP und Prüfsumme unter **Releases** laden, prüfen, vollständig entpacken und `Install_Mac.command` starten. Die installierte Release-Fassung wurde am **24. Oktober 2026 als voll funktionsfähig bestätigt**. Kostenlose Binärnutzung, kommerzieller Vertrieb nur mit Erlaubnis, Quellcode vorbehalten. **AJA Voice: Lizenzfreigabe von ElevenLabs ausstehend.**
