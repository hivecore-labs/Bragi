# Installation — AJA Bragi 0.1.6

## English

### Requirements

- An **Apple Silicon Mac** (arm64).
- **macOS 26.2 or later**.
- Internet access for the initial pinned model download.
- Permission to install the app in `/Applications`.
- Several GB of free disk space for separately downloaded models, plus room for the existing app and a staged replacement during installation. There is no single guaranteed threshold for every model/cache state.

The supplied signet is embedded as the app icon and is installed automatically with the app.

The application package includes Python and its runtime libraries. Homebrew and Xcode are not required to install the release. The installer does not automatically request `sudo` privileges.

The release bundles no reference WAVs. A fresh installation uses the Ryan preset and downloads its pinned CustomVoice model during setup. User-imported voices use the separately downloadable Base model. The explicit model-download action can fetch both. Existing custom profiles remain local and private.

### 1. Download and verify

In the repository's **Releases** section, download both assets to the same directory:

- `AJA-Bragi-0.1.6-arm64.zip`
- `AJA-Bragi-0.1.6-arm64.zip.sha256`

Open Terminal in that directory and run:

```bash
shasum -a 256 -c AJA-Bragi-0.1.6-arm64.zip.sha256
```

Expected result: `AJA-Bragi-0.1.6-arm64.zip: OK`.

A checksum detects file changes; a checksum obtained from the same source does not independently authenticate the publisher.

### 2. Extract the complete package

Double-click the ZIP. The extracted folder contains:

```text
AJA-Bragi-0.1.6-arm64/
├── AJA Bragi.app
├── Install_Mac.command
├── README.txt
├── INSTALLATION.txt
├── LICENSE_STATUS.txt
├── BUILD_INFO.json
└── SHA256SUMS
```

Keep the app and installer together. Optionally, open Terminal in this extracted folder and check the listed package files:

```bash
shasum -a 256 -c SHA256SUMS
```

### 3. Run the installer

Double-click `Install_Mac.command`. Alternatively, open Terminal in the extracted folder and run:

```bash
bash ./Install_Mac.command
```

The installer performs a light preflight check, copies and verifies the app, installs it in `/Applications`, loads the pinned model, plays one short welcome message, and registers **Bragi TTS** in macOS Services.

The welcome is spoken in German when the primary language under **System Settings → General → Language & Region** is German. All other primary languages use English. English is also the fallback if the preference cannot be read. Console messages remain in English.

### 4. Review macOS approvals

The Community package is ad-hoc signed and not Apple notarized. If macOS blocks a Bragi component after a launch attempt:

1. Open **System Settings → Privacy & Security**.
2. Review the message for the specifically named Bragi component.
3. If you trust the release, choose **Open Anyway** and confirm the system dialog.
4. Run the installer again.

If the warning names the app, opening `AJA Bragi.app` in Finder may be necessary before approval becomes available. Opening the app without selected text does not itself run setup.

For F7/F8/F9, grant the permissions requested by macOS for the Bragi media helper under **Accessibility** and, where requested, **Input Monitoring**. These permissions are separate from Open Anyway and may be requested on first reading.

The installer does not remove quarantine or disable system-wide security checks. A preflight check cannot pre-approve every later helper permission. Managed Macs may have additional restrictions.

### 5. Start reading and assign a shortcut

Select text in a compatible app and choose **right-click → Services → Bragi TTS**. Use F7/F8/F9 for previous section, pause/resume and next section. Depending on keyboard settings, also hold Fn.

For the best experience:

1. Open **System Settings → Keyboard → Keyboard Shortcuts → Services**.
2. Find **Bragi TTS**.
3. Enable it if necessary and assign an available keyboard shortcut.

### Troubleshooting

- **No Open Anyway entry:** it appears only when macOS reports an applicable security block. A model, audio or Services registration error needs its own correction; read the actual Terminal message.
- **The service is missing:** reopen the app you are reading from, then check Keyboard Shortcuts → Services. Run the installer again if setup did not finish.
- **Model is missing:** run the installer again with Internet access. Normal reading intentionally does not download a replacement model.
- **Media keys do not respond:** check the current Bragi Menu.app Accessibility entry and your Fn-key setting. If the switch is already enabled but prompts repeat after an update, use the renewal steps below. Review Input Monitoring only if macOS specifically requests it.
- **No space left on device:** free sufficient space, then run the installer again. Its staged replacement temporarily needs room alongside the existing application; model downloads need additional space. Open Anyway does not correct a storage failure.
- **Copying to `/Applications` fails with a permissions error:** use an account permitted to install there or contact the Mac administrator.
- **Checksum mismatch:** obtain a fresh package and checksum from the trusted release source before continuing.

