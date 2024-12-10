# Konfigurere VLAN for å Komme Inn i Et Domene

For å komme inn i et domene, må du ha de riktige VLAN (Virtual Local Area Network) konfigurerte.

## Metoder for å Konfigurere VLAN

### Første Metode:
1. **Network Adapteren din støtter VLAN-konfigurasjon.**
2. For å sjekke, søk på `Network connection` i søkefeltet.
3. Høyreklikk på **Ethernet** og velg `Properties`.
4. Klikk på `Configure` og gå til `Advanced`-fanen.
5. Hvis tilgjengelig, kan du manuelt skrive inn VLAN-ID.

### Andre Metode:
1. **Network Adapteren din støtter ikke VLAN-konfigurasjon.**
2. Åpne `Hyper-V` og klikk på `Virtual Switch Manager` på venstre siden.
3. Velg `External` og klikk på `Create Virtual Switch`.
4. Gi den et navn, aktiver `VLAN-ID` og skriv inn din VLAN-ID (f.eks. `851`).
5. Klikk på `Apply`.
6. Klikk på `New Virtual Network Switch` for å lage en intern switch.
7. **Husk!** Ikke aktiver `VLAN-ID` i den interne switchen.
