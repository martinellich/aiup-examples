# Hotelreservierungssystem – Anforderungskatalog

## Projektübersicht

Ein webbasiertes Hotelreservierungssystem, das Gästen die Suche, Buchung und Verwaltung von Hotelzimmerreservierungen
ermöglicht. Das System
unterstützt Hotelmitarbeitende bei der Verwaltung von Buchungen, der Zimmerverfügbarkeit und Gästeservices.

## Funktionale Anforderungen

| ID     | Anforderung                 | Beschreibung                                                                                                                         | Priorität |
|--------|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------|-----------|
| FR-001 | Zimmersuche                 | Gäste können verfügbare Zimmer nach Check-in-Datum, Check-out-Datum, Anzahl der Gäste und Zimmertyp suchen                           | Hoch      |
| FR-002 | Zimmerbuchung               | Gäste können verfügbare Zimmer durch Angabe persönlicher Daten und Zahlungsinformationen reservieren                                 | Hoch      |
| FR-003 | Buchungsbestätigung         | Das System sendet eine Buchungsbestätigung mit Reservierungsdetails per E-Mail                                                       | Hoch      |
| FR-004 | Buchungsverwaltung          | Gäste können ihre bestehenden Reservierungen anzeigen, ändern oder stornieren                                                        | Mittel    |
| FR-005 | Zimmerstammdaten            | Hotelmitarbeitende können Zimmerinformationen einschliesslich Typ, Kapazität und Ausstattung hinzufügen, aktualisieren und entfernen | Hoch      |
| FR-006 | Verfügbarkeitsverwaltung    | Hotelmitarbeitende können die Zimmerverfügbarkeit für bestimmte Daten anzeigen und aktualisieren                                     | Hoch      |
| FR-007 | Gäste-Check-in              | Hotelmitarbeitende können Gäste einchecken und konkrete Zimmernummern zuweisen                                                       | Hoch      |
| FR-008 | Gäste-Check-out             | Hotelmitarbeitende können Gäste auschecken und Schlussrechnungen erzeugen                                                            | Hoch      |
| FR-009 | Zahlungsabwicklung          | Das System verarbeitet Kreditkartenzahlungen für Reservierungen                                                                      | Hoch      |
| FR-010 | Preisverwaltung             | Hotelmitarbeitende können Zimmerpreise je nach Saison und Nachfrage festlegen und aktualisieren                                      | Mittel    |
| FR-011 | Gästekonto                  | Das System führt Gästekonten mit Kontaktdaten und Buchungshistorie                                                                   | Mittel    |
| FR-012 | Reporting                   | Hotelmitarbeitende können Berichte zu Auslastung, Umsatz und Buchungsstatistiken erstellen                                           | Mittel    |
| FR-013 | Zimmerstatus-Aktualisierung | Hotelmitarbeitende können den Zimmerstatus aktualisieren (sauber, schmutzig, Wartung, ausser Betrieb)                                | Mittel    |
| FR-014 | Buchungsbenachrichtigungen  | Das System sendet Erinnerungs-E-Mails an Gäste vor dem Check-in-Datum                                                                | Niedrig   |

## Nicht-funktionale Anforderungen

| ID      | Anforderung            | Beschreibung                                                              | Kennzahl                                                    | Priorität |
|---------|------------------------|---------------------------------------------------------------------------|-------------------------------------------------------------|-----------|
| NFR-001 | Antwortzeit            | Das System reagiert auf Benutzeranfragen innerhalb akzeptabler Zeitlimits | < 1 Sekunde für Suche, < 2 Sekunden für Buchung             | Hoch      |
| NFR-002 | Verfügbarkeit          | Das System steht für Buchungsvorgänge zur Verfügung                       | 99,5 % Betriebszeit während der Geschäftszeiten             | Hoch      |
| NFR-003 | Gleichzeitige Benutzer | Das System unterstützt mehrere gleichzeitige Benutzer                     | Bis zu 50 gleichzeitige Benutzer                            | Mittel    |
| NFR-004 | Datensicherheit        | Personen- und Zahlungsdaten der Gäste sind geschützt                      | SSL-Verschlüsselung                                         | Hoch      |
| NFR-005 | Responsives Design     | Das System passt sich verschiedenen Bildschirmgrössen an                  | Responsives Design für Tablets und Smartphones              | Mittel    |
| NFR-006 | Datensicherung         | Regelmässige Sicherung der Reservierungs- und Gästedaten                  | Tägliche automatisierte Backups mit Wiederherstellungstests | Hoch      |
| NFR-007 | Benutzeroberfläche     | Das System bietet eine intuitive und benutzerfreundliche Oberfläche       | Usability-Tests mit Zielnutzenden                           | Mittel    |
| NFR-008 | Skalierbarkeit         | Das System kann Wachstum bei Buchungen und Nutzenden bewältigen           | Unterstützung für 200 % Steigerung der aktuellen Last       | Niedrig   |

## Randbedingungen

| ID      | Restriktion                 | Beschreibung                                                                     | Typ       | Auswirkung                         |
|---------|-----------------------------|----------------------------------------------------------------------------------|-----------|------------------------------------|
| CON-001 | Technologiestack            | Muss Vaadin, Spring Boot und jOOQ verwenden                                      | Technisch | Entwicklungsansatz und Architektur |
| CON-002 | Datenbank                   | Muss die PostgreSQL-Datenbank verwenden                                          | Technisch | Datenspeicherung und Abfragedesign |
| CON-003 | Barrierefreiheit            | Muss grundlegende Web-Standards zur Barrierefreiheit (WCAG 2.1 Stufe A) erfüllen | Rechtlich | UI-Design und Implementierung      |
| CON-004 | Mehrsprachige Unterstützung | Das System unterstützt Deutsch, Französisch, Italienisch und Englisch            | Niedrig   | Attraktivität für Nutzende         |

