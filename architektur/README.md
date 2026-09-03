# Architektur-Dokumentation

Dieses Verzeichnis enthält alle Architekturentscheidungen und technischen Designs für die **Zentrale SQL Kontaktdatenbank**.

## Dokumente

| Datei | Inhalt | Status |
|---|---|---|
| [00_systemuebersicht.md](./00_systemuebersicht.md) | Gesamtüberblick, Komponenten, Technologieentscheidungen | ✅ |
| [01_datenbankschema.md](./01_datenbankschema.md) | ER-Diagramm, Tabellen, Spalten, Relationen | ✅ |
| [02_import_pipelines.md](./02_import_pipelines.md) | Datenfluss pro Quelle (Excel, vCard, LinkedIn) | ✅ |
| [03_deployment_nas.md](./03_deployment_nas.md) | Docker Setup auf Synology NAS, Netzwerk, Volumes | ✅ |
| [04_deduplizierung.md](./04_deduplizierung.md) | Logik zur Duplikatserkennung und -bereinigung | 🔲 |
| [05_erweiterungen.md](./05_erweiterungen.md) | Geplante weitere Quellen (Xing, Google, Apple Mail) | 🔲 |

## Konventionen

- Diagramme werden als **Mermaid**-Blöcke eingebettet (rendert in VS Code, GitHub, Obsidian)
- Jede Architekturentscheidung wird mit einer **ADR** (Architecture Decision Record) begründet
- Status-Icons: ✅ Fertig · 🔄 In Arbeit · 🔲 Geplant
