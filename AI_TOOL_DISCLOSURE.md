# Erklärung zur Nutzung von KI-Werkzeugen im Machine-Learning-Projekt

Dieses Dokument beschreibt den Einsatz von KI-basierten Werkzeugen im Rahmen des Machine-Learning-Projekts. Die Gliederung folgt dem **QUA³CK - Prozessmodell**, um transparent darzustellen, in welcher Phase des Projekts welche Werkzeuge zu welchem Zweck verwendet wurden.

Das QUA³CK - Modell ist ein iterativer Prozess für die Entwicklung von ML-Lösungen und steht für:
- **Q** - Question
- **U** - Understanding
- **A** - Algorithm Selection
- **A** - data Adaption
- **A** - parameter Adjustment
- **C** - Conclusion & Comparison
- **K** - Knowledge Transfer

Alle durch KI-Systeme generierten Ergebnisse (z.B. Code, Analysen, Texte) wurden von mir als verantwortlichem Entwickler kritisch geprüft, validiert und angepasst. Die finale Verantwortung für das Projekt liegt vollständig bei mir.

## Detaillierte Aufschlüsselung der Werkzeugnutzung nach Phase

| Phase (QUA³CK) | KI-Tool (Version) | Zweck | Beispielhafter Prompt / Anwendungsfall |
| :--- | :--- | :--- | :--- |
| **Q** - Question | Perplexity (Claude 3.5 Sonnet), Google Gemini 1.5 Pro | Recherche Datensätze, Konzept | "Finde aktuelle öffentliche Datensätze (CC-Lizenz) zum Thema 'Telco Customer Churn'. Liste Features und Zielvariablen auf." |
| **U** - Understanding | GitHub Copilot (GPT-4o), OpenAI GPT-4o | Explorative Datenanalyse (EDA) | "Erstelle ein Python-Skript mit `pandas` und `seaborn`, das die Verteilung der Zielvariable visualisiert und eine Korrelationsmatrix der numerischen Features plottet." |
| **A** - Algorithm Selection | OpenAI o1-preview, Google Gemini 1.5 Pro | Algorithmenauswahl | "Vergleiche `XGBoost`, `LightGBM` und `scikit-learn` RandomForest für tabuläre Daten. Erstelle eine Tabelle zu Trainingszeit und Interpretierbarkeit." |
| **A** - data Adaption | Cursor (Claude 3.5 Sonnet), GitHub Copilot Workspace | `scikit-learn` Preprocessing | "Implementiere eine `scikit-learn` Pipeline mit `ColumnTransformer`. Nutze `OneHotEncoder` für kategorische und `StandardScaler` für numerische Spalten." |
| **A** - parameter Adjustment | GitHub Copilot (GPT-4o) | `mlflow` & `scikit-learn` Integration | "Refactor `train.py`: Füge `mlflow.sklearn.autolog()` hinzu und logge benutzerdefinierte Metriken (F1-Score, AUC) für das Testset." |
| **C** - Conclusion & **C**omparison | OpenAI GPT-4o | Analyse von `mlflow`-Daten | "Schreibe ein Skript, das via `mlflow.search_runs()` Experimente lädt und mit `plotly` einen Scatter-Plot (Accuracy vs. Latency) erstellt." |
| **K** - Knowledge **T**ransfer | Cursor (Claude 3.5 Sonnet), OpenAI GPT-4o | `streamlit`-Dashboard | "Generiere eine `streamlit`-App: Lade das Modell via `mlflow`, erstelle Input-Regler für Features und visualisiere die Prediction mit einem `plotly` Gauge-Chart." |
| **K** - Knowledge **T**ransfer | DeepL Write, OpenAI GPT-4o | Dokumentation, Übersetzung | "Formuliere eine Zusammenfassung der Ergebnisse für die `README.md`. Übersetze die technischen Kommentare im Code ins Englische." |

## Verwendete Datensätze

Im Rahmen des Projekts wurden folgende öffentlich zugängliche Datensätze verwendet:

| Datensatz | Quelle | Beschreibung | Verwendungszweck |
| :--- | :--- | :--- | :--- |
| **Telco Customer Churn** | Kaggle / IBM Sample Data Sets | Datensatz mit 7043 Kunden, inkl. Demografie, Services und Churn-Label. | Hauptdatensatz für Training, Validierung und EDA (Phase **U**, **A**). |
| **Bank Customer Churn** | Kaggle (Public Domain) | Daten von 10.000 Bankkunden mit Kredit-Score, Balance und Produktanzahl. | Validierung der Pipeline-Generalisierbarkeit auf Finanzdaten (Phase **C**). |
| **Synthetic Churn Data** | Generiert (`scikit-learn`) | Synthetischer Datensatz (100k Samples) mit simulierten Features. | Lasttests für die API und Benchmarking der Inferenzzeit (Phase **K**). |
| **US Zip Code Database** | SimpleMaps (Basic) | Zuordnungstabelle von PLZ zu US-Bundesstaaten und Koordinaten. | Feature Engineering zur Anreicherung geografischer Informationen (Phase **A**). |
