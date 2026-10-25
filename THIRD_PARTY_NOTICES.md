# Third-party components and models

Applies to **AJA Bragi 0.1.6 Community**.

## English

The HiVEGrid binary-use license covers HiVEGrid first-party material. It does not replace or restrict independent third-party licenses.

The app includes Python and runtime libraries including MLX/mlx-audio, NumPy, SciPy, Hugging Face Hub, Transformers, tokenizers, safetensors, sounddevice and their bundled dependencies. Their supplied license files, copyright notices and distribution metadata are retained in the app's `Contents/Resources` and `Contents/Frameworks` trees. Native wheels can include their own `licenses/` directories and CycloneDX SBOMs. `SBOM.cdx.json` lists component identities and declared license information; `DEPENDENCY_REVIEW.json` documents advisory coverage and limits. Python's PSF terms, NumPy/SciPy notices, PyInstaller's bootloader exception and other third-party terms continue to apply to their corresponding material.

Model weights are not bundled in this ZIP. Explicit setup/download actions obtain pinned upstream snapshots:

- CustomVoice presets: [mlx-community/Qwen3-TTS-12Hz-1.7B-CustomVoice-8bit](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-CustomVoice-8bit/tree/main), revision `41d3337e8b7f2843a75841595fc14e4b9a7a4b96`, Apache-2.0; [upstream Qwen model](https://huggingface.co/Qwen/Qwen3-TTS-12Hz-1.7B-CustomVoice/tree/main).
- User-reference model: [mlx-community/Qwen3-TTS-12Hz-1.7B-Base-8bit](https://huggingface.co/mlx-community/Qwen3-TTS-12Hz-1.7B-Base-8bit), revision `e7dd0585652209fa0d7783659aad4e8a324de11c`, Apache-2.0; [upstream Qwen project](https://github.com/QwenLM/Qwen3-TTS).

See the upstream model cards and [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) for model terms. A license on model weights is not a blanket clearance of personality, recording or other third-party rights. Imported recordings remain the user's responsibility.

Apple AppKit/SwiftUI and system libraries are supplied and maintained by macOS, not redistributed in the ZIP.

## Deutsch — kurz

Fremdkomponenten und separat geladene Modelle behalten ihre eigenen Lizenzen. Die zugehörigen Hinweise bleiben in der App erhalten; SBOM und Abhängigkeitsbericht liegen im Paket. Die HiVEGrid-Lizenz schränkt unabhängig bestehende Rechte aus Fremdlizenzen nicht ein. Apple-Systembibliotheken werden nicht mitgeliefert.
