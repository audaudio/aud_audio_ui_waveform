# aud_audio_ui_waveform

English | [Deutsch](README.de.md)

[![CI](https://github.com/audaudio/aud_audio_ui_waveform/actions/workflows/quick_check.yaml/badge.svg)](https://github.com/audaudio/aud_audio_ui_waveform/actions/workflows/quick_check.yaml)

Waveform view of the Audanika Audio Engine, modeled on AudioKit Waveform. Pure
Flutter, free of the engine; part of the Audanika Audio Engine, planned in
[aud_audio_pm](https://github.com/audaudio/aud_audio_pm).

## Motivation

- Samplers and recorders built on the Audanika Audio Engine need to show audio
  files and selections in them, on every platform Flutter supports
- AudioKit Waveform shows a proven, MIT-licensed way to draw long files fast:
  peaks computed off the UI thread and cached per resolution; the package
  ports it instead of inventing a new one
- The view renders a Dart model and does not depend on the engine (decision
  ui-003), so it tests headless and works in an app, a plugin editor and a
  test alike

## Installation

The package is not published to pub.dev; add it from its git tags:

```yaml
dependencies:
  aud_audio_ui_waveform:
    git:
      url: git@github.com:audaudio/aud_audio_ui_waveform.git
      tag_pattern: '{{version}}'
    version: ^0.0.3
```

## Usage

The package is a placeholder: the widget follows with step S27 of the plan of
the Audanika Audio Engine (see [Status](#status)). Until then it exports
nothing but the boilerplate of the Flutter package template, so this is all
that runs:

```dart
import 'package:aud_audio_ui_waveform/aud_audio_ui_waveform.dart';

void main() {
  // The widget is not built yet; the package exports the boilerplate
  // Calculator of the Flutter package template until it arrives.
  print(Calculator().addOne(1));
}
```

```text
2
```

## Limitations

- No widget yet; see [Status](#status)
- The widget will not depend on the engine (decision ui-003): apps bind it
  through `aud_audio_ui_bindings`, plugin editors through their shell's
  protocol

## Documentation

- [Plan 17: Audanika Audio
  Engine](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/tickets/2026-10-07-17-audanika-audio-engine.md),
  which plans the package as step S27
- The decisions
  [ui-001](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/concepts/decisions/ui-001.md)
  (UI packages are Flutter widgets over Dart models) and
  [ui-003](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/concepts/decisions/ui-003.md)
  (the engine adapters live in a binding package)
- [AudioKit Waveform](https://github.com/AudioKit/Waveform), the template
  (MIT)
- The guides in [`doc/guides`](doc/guides) and the blog posts in
  [`doc/blog`](doc/blog)

## Status

Before 1.0 — the API may change between minor versions. The repo holds the
boilerplate of a Flutter package and its version constant only. Step S27
builds a waveform view with peaks computed in an isolate, a multi-resolution
cache, zoom and selection, rendered with a CustomPainter or fragment shaders,
over a model after AudioKit Waveform and the audio files of `aud_audio_file`.
The package depends on `aud_audio` and `aud_audio_file` for that.

## Contributing

Tickets run through the `gg` workflow: see the [Develop
Guide](doc/guides/develop-guide.md) and the [Review
Guide](doc/guides/for-ai/ai-review-guide.md).

## License

MIT — see [LICENSE](LICENSE).
