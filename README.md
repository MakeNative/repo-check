# repo-check

Claude-Code-Skill von MakeNative: prüft fremde GitHub-Repos auf Köder-Merkmale, bevor Claude Dateien daraus lädt. Braucht die GitHub-CLI `gh` (angemeldet mit `gh auth login`) und `jq`.

## Installation

In Claude Code:

```
/plugin marketplace add MakeNative/repo-check
/plugin install repo-check@repo-check
```

Danach Claude Code einmal neu starten.

## `/repo-check:repo-check` – fremde Repos prüfen, bevor etwas geladen wird

Auf GitHub liegen Kopien echter Projekte, deren README auf eine ZIP mit vermutlicher
Schadsoftware zeigt. Wer Repos von Agenten durchsuchen lässt, stößt früher oder später
darauf. Der Skill schaut deshalb zuerst nur auf Dateibaum und Kontodaten und lädt
dabei keine einzige Datei.

```
/repo-check:repo-check owner/repo owner/anderes-repo
```

| Ergebnis | Bedeutung | Danach |
|---|---|---|
| `OK` | keine Köder-Merkmale | Dateien dürfen als Text geladen werden |
| `VERDÄCHTIG` | Archiv oder Installer im Repo, oder junges Konto mit wenigen Repos und ein älteres Repo gleichen Namens | nichts laden, nicht empfehlen, von Hand ansehen |
| `FEHLER` | nicht vollständig geprüft | behandeln wie `VERDÄCHTIG` |

Auch seriöse Projekte enthalten manchmal Binärdateien, ein Treffer ist also ein Grund
zum Hinsehen und kein Urteil. Umgekehrt kommt ein Köder durch, der nur auf eine externe
Seite verlinkt. Fremde Dateien bleiben deshalb in jedem Fall Text und werden nie ausgeführt.

## MakeNative

Dieses Plugin ist Teil von [MakeNative](https://makenative.de). Wir arbeiten jeden Tag mit
Agenten-Pipelines und bringen anderen bei, sie für ihre eigenen Prozesse zu
bauen. Für Entwickler genauso wie für alle, die ihre Arbeit mit KI automatisieren wollen.

Du willst das für deine Arbeit lernen? Trag dich in die Liste ein:
[Bewerbung Starter-Kohorte](https://tally.so/r/5ByYj6?utm_source=github&utm_medium=readme&utm_campaign=starter-kohorte)

Christian Eichmüller · [LinkedIn](https://linkedin.com/in/christianeichmueller)

## Lizenz

MIT
