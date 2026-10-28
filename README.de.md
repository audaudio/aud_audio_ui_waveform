# aud_audio_ui_waveform

[English](README.md) | Deutsch

[![CI](https://github.com/audaudio/aud_audio_ui_waveform/actions/workflows/quick_check.yaml/badge.svg)](https://github.com/audaudio/aud_audio_ui_waveform/actions/workflows/quick_check.yaml)

Wellenform-Ansicht der Audanika Audio Engine, nach dem Vorbild von AudioKit
Waveform. Reines Flutter, frei von der Engine; Teil der Audanika Audio Engine,
geplant in [aud_audio_pm](https://github.com/audaudio/aud_audio_pm).

## Motivation

- Sampler und Recorder auf der Audanika Audio Engine müssen Audiodateien und
  Auswahlen darin anzeigen, auf jeder Plattform, die Flutter unterstützt
- AudioKit Waveform zeigt einen bewährten, MIT-lizenzierten Weg, lange Dateien
  schnell zu zeichnen: Spitzenwerte abseits des UI-Threads berechnet und je
  Auflösung gecacht; das Paket portiert ihn, statt Neues zu erfinden
- Die Ansicht zeichnet ein Dart-Modell und hängt nicht von der Engine ab
  (Entscheidung ui-003), sodass sie ohne Oberfläche testbar ist und in einer
  App, einem Plugin-Editor und einem Test gleichermaßen arbeitet

## Installation

Das Paket ist nicht auf pub.dev veröffentlicht; binde es über seine Git-Tags
ein:

```yaml
dependencies:
  aud_audio_ui_waveform:
    git:
      url: git@github.com:audaudio/aud_audio_ui_waveform.git
      tag_pattern: '{{version}}'
    version: ^0.0.3
```

## Verwendung

Das Paket ist ein Platzhalter: Das Widget folgt mit Schritt S27 des Plans der
Audanika Audio Engine (siehe [Stand](#stand)). Bis dahin exportiert es nur den
Boilerplate-Code der Flutter-Paketvorlage, mehr läuft also nicht:

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

## Grenzen

- Noch kein Widget; siehe [Stand](#stand)
- Das Widget wird nicht von der Engine abhängen (Entscheidung ui-003): Apps
  binden es über `aud_audio_ui_bindings`, Plugin-Editoren über das Protokoll
  ihrer Shell

## Dokumentation

- [Plan 17: Audanika Audio
  Engine](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/tickets/2026-10-07-17-audanika-audio-engine.md),
  der das Paket als Schritt S27 plant
- Die Entscheidungen
  [ui-001](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/concepts/decisions/ui-001.md)
  (UI-Pakete sind Flutter-Widgets über Dart-Modellen) und
  [ui-003](https://github.com/audaudio/aud_audio_pm/blob/main/doc/2026-Q4/concepts/decisions/ui-003.md)
  (die Engine-Adapter liegen in einem Binding-Paket)
- [AudioKit Waveform](https://github.com/AudioKit/Waveform), die Vorlage (MIT)
- Die Guides in [`doc/guides`](doc/guides) und die Blog-Posts in
  [`doc/blog`](doc/blog)

## Stand

Vor 1.0 — die API kann sich zwischen Minor-Versionen ändern. Das Repo enthält
nur den Boilerplate-Code eines Flutter-Pakets und seine Versionskonstante.
Schritt S27 baut eine Wellenform-Ansicht mit in einem Isolate berechneten
Spitzenwerten, einem Cache in mehreren Auflösungen, Zoom und Auswahl,
gezeichnet mit einem CustomPainter oder Fragment-Shadern, über einem Modell
nach AudioKit Waveform und den Audiodateien von `aud_audio_file`. Dafür hängt
das Paket von `aud_audio` and `aud_audio_file` ab.

## Mitwirken

Tickets laufen durch den `gg`-Workflow: siehe den [Develop
Guide](doc/guides/develop-guide.md) und den [Review
Guide](doc/guides/for-ai/ai-review-guide.md).

## Lizenz

MIT — siehe [LICENSE](LICENSE).
