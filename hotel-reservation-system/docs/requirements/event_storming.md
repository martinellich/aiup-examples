# Event Storming Diagram - Hotelreservierungssystem

## Legende
- 🟦 **Kommandos** (Commands) - Aktionen, die von Benutzern ausgelöst werden
- 🟧 **Domain Events** - Dinge, die im System passieren
- 🟨 **Akteure** (Actors) - Wer löst Kommandos aus
- 🟪 **Policies** - Automatische Reaktionen auf Events
- 🟩 **Read Models** - Ansichten/Abfragen

---

## Buchungs-Flow (Gäste)

```mermaid
graph LR
    G1[🟨 Gast] -->|sucht Zimmer| C1[🟦 Zimmer suchen]
    C1 --> E1[🟧 Zimmer gesucht]
    E1 --> R1[🟩 Verfügbare Zimmer anzeigen]

    G1 -->|bucht Zimmer| C2[🟦 Zimmer buchen]
    C2 --> E2[🟧 Zimmer gebucht]
    E2 --> E3[🟧 Zahlung verarbeitet]
    E3 -->|Policy| P1[🟪 Bestätigung senden]
    P1 --> E4[🟧 Buchungsbestätigung gesendet]
    E4 --> E5[🟧 Gästekonto erstellt/aktualisiert]

    G1 -->|verwaltet Buchung| C3[🟦 Buchung anzeigen/ändern/stornieren]
    C3 --> E6[🟧 Buchung angezeigt/geändert/storniert]

    E2 -->|Policy: Check-in naht| P2[🟪 Erinnerung senden]
    P2 --> E7[🟧 Erinnerungs-E-Mail gesendet]
```

---

## Hotelverwaltungs-Flow (Mitarbeitende)

```mermaid
graph LR
    M1[🟨 Hotelmitarbeitende] -->|verwaltet Zimmer| C4[🟦 Zimmer hinzufügen/aktualisieren/entfernen]
    C4 --> E8[🟧 Zimmerstammdaten geändert]

    M1 -->|verwaltet Verfügbarkeit| C5[🟦 Verfügbarkeit aktualisieren]
    C5 --> E9[🟧 Verfügbarkeit aktualisiert]

    M1 -->|checkt Gast ein| C6[🟦 Gast einchecken]
    C6 --> E10[🟧 Gast eingecheckt]
    E10 --> E11[🟧 Zimmernummer zugewiesen]

    M1 -->|checkt Gast aus| C7[🟦 Gast auschecken]
    C7 --> E12[🟧 Gast ausgecheckt]
    E12 -->|Policy| P3[🟪 Rechnung erstellen]
    P3 --> E13[🟧 Schlussrechnung erzeugt]

    M1 -->|verwaltet Preise| C8[🟦 Preis festlegen/aktualisieren]
    C8 --> E14[🟧 Zimmerpreis aktualisiert]

    M1 -->|verwaltet Zimmerstatus| C9[🟦 Zimmerstatus aktualisieren]
    C9 --> E15[🟧 Zimmerstatus geändert]

    M1 -->|erstellt Berichte| C10[🟦 Bericht erstellen]
    C10 --> E16[🟧 Bericht erstellt]
    E16 --> R2[🟩 Auslastung/Umsatz/Statistiken]
```

---

## Vollständiges Event Storming Board

```mermaid
graph TB
    subgraph Gäste["🟨 Gäste (Guests)"]
        G1[Gast]
    end

    subgraph Suche["Zimmersuche"]
        C1[🟦 Zimmer suchen<br/>FR-001]
        E1[🟧 Zimmer gesucht]
        R1[🟩 Verfügbare Zimmer]
    end

    subgraph Buchung["Buchungsprozess"]
        C2[🟦 Zimmer buchen<br/>FR-002]
        E2[🟧 Zimmer gebucht]
        C9[🟦 Zahlung verarbeiten<br/>FR-009]
        E3[🟧 Zahlung verarbeitet]
        P1[🟪 Bestätigung automatisch senden]
        E4[🟧 Buchungsbestätigung gesendet<br/>FR-003]
        E5[🟧 Gästekonto aktualisiert<br/>FR-011]
    end

    subgraph BuchungsVerwaltung["Buchungsverwaltung"]
        C3[🟦 Buchung anzeigen/ändern/stornieren<br/>FR-004]
        E6[🟧 Buchung geändert/storniert]
        P2[🟪 Check-in Erinnerung]
        E7[🟧 Erinnerungs-E-Mail gesendet<br/>FR-014]
    end

    subgraph Personal["🟨 Hotelmitarbeitende (Staff)"]
        M1[Mitarbeitende]
    end

    subgraph ZimmerVerwaltung["Zimmerverwaltung"]
        C4[🟦 Zimmer hinzufügen/aktualisieren/entfernen<br/>FR-005]
        E8[🟧 Zimmerstammdaten geändert]
        C5[🟦 Verfügbarkeit aktualisieren<br/>FR-006]
        E9[🟧 Verfügbarkeit aktualisiert]
        C8[🟦 Preis festlegen/aktualisieren<br/>FR-010]
        E14[🟧 Zimmerpreis aktualisiert]
        C10[🟦 Zimmerstatus aktualisieren<br/>FR-013]
        E15[🟧 Zimmerstatus geändert]
    end

    subgraph CheckInOut["Check-in / Check-out"]
        C6[🟦 Gast einchecken<br/>FR-007]
        E10[🟧 Gast eingecheckt]
        E11[🟧 Zimmernummer zugewiesen]
        C7[🟦 Gast auschecken<br/>FR-008]
        E12[🟧 Gast ausgecheckt]
        P3[🟪 Rechnung automatisch erstellen]
        E13[🟧 Schlussrechnung erzeugt]
    end

    subgraph Reporting["Reporting"]
        C11[🟦 Bericht erstellen<br/>FR-012]
        E16[🟧 Bericht erstellt]
        R2[🟩 Auslastung/Umsatz/Statistiken]
    end

    %% Gäste-Flow
    G1 --> C1
    C1 --> E1
    E1 --> R1
    G1 --> C2
    C2 --> E2
    E2 --> C9
    C9 --> E3
    E3 --> P1
    P1 --> E4
    E4 --> E5
    G1 --> C3
    C3 --> E6
    E2 --> P2
    P2 --> E7

    %% Personal-Flow
    M1 --> C4
    C4 --> E8
    M1 --> C5
    C5 --> E9
    M1 --> C8
    C8 --> E14
    M1 --> C10
    C10 --> E15
    M1 --> C6
    C6 --> E10
    E10 --> E11
    M1 --> C7
    C7 --> E12
    E12 --> P3
    P3 --> E13
    M1 --> C11
    C11 --> E16
    E16 --> R2

    style G1 fill:#fff9c4
    style M1 fill:#fff9c4
    style P1 fill:#e1bee7
    style P2 fill:#e1bee7
    style P3 fill:#e1bee7
    style R1 fill:#c8e6c9
    style R2 fill:#c8e6c9
```

