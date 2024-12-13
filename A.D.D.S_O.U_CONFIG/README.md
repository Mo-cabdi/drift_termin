Here’s the updated documentation with sections for **å sette opp brukere, klienter og administrator** added:

---

# IT-Drift Dokumentasjon  
## Hvordan sette opp DHCP, Domenet, og Brukeradministrasjon  

---

## Innholdsfortegnelse  
1. [Installere DHCP - Del 1](#del-1-installere-dhcp)  
2. [Konfigurere DHCP - Del 2](#del-2-konfigurere-dhcp)  
3. [Lage et nytt Scope - Del 3](#del-3-lage-et-nytt-scope)  
4. [Sette opp et Domene](#sette-opp-domenet)  
5. [Sette opp Brukere, Klienter og Administrator](#sette-opp-brukere-klienter-og-administrator)  

---

### Del 1: Installere DHCP  
1. Åpne **Server Manager** og klikk på **Add Roles and Features** i **Server Manager Dashboard**.  
2. Velg **Role-based or feature-based installation**, og klikk **Next**.  
3. Velg serveren du vil installere DHCP-rollen på, og klikk **Next**.  
4. Velg **DHCP Server**, og klikk **Add Features** når dialogboksen vises.  
5. Klikk **Next** til du kommer til siste side, og velg **Install**.  

---

### Del 2: Konfigurere DHCP  
1. Trykk på trekanten som vises ved flagget i **Server Manager** for å starte konfigurasjonen.  
2. Velg **Complete DHCP Configuration**.  
3. Velg om DHCP skal autoriseres automatisk i **Active Directory** (nødvendig i et domene).  
4. Velg legitimasjon (administratorkontoen brukes vanligvis som standard), og klikk **Commit**.  
5. Klikk **Close** når du er ferdig.  

---

### Del 3: Lage et nytt Scope  
1. Gå til **Tools** i **Server Manager**, og velg **DHCP**.  
2. Velg DHCP-serveren fra listen i venstre panel.  
3. Høyreklikk på **IPv4** (eller **IPv6**, avhengig av nettverket ditt), og velg **New Scope**.  
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
7. Kontroller at **IPv4**-statusen er **grønn**, som indikerer at det fungerer.  

---

### Sette opp Domenet  
1. **Velg en domenekontroller**:  
   - Dette er en server som administrerer domenet. Den lagrer brukerkontoer, grupper, data om datamaskiner, og andre objekter i domenet.  
2. **Installer Active Directory**:  
   - Active Directory er Microsofts tjeneste for domenestyring. Den gir en sentral database for å lagre informasjon om brukere, datamaskiner og objekter i nettverket.  
3. **Konfigurer domenet**:  
   - Definer domenenavn, opprett organisasjonsenheter (OUs), og angi gruppepolicyer.  
4. **Bli med datamaskiner i domenet**:  
   - Hver datamaskin som skal være en del av domenet, må kobles til det. Dette kan gjøres under operativsysteminstallasjon eller etterpå.  

---

### Sette opp Brukere, Klienter og Administrator  

#### 1. Opprette en ny bruker  
1. Åpne **Active Directory Users and Computers** i **Server Manager**.  
2. Naviger til domenenavnet ditt i venstre panel, og høyreklikk på **Users**-mappen.  
3. Velg **New** > **User**.  
4. Fyll ut brukerinformasjonen:  
   - **Full name**: Fullt navn på brukeren.  
   - **User logon name**: Brukernavn for pålogging.  
5. Angi et midlertidig passord, og huk av for **User must change password at next logon** (anbefalt for sikkerhet).  
6. Klikk **Next** og deretter **Finish** for å opprette brukeren.  

---

#### 2. Koble en klientmaskin til domenet  
1. Logg inn på klientmaskinen som lokal administrator.  
2. Åpne **System Properties** (høyreklikk på **Denne PC-en** > **Egenskaper**).  
3. Klikk på **Endre innstillinger** under **Datamaskinnavn, domene og arbeidsgruppeinnstillinger**.  
4. Velg **Endre**, og under **Medlem av**, velg **Domene**.  
5. Skriv inn domenenavnet og klikk **OK**.  
6. Når du blir bedt om legitimasjon, skriv inn en administratorkonto for domenet.  
7. Start maskinen på nytt etter vellykket tilkobling.  

---

#### 3. Gi en bruker administratorrettigheter  
1. Åpne **Active Directory Users and Computers**.  
2. Finn brukeren du vil gi administratorrettigheter til.  
3. Høyreklikk på brukeren, og velg **Properties**.  
4. Gå til fanen **Member Of** og klikk **Add**.  
5. Skriv inn **Domain Admins**, og klikk **OK**.  
6. Klikk **Apply**, og deretter **OK** for å lagre endringene.  

---


