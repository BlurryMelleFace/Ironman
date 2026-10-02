# Strava Aktivitäten — IRONMAN Belgium 2027

> Einzelne Strava-Aktivitäten werden als eigene Notizen in `Log/Strava/Activities` gespeichert. Diese Ansicht gruppiert sie nach Trainingswoche; mehrere Aktivitäten pro Tag bleiben getrennte Einträge.

![[Strava Activities.base]]

## Plugin einrichten

Derzeit ist kein Strava-Community-Plugin in diesem Vault aktiviert. Für einzelne Aktivitätsnotizen passt **Strava Sync**:

1. In Obsidian unter **Einstellungen → Community-Plugins** das Plugin installieren und aktivieren.
2. Strava-OAuth direkt im Plugin autorisieren. Zugangsdaten und Tokens nicht in Vault-Dateien oder Chats eintragen.
3. Als Speicherort `Log/Strava/Activities` festlegen.
4. Das Plugin-Template so konfigurieren, dass es die Felder aus [[Templates/Strava Activity Template]] befüllt. `week_start` muss der Montag der lokalen Aktivitätswoche sein; `week_number` folgt [[../Plan/03 Week by Week Schedule]].
5. Optional den CSV-Import für den historischen Backfill verwenden.

Die Activity Notes enthalten Rohdaten. Die manuell gepflegten Soll-/Ist- und RPE-Werte in [[Messwerte]] werden dadurch nicht überschrieben.