---

## Aggregates (Bounded Contexts)

### 1. **Buchung (Reservation)**
- **Events**: Zimmer gebucht, Buchung geändert, Buchung storniert, Zahlung verarbeitet, Bestätigung gesendet
- **Commands**: Zimmer buchen, Buchung ändern, Buchung stornieren
- **Business Rules**:
  - Verfügbarkeit prüfen vor Buchung
  - Zahlung erforderlich für Buchung
  - Stornierungsrichtlinien beachten

### 2. **Zimmer (Room)**
- **Events**: Zimmerstammdaten geändert, Verfügbarkeit aktualisiert, Zimmerpreis aktualisiert, Zimmerstatus geändert
- **Commands**: Zimmer hinzufügen/aktualisieren/entfernen, Verfügbarkeit aktualisieren, Preis festlegen
- **Business Rules**:
  - Zimmertyp und Kapazität definieren
  - Preise saisonabhängig
  - Status: verfügbar, sauber, schmutzig, Wartung, außer Betrieb

### 3. **Aufenthalt (Stay)**
- **Events**: Gast eingecheckt, Zimmernummer zugewiesen, Gast ausgecheckt, Schlussrechnung erzeugt
- **Commands**: Gast einchecken, Gast auschecken
- **Business Rules**:
  - Check-in nur mit gültiger Buchung
  - Zimmernummer bei Check-in zuweisen
  - Rechnung bei Check-out erstellen

### 4. **Gästekonto (Guest Account)**
- **Events**: Gästekonto erstellt/aktualisiert, Buchungshistorie aktualisiert
- **Commands**: Kontodaten aktualisieren, Buchungshistorie abfragen
- **Business Rules**:
  - Kontaktdaten pflegen
  - Buchungshistorie speichern

### 5. **Reporting**
- **Events**: Bericht erstellt
- **Commands**: Bericht erstellen (Auslastung, Umsatz, Buchungsstatistiken)
- **Business Rules**:
  - Historische Daten auswerten
  - Verschiedene Berichtstypen unterstützen

---

## Wichtige Policies (Automatisierung)

1. **🟪 Buchungsbestätigung automatisch senden**
   - **Trigger**: Zimmer gebucht + Zahlung verarbeitet
   - **Aktion**: E-Mail mit Reservierungsdetails senden

2. **🟪 Check-in Erinnerung senden**
   - **Trigger**: Check-in-Datum naht (z.B. 24h vorher)
   - **Aktion**: Erinnerungs-E-Mail an Gast senden

3. **🟪 Schlussrechnung automatisch erstellen**
   - **Trigger**: Gast ausgecheckt
   - **Aktion**: Rechnung generieren und bereitstellen

4. **🟪 Verfügbarkeit aktualisieren**
   - **Trigger**: Zimmer gebucht / Gast eingecheckt / Gast ausgecheckt
   - **Aktion**: Zimmerverfügbarkeit im System aktualisieren

---

## Externe Systeme

- 🟩 **Zahlungssystem** (FR-009): Kreditkartenzahlungen verarbeiten
- 🟩 **E-Mail-System** (FR-003, FR-014): Bestätigungen und Erinnerungen versenden
- 🟩 **Reporting-System** (FR-012): Berichte generieren

---

## Hot Spots / Risiken 🔴

1. **Doppelbuchungen vermeiden**: Gleichzeitige Buchungen desselben Zimmers
2. **Zahlungssicherheit**: PCI-DSS-Konformität für Kreditkartendaten (NFR-004)
3. **Verfügbarkeitskonsistenz**: Synchronisation zwischen Buchungen und Check-ins
4. **Stornierungsfristen**: Rückerstattungslogik und Geschäftsregeln
5. **Gleichzeitige Benutzer**: 50 gleichzeitige Benutzer unterstützen (NFR-003)
6. **Antwortzeiten**: < 1s für Suche, < 2s für Buchung (NFR-001)