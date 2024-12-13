# IT-drift Dokumentasjon

## Hvordan sette opp DHCP

### Del 1: Installere DHCP-rollen
1. Åpne **Server Manager** og klikk på **Add Roles and Features** i Server Manager Dashboard.
2. Velg **Role-based or feature-based installation**, og klikk **Next**.
3. Velg serveren du vil installere DHCP-rollen på, og klikk **Next**.
4. Velg **DHCP Server**, og klikk **Add Features** når dialogboksen vises.
5. Klikk **Next** til du kommer til siste side, og velg **Install**.

### Del 2: Konfigurere DHCP
1. Trykk på trekanten som vises ved flagget i Server Manager for å starte konfigurasjonen.
2. Velg **Complete DHCP Configuration**.
3. Velg om DHCP skal autoriseres automatisk i Active Directory (nødvendig i et domene).
4. Velg legitimasjon (administratorkontoen brukes vanligvis som standard), og klikk **Commit**.
5. Klikk **Close** når du er ferdig.

### Del 3: Lage et nytt Scope
1. Gå til **Tools** i Server Manager, og velg **DHCP**.
2. Velg DHCP-serveren fra listen i venstre panel.
3. Høyreklikk på **IPv4** (eller IPv6, avhengig av nettverket ditt), og velg **New Scope**.
4. Fyll ut følgende informasjon:
   - **Navn og beskrivelse**: Gi scope et beskrivende navn.
   - **IP-adresseområde**: Angi start- og sluttadressene for IP-adressene som skal deles ut.
   - **Ekskluder adresser**: Spesifiser adresser i området som ikke skal deles ut.
   - **Leietid**: Angi hvor lenge en klient kan beholde en IP-adresse (standard er 8 dager).
   - **Ruter (standard gateway)**: Oppgi IP-adressen til nettverkets gateway.
   - **Domenenavn og DNS-servere**: Oppgi domenenavn og DNS-servernes IP-adresser.
   - **WINS-servere (valgfritt)**: Oppgi IP-adresser til WINS-servere (hvis brukt).
5. Velg om du vil aktivere scope med en gang eller senere.
6. Når scopen er aktivert:
   - Høyreklikk på serverens navn i venstre rute.
   - Velg **Authorize**, bekreft autorisasjon, og klikk **Refresh**.
7. Kontroller at IPv4-statusen er grønn, som indikerer at det fungerer.

---

## Sette opp Domenet

### Del 1: Konfigurere domenekontroller
1. **Velg en domenekontroller**: Dette er en server som administrerer domenet. Den lagrer brukerkontoer, grupper, data om datamaskiner, og andre objekter i domenet.
2. **Installer Active Directory**: Active Directory er Microsofts tjeneste for domenestyring. Den gir en sentral database for å lagre informasjon om brukere, datamaskiner og objekter i nettverket.
3. **Konfigurer domenet**:
   - Definer domenenavn.
   - Opprett organisasjonsenheter (OUs).
   - Angi gruppepolicyer.
4. **Bli med datamaskiner i domenet**:
   - Hver datamaskin som skal være en del av domenet, må kobles til det. Dette kan gjøres under operativsysteminstallasjon eller etterpå.

### Del 2: Opprette brukere
1. Åpne **Active Directory Users and Computers** i Server Manager.
2. Naviger til domenenavnet ditt i venstre panel, og høyreklikk på **Users**-mappen.
3. Velg **New > User**.
4. Fyll ut brukerinformasjonen:
   - **Full name**: Fullt navn på brukeren.
   - **User logon name**: Brukernavn for pålogging.
5. Angi et midlertidig passord, og huk av for **User must change password at next logon** (anbefalt for sikkerhet).
6. Klikk **Next** og deretter **Finish** for å opprette brukeren.

