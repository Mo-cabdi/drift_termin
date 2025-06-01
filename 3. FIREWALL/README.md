For å installere OPNsense på Hyper-V, følg disse trinnene:

### 1. **Forbered OPNsense-installasjonsfilene**
   - Last ned OPNsense-installasjons-ISO fra den offisielle nettsiden: [https://opnsense.org/download/](https://opnsense.org/download/).
   - Velg den riktige arkitekturen (vanligvis "AMD64") og et speil nærmest din plassering.

### 2. **Lag en ny virtuell maskin (VM) i Hyper-V**

   - Åpne **Hyper-V Manager**.
   - I **Actions**-panelet på høyre side, klikk på **New** og velg **Virtual Machine**.
   - **Gi VM-en et navn** (f.eks. "OPNsense").
   - **Velg generasjon**:
     - Velg **Generation 1** for BIOS-baserte systemer (de fleste OPNsense-installasjoner bruker denne).
   - **Tildel minne** (anbefalt 2 GB eller mer, avhengig av behov).
   - **Konfigurer nettverk**:
     - Velg en **External virtual switch** for VM-ens nettverksadapter for å få tilgang til internett eller ditt lokale nettverk.
   - **Konfigurer virtuell harddisk**:
     - Velg **Create a virtual hard disk**, og sett passende størrelse (f.eks. 10-20 GB er vanligvis tilstrekkelig for OPNsense).
   - **Installer operativsystem**:
     - Velg **Install an operating system from a bootable CD/DVD-ROM**, og pek til OPNsense ISO-filen du lastet ned tidligere.

### 3. **Juster VM-innstillingene**

   Før du starter VM-en, sørg for at innstillingene er riktige for OPNsense:

   - **Prosessor**:
     - Gå til **Processor**-innstillingene og sørg for at minst **1 virtuell prosessor** er tildelt (om du planlegger å bruke den til mer intensive oppgaver, kan du tildele flere).
   - **DVD-stasjon**:
     - Verifiser at **ISO**-filen for OPNsense er festet til DVD-stasjonen i VM-innstillingene.
   - **Nettverksadapter**:
     - Sørg for at den **eksterne nettverksadapteren** er korrekt tilkoblet.

### 4. **Start den virtuelle maskinen**
   - Høyreklikk på VM-en i Hyper-V Manager og velg **Start**.
   - Åpne **Virtual Machine Connection**-vinduet.

### 5. **Installer OPNsense**

   - VM-en skal starte opp og laste OPNsense-installasjonsprogrammet.
   - Følg instruksjonene på skjermen for å installere OPNsense. Her er de viktigste trinnene:
     - Velg **Install (UFS)** når du blir spurt om installasjonsmetode.
     - Velg harddisken for å installere OPNsense (vanligvis den standard disken).
     - Sett opp et **root-passord** og andre konfigurasjoner som forespurt (f.eks. velg standard tastaturoppsett).
     - Vent til installasjonen er fullført.
     - Når installasjonen er ferdig, vil installasjonsprogrammet be om å starte på nytt. Husk å fjerne ISO-filen fra den virtuelle CD/DVD-stasjonen, slik at den ikke starter opp i installasjonsprogrammet på nytt.

### 6. **Konfigurasjon etter installasjon**

   - Når OPNsense er installert og VM-en starter på nytt, vil systemet be om å konfigurere nettverksgrensesnittene.
   - Som standard bruker OPNsense **to grensesnitt** (WAN og LAN).
     - Konfigurer **WAN**-grensesnittet for å koble til internett (det kan konfigureres dynamisk eller statisk, avhengig av ditt nettverk).
     - Konfigurer **LAN**-grensesnittet for interne nettverkstilkoblinger.
   - Etter at grensesnittene er konfigurert, kan du få tilgang til **OPNsense Web GUI** fra en nettleser ved å navigere til LAN-grensesnittets IP-adresse (standard er 192.168.1.1).
   - Logg inn med standard legitimasjon:  
     - **Brukernavn:** `root`  
     - **Passord:** (passordet du satte under installasjonen).

### 7. **Fullfør konfigurasjonen**
   - Nå kan du fortsette med videre konfigurasjoner i OPNsense GUI, som å sette opp brannmur, VPN, DNS osv.

### Ytterligere notater:
   - Du kan også tildele flere virtuelle nettverksadaptere hvis du ønsker flere grensesnitt for spesifikke formål som VLAN-er.

Det er det! Du har nå OPNsense kjørende på Hyper-V.
