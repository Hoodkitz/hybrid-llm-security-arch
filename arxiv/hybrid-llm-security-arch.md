# Hybride optisch-digitale Sicherheitsarchitektur für MoE-LLMs: CertMoE, CaMeL und nanophotonische Hardware

## Executive Summary

Dieses Papier skizziert eine mehrschichtige Sicherheitsarchitektur für Large Language Models (LLMs) mit Mixture-of-Experts (MoE). Das Konzept sieht drei zentrale Ebenen vor: (1) eine routing-bewusste Robustheitszertifizierung (CertMoE), (2) eine systemische Prompt-Injection-Abwehr für Multi-Agenten-Systeme (CaMeL) und (3) eine nanophotonische Hardware-Schicht als physikalische Obfuskation und Beschleuniger. Abschließend werden technologische Reifegrade (TRL) und Latenzprofile der relevanten Komponenten bewertet.

## 1. Einleitung und Motivation

Die rasante Zunahme von Angriffen im Bereich Adversarial Machine Learning (AML) zeigt, dass klassische Software-Sicherheit für LLMs nicht ausreicht. Gleichzeitig definieren das NIST AI Risk Management Framework (AI RMF 1.0) und die NIST AI 100-2 Taxonomie klare Erwartungen an Robustheit, Transparenz und Lebenszyklus-Sicherheit. Moderne generative Modelle, insbesondere großskalige LLMs mit Mixture-of-Experts (MoE), stellen diese Anforderungen vor neue Herausforderungen: Routing-Entscheidungen, verteilte Experten und Multi-Agenten-Orchestrierung erzeugen neue Angriffsflächen.

Vor diesem Hintergrund wird ein Paradigmenwechsel vorgeschlagen: Sicherheitsgarantien sollen nicht nur auf Software-Ebene, sondern durch hybride optisch-digitale Architekturen erzwungen werden.

## 2. Adversarial Machine Learning und NIST-Taxonomie

NIST AI 100-2 beschreibt eine Taxonomie von Adversarial Machine Learning, die vier Dimensionen umfasst: Angriffstypen (Evasion, Poisoning, Privacy, Abuse), Angriffsstufen (White-Box, Black-Box), Angriffsziele (Integrity, Availability, Confidentiality) und Angriffsoberflächen (Training, Inference, Deployment).

Die NIST-Taxonomie zeigt, dass Angriffe auf LLMs nicht nur die Modellparameter, sondern auch das Routing, die Datenpipeline und die Deployment-Infrastruktur betreffen können. In Kombination mit dem AI RMF wird deutlich, dass vertrauenswürdige KI nicht als monolithisches System, sondern als geschichtetes, messbares und kontrollierbares Gesamtsystem zu verstehen ist.

## 3. CertMoE: Routing-bewusste Robustheitszertifizierung für MoE-LLMs

### 3.1 Grundidee von CertMoE

CertMoE ist ein Framework zur Robustheitszertifizierung für MoE-LLMs, das Routing-Entscheidungen explizit in die Zertifizierung einbezieht. Für einen gegebenen Eingabeprompt wird eine Menge von stochastisch permutierten Eingaben erzeugt und das Modell darauf evaluiert. Die Zertifizierung nutzt statistische Methoden, um eine untere Schranke für die Robustheit gegen adversariale Störungen zu garantieren.

### 3.2 Routing-Containment und Failure Attribution

Ein zentrales Konzept ist der Routing-Containment-Constraint: Nur wenn die Expertenauswahl über alle permutierten Eingaben hinweg innerhalb eines definierten Bereichs bleibt, gilt das Zertifikat als gültig. Dies verhindert, dass ein Angreifer durch geschickte Eingabe das Routing manipuliert und dadurch die Robustheitsgarantie umgeht.

CertMoE ermöglicht zusätzlich eine analytische Failure Attribution: Bei Zertifikatsverletzungen kann nachvollzogen werden, ob der Fehler im Routing, in der Expertenauswahl oder in der finalen Ausgabe liegt.

### 3.3 Betriebsmodell und Overhead

CertMoE ist explizit als On-Demand-Zertifizierer konzipiert: Im Normalbetrieb läuft das Modell ohne Overhead, die Zertifizierung wird nur bei Bedarf (z. B. bei sicherheitskritischen Anfragen oder vor Deployment-Entscheidungen) aktiviert.