### Accessibility enabled but prompts repeat or media keys fail

An ad-hoc signed update can change the code identity stored with a macOS permission. The old entry may still look enabled while macOS rejects the installed build. Renew the menu application's entry using the steps below if it no longer matches the installed build.

1. Finish or clear the active reading, then choose **Quit menu** in Bragi.
2. Open **System Settings → Privacy & Security → Accessibility**.
3. Select only the stale **Bragi Menu.app** entry and remove it with **−**.
4. Choose **+**, press **Command–Shift–G**, and enter the installed path:

   ```text
   /Applications/AJA Bragi.app/Contents/Helpers/Bragi Menu.app
   ```

5. Confirm the selection with **Open**, enable its switch, and authenticate with macOS if requested.
6. Open **AJA Bragi** in Applications, start a reading, and test F7/F8/F9 while the queue is active.

Grant access only to the named installed application that you trust. Leave unrelated applications and permissions unchanged. If macOS explicitly requests **Input Monitoring**, review that separate request. A binary update may require a renewed grant.

A technical audio-test success does not assess subjective pronunciation. The previous app is restored if replacement fails; a later model/audio setup failure does not roll back the entire installation.

---

## Menu bar, voices and playback — 0.1.6

Start reading with **Services → Bragi TTS**, or open **AJA Bragi** in Applications. The transparent Bragi signet opens a compact HiVEGrid panel. Its interface starts in English; **EN / DE** switches the entire interface between English and German and saves the choice.

- **Playback:** live loading/generation/playback/pause/error status, active voice and queued sections.
- **Previous / Pause or Resume / Next:** operate on the same queue as Services and F7/F8/F9.
- **Stop & Clear Queue:** stops the current section, removes pending sections and releases pause. A fresh selection starts normally.
- **Voices:** nine Qwen presets, local custom WAV profiles. Voice changes apply to the next section, preserving the running section.
- **Preview voice:** appends a short sample to the existing queue.
- **Download / check voice models:** explicitly downloads the pinned Base and CustomVoice models. The first download requires several GB. Selection, import, polling and ordinary reading do not download models.

The presets are Ryan, Aiden, Vivian, Serena, Uncle Fu, Dylan, Eric, Ono Anna and Sohee. They support German and English; their native languages and accents differ. The pinned CustomVoice checkpoint is published under Apache-2.0: [MLX model card](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-CustomVoice-8bit), [upstream voice descriptions](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice).

To add a custom voice, choose **Add a reference WAV**, a name, its exact transcript and recording language (German or English). Use a clear **3–30 second PCM WAV, 16/24/32-bit, 16–96 kHz, mono/stereo, up to 32 MB**. Confirm that you may use the recording and voice as an AI reference. **Save & use** makes a private local copy and selects it; there is no training step or upload. A profile can speak both supported output languages. Import another profile if you want to retain a second recording/transcript.

Profiles are stored privately in `~/Library/Application Support/AJA Bragi`. To delete a custom profile, first select another voice and use the trash button in the custom profile list. Closing or quitting the menu leaves reading independent. Polling does not extend the speech engine's idle timer. If a required model is absent, the current section is retained and the queue pauses; download it, then resume.

Ryan is the default preset. Setup works without a custom reference WAV. **AJA Voice: awaiting licensing approval from ElevenLabs.**

## Services and menu icon

**Services → Bragi TTS** starts the native menu provider when needed. Speech and queue processing continue independently. Click the transparent signet for playback and voice controls; closing the panel keeps the icon, while **Quit menu** closes the menu. If Services or its shortcut is missing, run setup, check Keyboard Shortcuts → Services and reopen the calling app.

## European language profiles

Nine Qwen presets are available. Fourteen language profiles provide one **Male / Ryan** and one **Female / Serena** option for each of **German, English, French, Spanish, Italian, Portuguese and Russian**. These profiles explicitly select the output language. They reuse the model's multilingual timbres; they are not fourteen newly recorded or native-speaker voices. Accents may vary. **Preview voice** speaks a short sample in the chosen profile's language. The interface still switches separately with EN / DE. Choose the language of your text; Bragi reads it aloud and does not translate it. German number/date preparation applies only when the selected output language is German.

## Reading privacy and session cleanup