### Del 3: Koble klientmaskiner til domenet
1. Logg inn på klientmaskinen som lokal administrator.
2. Åpne **System Properties** (høyreklikk på Denne PC-en > Egenskaper).
3. Klikk på **Endre innstillinger** under Datamaskinnavn, domene og arbeidsgruppeinnstillinger.
4. Velg **Endre**, og under **Medlem av**, velg **Domene**.
5. Skriv inn domenenavnet og klikk **OK**.
6. Når du blir bedt om legitimasjon, skriv inn en administratorkonto for domenet.
7. Start maskinen på nytt etter vellykket tilkobling.

### Del 4: Gi en bruker administratorrettigheter
1. Åpne **Active Directory Users and Computers**.
2. Finn brukeren du vil gi administratorrettigheter til.
3. Høyreklikk på brukeren, og velg **Properties**.
4. Gå til fanen **Member Of** og klikk **Add**.
5. Skriv inn **Domain Admins**, og klikk **OK**.
6. Klikk **Apply**, og deretter **OK** for å lagre endringene.

---

## VLAN-konfigurasjon

### Metode 1: Hvis nettverksadapteren støtter VLAN
1. Åpne **Network Connections** ved å søke på det i søkefeltet.
2. Høyreklikk på **Ethernet** og velg **Properties**.
3. Klikk på **Configure** og gå til **Advanced**-fanen.
4. Finn **VLAN ID**, og skriv inn ønsket ID (f.eks. 851).

### Metode 2: Hvis nettverksadapteren ikke støtter VLAN
1. Åpne **Hyper-V Manager**.
2. Klikk på **Virtual Switch Manager** på venstre side.
3. Velg **External** og klikk **Create Virtual Switch**.
4. Gi det et navn, aktiver **VLAN ID**, og skriv inn ønsket ID.
5. Klikk **Apply**.
6. Opprett en intern svitsj:
   - Klikk **New Virtual Network Switch** og velg **Internal**.
   - Ikke aktiver VLAN ID for interne svitsjer.

---

## Installere Web Server og lage en standard startside

### Installere IIS Manager
1. Åpne **Server Manager** og legg til roller og funksjoner.
2. Velg serveren du vil installere IIS på, og klikk **Next**.
3. Huk av for **Web Server (IIS)** under **Server Roles**.
4. Klikk **Next** og deretter **Install**.
5. Start IIS Manager ved å skrive `inetmgr` i Run-vinduet (Win + R).

### Last opp nettsidefiler til wwwroot
1. Naviger til `C:\inetpub\wwwroot`.
2. Kopier nettsidefilene (HTML, CSS, JS, etc.) til denne mappen.
3. Konfigurer IIS:
   - Åpne IIS Manager.
   - Høyreklikk på **Sites** og velg **Add Website**.
   - Sjekk at **Physical Path** peker til `C:\inetpub\wwwroot`.
   - Velg domene-IP under **Bindings**.
   - Klikk **Browse Website** for å teste.

---

## Bruk av gruppepolicy

1. **Installer Microsoft Edge Administrative Template**:
   - Last ned policy-filene (.admx) fra [Microsoft Edge for Business](https://www.microsoft.com/edge/business/download).
2. **Kopier .admx-filer**:
   - Legg filene til `C:\Windows\PolicyDefinitions`.
   - Kopier språkfiler (.adml) til tilsvarende språkmappe (f.eks. `nb-NO`).
3. **Åpne gruppepolicyeditoren**:
   - Trykk Win + R, skriv `gpedit.msc`, og trykk Enter.
4. **Naviger til policyer for Microsoft Edge**:
   - Gå til **Datamaskinkonfigurasjon > Administrative maler > Microsoft Edge**.
5. **Konfigurer policy**:
   - Dobbeltklikk på ønsket policy, f.eks. **Angi oppstartssider**.
   - Aktiver policyen og angi ønsket URL.
6. **Bruk policyen**:
   - Kjør `gpupdate /force` i et administratorkommandovindu.
7. Start Edge på nytt for å se endringene.
