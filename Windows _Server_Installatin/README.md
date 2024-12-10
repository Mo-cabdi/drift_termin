
---

# Installer Windows Server 22

**NB**:  
Målgruppen er en middels god VG2-elev ved IM. Derfor vil jeg ikke vise de små stegene. Hvis du sliter med noe, ta kontakt for å få hjelp.

---

## Det du trenger:
- **USB** med minimum 8GB.  
- **Administrator-passord** om du bruker organisasjons-PC-er.

---

## Veiledning

### 1. Start med forberedelser
- Sett inn USB-en i maskinen.  
- **NB**: USB-en bør være tom.  

---

### 2. Last ned Windows Server 22 som ISO
- Følg denne [videoen](https://www.youtube.com/watch?v=jonPNWsXQto) for å installere Windows Server 22 som en `.ISO`-fil, og lag en bootbar USB.  


---

### 3. Boot til menyen
- Slå av maskinen, start den igjen, og trykk på **F10** (eller **Fn + F10** på noen PC-er) for å komme til **BOOT-menyen**.

---

### 4. Deaktiver Secure Boot
- Gå til **Security**, og sjekk at **Secure Boot** er deaktivert.  
  ![Secure Boot Deaktivert](https://github.com/user-attachments/assets/774a7a7e-419f-416f-a4a4-2082c3d876c8)

- På noen PC-er får du en bekreftelsesmelding.  
  - Skriv inn koden maskinen gir deg, og trykk **Enter**.

---

### 5. Endre Boot-rekkefølge
- Gå til **Storage**-menyen, og velg **Boot Order**.  
  ![Boot Order](https://github.com/user-attachments/assets/3a0fc09c-47f6-4fa9-b2bd-e3ef1bb684a8)

- Velg **USB Hard Drive**, trykk **Enter**, flytt den til toppen, og trykk **Enter** igjen.

---

### 6. Lagre endringer
- Trykk **F10** for å akseptere.  
- Gå til **File** og velg **Save changes and exit**.

---

### 7. Fullfør installasjonen
- Start PC-en på nytt.  
- Følg denne [videoen](https://www.youtube.com/watch?v=AQglfvisCG8) for å fullføre installasjonsprosessen:
- 

  

---

### 8. Fjern USB-en
- Når prosessen er ferdig, fjern USB-en.

---

## Gratulerer! 🎉  
Du har installert **Windows Server 22**!

---

This version uses clear sections, headings, and styled lists to make the guide easy to follow. Let me know if you want to adjust anything!