Reading privacy: Previous is available within an active reading queue only. When the complete queue finishes, Bragi clears its reading history and terminates/reaps the speech process, releasing its text, generated audio and model state. Stop & Clear Queue cancels the current section and discards the queued text and history. Bragi does not save selected reading text or generated speech to files; diagnostic logs contain fixed technical events, not worker message bodies. A missing voice model can leave unplayed text explicitly paused for download/resume; Clear discards it. Intentionally imported reference WAVs and their transcripts remain saved voice settings until you delete the profile.

The next reading reloads its model from the local cache, so its first audio can take longer. This is application-level lifecycle cleanup, not a guarantee of forensic erasure from macOS memory, swap, OS audio buffers, backups or the originating application/clipboard. When updating an already running older build, end the old Bragi background process before testing the new app.

## Deutsch — Kurzanleitung

**Voraussetzungen:** Apple Silicon, macOS 26.2 oder neuer und Internet für den ersten Modelldownload.

1. Unter **Releases** das ZIP und seine `.sha256` herunterladen. Im Download-Ordner prüfen:

   ```bash
   shasum -a 256 -c AJA-Bragi-0.1.6-arm64.zip.sha256
   ```

2. ZIP vollständig entpacken. App und Installer zusammen im Ordner lassen.
3. `Install_Mac.command` doppelklicken oder im entpackten Ordner starten:

   ```bash
   bash ./Install_Mac.command
   ```

4. Falls macOS Bragi ausdrücklich blockiert: **Systemeinstellungen → Datenschutz & Sicherheit → Dennoch öffnen** für die genannte Komponente prüfen. Für die Medientasten gegebenenfalls Bedienungshilfen und Eingabeüberwachung freigeben.
5. Text markieren → **Dienste → Bragi TTS**. Einen Tastaturkurzbefehl unter **Tastatur → Tastaturkurzbefehle → Dienste** einrichten.

**Bei wiederholter Bedienungshilfen-Abfrage trotz eingeschaltetem Bragi-Schalter:** Vorlesen beenden, Bragi-Menü schließen, unter Datenschutz & Sicherheit → Bedienungshilfen nur den alten Bragi-Menu-Eintrag entfernen und über **+**, **⌘⇧G** die aktuelle `/Applications/AJA Bragi.app/Contents/Helpers/Bragi Menu.app` hinzufügen und aktivieren. Danach Bragi öffnen und während des Vorlesens testen. Bei „No space left on device“ zunächst Speicher freigeben; die Installation braucht Platz für eine zusätzliche App-Kopie und die Modelle.

Die installierte Release-Fassung wurde am **24. Oktober 2026 als voll funktionsfähig bestätigt**.

**F7:** zurück · **F8:** Pause/Fortsetzen · **F9:** weiter; gegebenenfalls zusätzlich Fn. Die Begrüßung ist bei deutscher primärer Systemsprache Deutsch, sonst Englisch. Die geschriebenen Installationsmeldungen bleiben Englisch.

Der native Dienst startet das Bragi-Menüsymbol bei Bedarf selbst. Unter **Tastaturkurzbefehle → Dienste** kann ein Kurzbefehl für Bragi TTS zugewiesen werden.

Neun Qwen-Presets stehen zur Verfügung. Deutsch, Englisch, Französisch, Spanisch, Italienisch, Portugiesisch und Russisch erhalten je ein männliches Ryan- und weibliches Serena-Profil. Diese mehrsprachigen Profile stellen die Ausgabesprache fest ein; sie sind keine neuen muttersprachlichen Aufnahmen. Akzente können variieren. Die Vorschau folgt der gewählten Sprachoption; es findet keine Übersetzung statt.

Datenschutz beim Vorlesen: Zurück funktioniert nur innerhalb der aktiven Warteschlange. Nach deren vollständigem Ende löscht Bragi den Vorleseverlauf und beendet den Sprachprozess samt Text-, Audio- und Modellzustand. Stop & Clear Queue verwirft den laufenden Text, die Warteschlange und den Verlauf. Vorgelesene Texte und erzeugtes Audio werden nicht als Dateien gespeichert; Logs übernehmen keine Worker-Meldungstexte. Fehlt ein Modell, bleibt noch nicht vorgelesener Text ausdrücklich pausiert zum Fortsetzen erhalten; Clear verwirft ihn. Bewusst importierte Referenz-WAVs und ihre Transkripte bleiben als Stimmeinstellung bis zum Löschen des Profils gespeichert.

Beim nächsten Vorlesen wird das lokale Modell erneut geladen. Eine forensische Löschung aus macOS-Speicher, Swap, Betriebssystem-Audiopuffern, Backups oder der ursprünglichen App/Zwischenablage wird nicht zugesichert. Vor dem Test eines Updates einen noch laufenden alten Bragi-Hintergrundprozess beenden.