Dieses Betriebsmodell erlaubt es, Zertifizierung selektiv etwa für sicherheitskritische Eingaben oder vor Modell-Updates durchzuführen, ohne den produktiven Betrieb zu beeinträchtigen.

## 4. Multi-Agenten-Architekturen und CaMeL-Defense

### 4.1 Agentensysteme und OWASP-GenAI-Kontext

In Enterprise-Umgebungen entstehen zunehmend Multi-Agenten-Systeme, in denen LLMs als Orchestratoren, Planer und Ausführer agieren. Diese Systeme erhöhen die Angriffsfläche deutlich, weil Angreifer nicht nur auf das zentrale Modell, sondern auf die gesamte Agenten-Interaktionskette abzielen können.

### 4.2 CaMeL: Prompt-Injection-Abwehr durch Systemdesign

CaMeL ("Defeating Prompt Injections by Design") schlägt eine systemische Defense vor, die Prompt-Injection nicht durch Filter, sondern durch architektonische Trennung verhindert. Die Architektur erzwingt strikte Input- und Output-Policies: Untrusted Inputs werden als Daten behandelt, nicht als Instruktionen. Jede Agentenaktion wird durch eine Policy-Maschine validiert, bevor sie ausgeführt wird.

### 4.3 Integration mit CertMoE

Die Kombination von CertMoE und CaMeL eröffnet eine zweistufige Sicherheitsarchitektur: CertMoE zertifiziert die Robustheit des zugrundeliegenden MoE-Modells, während CaMeL die Agenten-Interaktionen absichert. Für besonders kritische Subtasks in einer Multi-Agenten-Umgebung könnte die Policy von CaMeL sogar eine CertMoE-Zertifizierung als Voraussetzung für die Ausführung verlangen.

## 5. Nanophotonische Hardware als Sicherheitsanker

### 5.1 Optische Neural Networks und Security by Light

Optische und nanophotonische Rechenarchitekturen werden intensiv als Beschleuniger für neuronale Netze erforscht. Gleichzeitig existiert Arbeit zu Datenschutz in neuromorphen photonic Systemen, die belegt, dass optische Hardware nicht nur Performance, sondern auch Sicherheitseigenschaften bieten kann.

Diese Literatur belegt, dass Photonik-Sicherheit ein wachsendes Forschungsfeld ist, das über reine Beschleunigung hinausgeht.

### 5.2 Optik als physikalische Obfuskation von Gradienten und Gewichten

Die vorgeschlagene Architektur nutzt nanophotonische Komponenten nicht nur zur Beschleunigung, sondern als physikalische Obfuskation: Gewichte und Gradienten werden in optischen Medien gespeichert und verarbeitet, was einen White-Box-Angreifer auf digitaler Ebene an der vollständigen Rekonstruktion der Modellparameter hindert.

Ein White-Box-Angreifer, der auf der digitalen Ebene vollständigen Zugriff auf Gewichte und Aktivierungen hat, kann die optische Schicht nicht vollständig rekonstruieren, da die physikalische Realisierung (Phase, Amplitude, Polarisation) Informationen enthält, die nicht digital abgebildet werden.

Diese physikalische Obfuskation ersetzt keine kryptographischen oder softwareseitigen Sicherheitsmaßnahmen, sondern ergänzt sie um eine zusätzliche Verteidigungsebene.

### 5.3 Schnittstellen und Latenzprofile

Der Engpass hybrider optisch-digitaler Architekturen liegt in den Elektro-Optischen (E/O) und Opto-Elektrischen (O/E) Schnittstellen. DMD/MEMS-basierte Modulatoren arbeiten typischerweise im Bereich von etwa 10–100 Mikrosekunden, während integrierte Photonik-ICs Latenzen im Nanosekundenbereich erreichen können.

Die Architektur muss daher E/O- und O/E-Schnittstellen so gestalten, dass Zertifizierungs- und Defense-Operationen innerhalb akzeptabler Latenzbudgets bleiben.

## 6. Supply-Chain-Sicherheit und Modelllebenszyklus

### 6.1 Bedrohungen entlang der LLM-Pipeline

Der Lebenszyklus moderner LLMs umfasst typischerweise Pre-Training auf großskaligen Datensätzen, Supervised Fine-Tuning, Reward Modeling und Reinforcement Learning. Da viele Organisationen externe Datensätze, Open-Source-Gewichte oder Third-Party-Modelle nutzen, ist die Supply-Chain ein kritischer Angriffspunkt.

