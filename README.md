# Zentrale SQL Kontaktdatenbank

Dieses Projekt baut eine zentrale, lokal gehostete Kontaktdatenbank auf einem **Synology NAS** auf.  
Kontakte aus verschiedenen Quellen werden importiert, normalisiert, dedupliziert und dauerhaft in einer PostgreSQL-Datenbank gespeichert.

---

## Motivation

Kontakte verteilen sich über viele Systeme: LinkedIn, Apple Kontakte, Excel-Listen, Google, Xing.  
Ziel ist eine **einzige, saubere Datenbank** als "Source of Truth" — lokal, privat, unter eigener Kontrolle.

---

## Unterstützte Import-Quellen

| Quelle | Format | Status |
|---|---|---|
| Excel / CSV-Listen | `.xlsx`, `.csv` | 🔲 Geplant |
| Apple Kontakte | `.vcf` (vCard 3.0/4.0) | 🔲 Geplant |
| LinkedIn | `Connections.csv` | 🔲 Geplant |
| Xing | CSV-Export | 🔲 Geplant |
| Google Kontakte | CSV / vCard | 🔲 Geplant |

---

## Technologie-Stack

| Komponente | Technologie |
|---|---|
| Datenbank | PostgreSQL 15 (Docker) |
| Web-UI | Adminer |
| Container-Host | Synology NAS (Container Station) |
| Import-Tool | Python 3.11+ |

---

## Projektstruktur

```
ZentraleSQLKontaktdatenbank/
├── architektur/           ← Technische Dokumentation (Mermaid-Diagramme)
│   ├── README.md
│   ├── 00_systemuebersicht.md
│   ├── 01_datenbankschema.md
│   ├── 02_import_pipelines.md
│   └── 03_deployment_nas.md
├── docker/                ← Docker Compose & .env für NAS-Deployment
├── schema/                ← SQL Init-Skripte
├── importer/              ← Python Import-Tool
└── README.md              ← Diese Datei
```

---

## Schnellstart

> Detaillierte Anleitungen sind in den [Architekturdokumenten](./architektur/README.md) zu finden.

### 1. NAS-Datenbank starten

```bash
cd docker/
cp .env.template .env      # Passwort setzen
docker compose up -d
```

Adminer Web-UI erreichbar unter: `http://<NAS-IP>:8088`

### 2. Kontakte importieren

```bash
cd importer/
pip install -r requirements.txt

# Excel importieren
python main.py --source excel --file "kontakte.xlsx"

# Apple vCard importieren
python main.py --source vcard --file "Kontakte.vcf"

# LinkedIn importieren
python main.py --source linkedin --file "Connections.csv"
```

---

## Dokumentation

| Dokument | Inhalt |
|---|---|
| [Systemübersicht](./architektur/00_systemuebersicht.md) | Gesamtarchitektur, Komponenten, Entscheidungen |
| [Datenbankschema](./architektur/01_datenbankschema.md) | ER-Diagramm, Tabellen, Indizes, Views |
| [Import-Pipelines](./architektur/02_import_pipelines.md) | Datenfluss, Spalten-Mappings, CLI |
| [NAS-Deployment](./architektur/03_deployment_nas.md) | Docker Setup, Netzwerk, Backup |

---

## Status

🚧 **In Entwicklung** — Architekturphase abgeschlossen, Implementierung ausstehend.
