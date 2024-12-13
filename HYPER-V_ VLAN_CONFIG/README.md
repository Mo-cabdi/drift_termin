# Opprette en ny virtuell maskin i Hyper-V

1. Åpne **Hyper-V Manager:** Dette er verktøyet du bruker for å administrere virtuelle maskiner på din Windows-server.
2. **Ny virtuell maskin:** Her starter du prosessen med å lage en ny virtuell datamaskin.
3. **Generasjon 2:** Dette er den nyeste typen virtuell maskin og gir bedre ytelse og fleksibilitet.
4. **Navn og plassering:** Gi maskinen et navn du husker, og velg hvor konfigurasjonsfilene skal lagres.
5. **Minne:** Dette er hvor mye RAM den virtuelle maskinen kan bruke. 2GB er et bra utgangspunkt for OpnSense.
6. **Nettverk:** Koble til et nettverk slik at den virtuelle maskinen kan kommunisere med andre enheter.
7. **Harddisk:** Dette er den virtuelle maskinens lagringsplass.








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