### 6.2 Schutzprinzipien für die vier Phasen

Ausgehend von existierenden Best Practices und Standardisierungsansätzen lässt sich die Pipeline in vier Phasen unterteilen:

1. **Pre-Training:** Fokus auf Datenherkunft, automatisierte Detektion von Poisoning und Anomalien in Trainingsdaten.
2. **Supervised Fine-Tuning:** Härtung gegen Clean-Label- und Backdoor-Poisoning, etwa durch Datenvalidierung und Red-Teaming.
3. **Reward Modeling:** Strikte Isolierung und Zugangskontrollen für Reward-Modelle, um Manipulation zu verhindern.
4. **Reinforcement Learning / Deployment:** Kombination aus Ausgabefiltern, Zertifizierung (CertMoE) und Agenten-Defense (CaMeL).

Die vorgeschlagene optisch-digitale Schicht kann in Phase 1 und 4 zusätzliche Integritätsprüfungen durch physikalische Verifikation ermöglichen.

## 7. Technologischer Reifegrad (TRL) und Roadmap

### 7.1 TRL-Einschätzung zentraler Komponenten

| Subsystem / Komponente | Kategorie | Geschätzter TRL | Begründung |
|---|---|---|---|
| CertMoE & Routing-Smoothing | Software / Algorithmus | TRL 3–4 | Mathematisch fundiert, aber noch keine großskalige Evaluation |
| CaMeL-Defense / Agentenfilter | Software / Defense | TRL 3 | Forschungskonzept, erste Prototypen |
| DMD/MEMS-Modulatoren | Hardware / Optik | TRL 7–8 | Industriell verfügbar, aber nicht für NN optimiert |
| Integrierte Photonic-ICs für NN | Hardware / Optik | TRL 4–6 | Zahlreiche Prototypen, noch keine Standardisierung |
| Huygens-Metasurfaces | Hardware / Optik | TRL 2–3 | Experimentell, Grundlagenforschung |

Diese Einschätzung zeigt, dass ein vollständig integriertes optisch-digitales Sicherheitssystem heute nicht realisierbar ist, aber einzelne Komponenten bereits nutzbar sind.

### 7.2 Forschungsempfehlungen

Auf Basis der analysierten Literatur und der vorgeschlagenen Architektur lassen sich folgende Forschungsempfehlungen ableiten:

1. **Co-Design von Algorithmus und Hardware:** Entwicklung von Routing-Smoothing-Algorithmen, die auf optische Hardware zugeschnitten sind.
2. **Standardisierte Testbenchmarks:** Aufbau von Benchmarks zur Bewertung optisch-digitaler Sicherheitsarchitekturen.
3. **Integration in AI-RMF-Prozesse:** Verknüpfung der vorgeschlagenen Architektur mit NIST AI RMF und AI 100-2.
4. **Side-Channel- und Optik-spezifische Threat-Modelle:** Systematische Analyse optischer Angriffsvektoren.

### 7.3 Publikations- und Community-Strategie

Die in diesem Papier beschriebene Architektur liegt an der Schnittstelle von adversarial ML, Multi-Agenten-Sicherheit und photonischer Hardware. Geeignete Publikationsvenues umfassen:

- **Adversarial-ML-Workshops an Top-ML-Konferenzen**, z. B. AdvML-Workshop bei ICML oder NeurIPS
- **Security-Konferenzen mit ML-Fokus**, etwa USENIX Security, IEEE S&P, NDSS, ACSAC
- **Photonik- und Optik-Journals/Conferences**, wenn der Schwerpunkt stärker auf der hardwareseitigen Obfuskation liegt

Für eine erste Veröffentlichung bietet sich ein **Positions- oder Architekturpaper** an, das die drei Ebenen (CertMoE, CaMeL, Photonik) als integriertes Framework präsentiert.

## 8. Schlussfolgerung

Die Kombination aus NIST-Taxonomie, AI-RMF und aktueller Forschung zu CertMoE, CaMeL und photonischer Hardware ermöglicht eine neuartige, mehrschichtige Sicherheitsarchitektur für MoE-LLMs. Das hier ausgearbeitete Konzept einer hybriden optisch-digitalen Sicherheitsarchitektur zeigt, dass Sicherheit nicht nur als Software-Problem, sondern als systemisches, hardware-gestütztes Designproblem verstanden werden muss.
