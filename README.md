# openstreetbike
kleine ETL-Pipeline, Daten sollen bereinigt, transformiert und in relationale Datenbank gespeichert werden. Prozess wird automatisiert.

# Übungsaufgabe Work in Progress

## 🛠️ Projekt: "OpenStreetBike – Fahrradstationsdaten verarbeiten"
### 🧠 Ziel:
Baue eine kleine ETL-Pipeline, die öffentlich verfügbare Daten von Fahrradverleihstationen (z. B. aus einer europäischen Stadt wie Oslo, Paris oder Köln) regelmäßig verarbeitet. Die Daten sollen bereinigt, transformiert und in eine relationale Datenbank gespeichert werden. Zusätzlich wird der Prozess automatisiert.

### 📦 Datensatz-Vorschlag
Open-Data-Datensatz Vorschlag:

Name: Oslo City Bike – Station status

Zugriff: Echtzeitdaten via REST-API (JSON)

Daten: Verfügbare Fahrräder, Dockingstations, Kapazitäten etc.

Alternativ: Stadt Köln – Open Data Fahrradverleihstationen

Vorteil: Echtzeitdaten (perfekt für Übung mit Airflow), aber überschaubar in der Größe.

### 🧩 Aufgabenstellung (für 1 Woche / ca. 4 h pro Tag)
Tag 1 – Setup & Exploration
- API/CSV-Datenquelle verstehen: Strukturen, Formate, Datenmengen

- Beispiel-Request oder CSV-Datei laden, ersten Überblick verschaffen

- SQLite oder PostgreSQL lokal aufsetzen

- Python-Umgebung vorbereiten (venv, requirements.txt mit requests, pandas, sqlalchemy etc.)

Tag 2 – Extract & Load
- Daten abrufen (API oder CSV)

- In einen DataFrame laden

- Tabellenstruktur für deine Zieldatenbank entwerfen (z. B. stations, status_logs)

- Ladefunktion schreiben, um die Daten per SQLAlchemy in die DB zu schreiben

Tag 3 – Transform
- Daten bereinigen:

  - Fehlende Werte behandeln

  - Datentypen prüfen und ggf. umwandeln

  - Zeitformate vereinheitlichen

- Transformation:

  - Neue Spalten ableiten (z. B. Auslastung = bikes_available / capacity)

  - Daten normalisieren (z. B. separate Tabellen für statische vs. dynamische Infos)

Tag 4 – Automatisierung mit Prefect oder Airflow
- Workflow-Definition: Extract → Transform → Load

- Täglicher oder stündlicher Ablauf

- Logging & einfache Fehlerbehandlung integrieren

- Lokales Testen mit Prefect Orion oder Airflow im Docker-Setup

Tag 5 – Erweiterungen & Tests
- Unit Tests für Transformationsfunktionen (z. B. mit pytest)

- Parametrisierung (z. B. API-Keys, Pfade, DB-Verbindung) über .env + dotenv

- Logging verbessern (logging-Modul)

Tag 6 – Visualisierung / Abfragen
- Beispielhafte SQL-Abfragen:

  - Stationen mit höchster Auslastung

  - Durchschnittliche Auslastung pro Tag

  - Optionale Mini-Visualisierung mit matplotlib oder streamlit (wenn’s Spaß macht)

Tag 7 – Dokumentation & Refactoring
Projektstruktur aufräumen (src/, etl/, data/ etc.)

README schreiben:

Projektbeschreibung

Setup-Anleitung

Beispielabfragen

Dockerfile (optional) zur Containerisierung

📁 Projektstruktur (Vorschlag)
bash
Kopieren
Bearbeiten
bike_etl_project/
│
├── data/                 # Rohdaten oder Beispiel-Downloads
├── etl/
│   ├── extract.py
│   ├── transform.py
│   ├── load.py
│   └── pipeline.py       # Hauptpipeline
│
├── dags/                 # Falls du Airflow nutzt
├── tests/                # Pytest-Tests
├── .env
├── requirements.txt
├── README.md
└── run_pipeline.py       # Für manuelle Ausführung
🔧 Tools & Libraries
Python (pandas, requests, sqlalchemy, dotenv, logging, pytest)

Datenbank: SQLite für den Anfang, PostgreSQL optional

Workflow: Prefect (einfacher Einstieg) oder Airflow (Enterprise-ready)

Bonus: streamlit für Mini-Dashboards, docker für Packaging
