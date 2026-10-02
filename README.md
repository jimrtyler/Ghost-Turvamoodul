# 👻 Ghost Turvamoodul
**PowerShell-Põhine Windows & Azure Turvakõvendamine**

> **Ennetav turvakõvendamine Windows lõpp-punktide ja Azure keskkondade jaoks.** Ghost pakub PowerShell-põhiseid kõvendamisfunktsioone, mis aitavad vähendada levinud rünnakuvektoreid, keelates mittevajalikud teenused ja protokollid.

## ⚠️ Olulised Lahtiütlused

**TESTIMINE NÕUTAV**: Testke Ghost alati esmalt mitte-tootmiskeskkondades. Teenuste keelamine võib mõjutada õigustatud ärifunktsioone.

**GARANTIID PUUDUVAD**: Kuigi Ghost sihtib levinud rünnakuvektoreid, ei saa ükski turvatööriist takistada kõiki rünnakuid. See on üks osa terviklikust turvastrateegist.

**TÖÖMÕJU**: Mõned funktsioonid võivad mõjutada süsteemi funktsionaalsust. Vaadake iga seade hoolikalt üle enne juurutamist.

**PROFESSIONAALNE HINNANG**: Tootmiskeskkondade jaoks konsulteerige turvaekspertidega, et tagada seadete kooskõla teie organisatsiooni vajadustega.

## 📊 Turvamaastik

Lunavara kahjud ulatusid **57 miljardi dollarini 2025. aastal**, kusjuures uuringud näitavad, et paljud edukad rünnakud kasutavad ära Windows-i põhiteenuseid ja valekonfiguratsioone. Levinud rünnakuvektorid hõlmavad:

- **90% lunavara juhtumeid** hõlmab RDP ärakasutamist
- **SMBv1 haavatavused** võimaldasid rünnakuid nagu WannaCry ja NotPetya
- **Dokumendimakrod** jäävad peamiseks pahavara kohaletoimetamise meetodiks
- **USB-põhised rünnakud** jätkavad õhupiluga võrkude sihtimist
- **PowerShell kuritarvitamine** on viimastel aastatel märkimisväärselt kasvanud

## 🛡️ Ghost Turvafunktsioonid

Ghost pakub **16 Windows kõvendamisfunktsiooni** pluss **Azure turvaintegratsioon**:

### Windows Lõpp-punkti Kõvendamine

| Funktsioon | Eesmärk | Kaalutlused |
|------------|---------|-------------|
| `Set-RDP` | Haldab kaugtöölaua juurdepääsu | Võib mõjutada kaughaldust |
| `Set-SMBv1` | Kontrollib vana SMB protokolli | Vajalik väga vanadele süsteemidele |
| `Set-AutoRun` | Kontrollib AutoPlay/AutoRun | Võib mõjutada kasutajamugavust |
| `Set-USBStorage` | Piirab USB-salvestusseadmeid | Võib mõjutada õigustatud USB kasutamist |
| `Set-Macros` | Kontrollib Office makro täitmist | Võib mõjutada makrodega dokumente |
| `Set-PSRemoting` | Haldab PowerShell kaugjuhtimist | Võib mõjutada kaughaldust |
| `Set-WinRM` | Kontrollib Windows kaughaldust | Võib mõjutada kaughaldust |
| `Set-LLMNR` | Haldab nimeulatusprotokolli | Tavaliselt ohutu keelata |
| `Set-NetBIOS` | Kontrollib NetBIOS TCP/IP-s | Võib mõjutada pärandrakendusi |
| `Set-AdminShares` | Haldab haldusressursse | Võib mõjutada kaugfaili juurdepääsu |
| `Set-Telemetry` | Kontrollib andmete kogumist | Võib mõjutada diagnostika võimeid |
| `Set-GuestAccount` | Haldab külaliskontot | Tavaliselt ohutu keelata |
| `Set-ICMP` | Kontrollib ping vastuseid | Võib mõjutada võrgudiagnostikat |
| `Set-RemoteAssistance` | Haldab kaugabi | Võib mõjutada tehnilise toe töötamist |
| `Set-NetworkDiscovery` | Kontrollib võrgu avastamist | Võib mõjutada võrgu sirvimist |
| `Set-Firewall` | Haldab Windows tulemüüri | Kriitiline võrguturvalisuse jaoks |

### Azure Pilve Turvalisus

| Funktsioon | Eesmärk | Nõuded |
|------------|---------|--------|
| `Set-AzureSecurityDefaults` | Võimaldab Azure AD põhiturvalisust | Microsoft Graph load |
| `Set-AzureConditionalAccess` | Konfigureerib juurdepääsupoliitikaid | Azure AD P1/P2 litsentsid |
| `Set-AzurePrivilegedUsers` | Auditeerib privileegitud kontosid | Globaalse administraatori load |

### Ettevõtte Juurutamise Valikud

| Meetod | Kasutusala | Nõuded |
|--------|------------|--------|
| **Otsene Täitmine** | Testimine, väikesed keskkonnad | Kohalikud administraatori õigused |
| **Group Policy** | Domeeni keskkonnad | Domeeni administraator, GP haldus |
| **Microsoft Intune** | Pilves hallatavad seadmed | Intune litsentsid, Graph API |

## 🚀 Kiire Alustamine

### Turvaanalüüs
```powershell
# Laadi Ghost moodul
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Kontrolli praegust turvapositsiooni
Get-Ghost
```

### Põhiline Kõvendamine (Testi Esmalt)
```powershell
# Oluline kõvendamine - testi esmalt laboratooriumikeskkonnas
Set-Ghost -SMBv1 -AutoRun -Macros

# Vaata muudatusi üle
Get-Ghost
```

### Ettevõtte Juurutamine
```powershell
# Group Policy juurutamine (domeeni keskkonnad)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune juurutamine (pilves hallatavad seadmed)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Paigaldamise Meetodid

### Valik 1: Otsene Allalaadimine (Testimine)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### Valik 2: Mooduli Paigaldamine
```powershell
# Paigalda PowerShell Gallery-st (kui saadaval)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Valik 3: Ettevõtte Juurutamine
```powershell
# Kopeeri võrguasukohta Group Policy juurutamiseks
# Konfigureeri Intune PowerShell skriptid pilve juurutamiseks
```

## 💼 Kasutusala Näited

### Väike Ettevõte
```powershell
# Põhiline kaitse minimaalse mõjuga
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Tervishoiu Keskkond
```powershell
# HIPAA-keskne kõvendamine
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Finantsteenused
```powershell
# Kõrge turvalisuse konfiguratsioon
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Pilv-Esmane Organisatsioon
```powershell
# Intune-hallatav juurutamine
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 📝 Funktsiooni Üksikasjad

### Põhilised Kõvendamisfunktsioonid

#### Võrguteenused
- **RDP**: Blokeerib kaugtöölaua juurdepääsu või randomiseerib pordi
- **SMBv1**: Keelab vana failijagamise protokolli
- **ICMP**: Takistab ping vastuseid luuramiseks
- **LLMNR/NetBIOS**: Blokeerib vana nimeulatuse protokollid

#### Rakenduste Turvalisus
- **Makrod**: Keelab makro täitmise Office rakendustes
- **AutoRun**: Takistab automaatset täitmist eemaldatavalt meediumilt

#### Kaughaldus
- **PSRemoting**: Keelab PowerShell kaugsessioone
- **WinRM**: Peatab Windows kaughalduse
- **Kaugabi**: Blokeerib kaugabi ühendused

#### Juurdepääsu Kontroll
- **Admin Shares**: Keelab C$, ADMIN$ ressursid
- **Külaliskonto**: Keelab külalise juurdepääsu
- **USB Salvestus**: Piirab USB-seadmete kasutamist

### Azure Integratsioon
```powershell
# Ühendu Azure rentnikuga
Connect-AzureGhost -Interactive

# Võimalda turvavaikimisi
Set-AzureSecurityDefaults -Enable

# Konfigureeri tingimuslik juurdepääs
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Auditeeri privileegitud kasutajaid
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune Integratsioon (Uus v2-s)
```powershell
# Ühendu Intune-ga
Connect-IntuneGhost -Interactive

# Juuruta Intune poliitikate kaudu
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Olulised Kaalutlused

### Testimise Nõuded
- **Laboratooriumikeskkond**: Testi kõik seaded esmalt isoleeritud keskkonnas
- **Järkjärguline Juurutamine**: Juuruta järk-järgult probleemide tuvastamiseks
- **Tagasipöördumise Plaan**: Veendu, et saad muudatusi vajadusel tagasi pöörata
- **Dokumenteerimine**: Salvesta, millised seaded töötavad sinu keskkonnas

### Potentsiaalne Mõju
- **Kasutaja Produktiivsus**: Mõned seaded võivad mõjutada igapäevaseid töövoogusid
- **Pärandrakendused**: Vanemad süsteemid võivad vajada teatud protokolle
- **Kaugjuurdepääs**: Kaaluta mõju õigustatud kaughaldusele
- **Äriprotsessid**: Veendu, et seaded ei riku kriitilisi funktsioone

### Turvalisuse Piirangud
- **Sügav Kaitse**: Ghost on üks turvakirde, mitte täielik lahendus
- **Jätkuv Haldus**: Turvalisus nõuab pidevat jälgimist ja uuendusi
- **Kasutaja Koolitus**: Tehnilised kontrollid peavad käima koos turvaeteadlikkusega
- **Ohtude Areng**: Uued rünnakumeetodid võivad praegust kaitset mööda hiilida

## 🎯 Näidis Rünnaku Stsenaariumid

Kuigi Ghost sihtib levinud rünnakuvektoreid, sõltub konkreetne ennetamine õigest juurutamisest ja testimisest:

### WannaCry-laadsed Rünnakud
- **Maandamine**: `Set-Ghost -SMBv1` keelab haavatava protokolli
- **Kaalutlus**: Veendu, et ükski pärandsüsteem ei vaja SMBv1

### RDP-põhine Lunavara
- **Maandamine**: `Set-Ghost -RDP` blokeerib kaugtöölaua juurdepääsu
- **Kaalutlus**: Võib vajada alternatiivseid kaugjuurdepääsu meetodeid

### Dokumendi-põhine Pahavara
- **Maandamine**: `Set-Ghost -Macros` keelab makro täitmise
- **Kaalutlus**: Võib mõjutada õigustatud makrodega dokumente

### USB-tarnitud Ohud
- **Maandamine**: `Set-Ghost -USBStorage -AutoRun` piirab USB funktsionaalsust
- **Kaalutlus**: Võib mõjutada õigustatud USB-seadmete kasutamist

## 🏢 Ettevõtte Funktsioonid

### Group Policy Tugi
```powershell
# Rakenda seaded Group Policy registri kaudu
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Seaded rakenduvad domeeniüleses pärast GP värskendust
gpupdate /force
```

### Microsoft Intune Integratsioon
```powershell
# Loo Intune poliitikad Ghost seadete jaoks
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Poliitikad juurutatakse hallatavates seadmetes automaatselt
```

### Vastavuse Raportid
```powershell
# Genereeri turvaanalüüsi raport
Get-Ghost | Export-Csv -Path "TurvaAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure turvapositsiooni raport
Get-AzureGhost | Out-File "AzureTurvaRaport.txt"
```

## 📚 Parimad Tavad

### Eel-juurutamine
1. **Dokumenteeri Praegust Olukorda**: Käivita `Get-Ghost` enne muudatusi
2. **Testi Põhjalikult**: Valideeri mitte-tootmiskeskkonnas
3. **Planeeri Tagasipöördumine**: Tea, kuidas iga seadet tagasi pöörata
4. **Sidusrühmade Ülevaatus**: Veendu, et äriüksused kiidavad muudatused heaks

### Juurutamise Ajal
1. **Järkjärguline Lähenemine**: Juuruta esmalt pilootrühmadesse
2. **Jälgi Mõju**: Jälgi kasutajate kaebusi või süsteemiprobleeme
3. **Dokumenteeri Probleemid**: Salvesta kõik probleemid tulevase viite jaoks
4. **Teata Muudatustest**: Informeeri kasutajaid turvaparandustest

### Pärast Juurutamist
1. **Regulaarne Hindamine**: Käivita perioodiliselt `Get-Ghost` seadete kontrollimiseks
2. **Uuenda Dokumentatsiooni**: Hoia turvakonfiguratsioonid ajakohasena
3. **Hinda Efektiivsust**: Jälgi turvaohtuintsidente
4. **Pidev Parandamine**: Kohenda seadeid ohtumaastiku põhjal

## 🔧 Veaotsing

### Levinud Probleemid
- **Loa Vead**: Veendu, et PowerShell sessioon on administraatori õigustega
- **Teenuse Sõltuvused**: Mõnel teenusel võivad olla sõltuvused
- **Rakenduse Ühilduvus**: Testi ärirakenduste osas
- **Võrguühenduvus**: Kontrolli, et kaugjuurdepääs ikka töötab

### Taastamise Valikud
```powershell
# Taasaktiveeri konkreetsed teenused vajadusel
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 Autori Kohta

**Jim Tyler** - Microsoft MVP PowerShell jaoks
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10 000+ tellimust)
- **Uudiskiri**: [PowerShell.News](https://powershell.news) - Iganädalane turvaanalüütika
- **Autor**: "PowerShell for Systems Engineers"
- **Kogemus**: Aastakümnete PowerShell automatiseerimise ja Windows turvalisuse kogemus

## 📄 Litsents & Lahtiütlus

### MIT Litsents
Ghost on saadaval MIT litsentsi all vabaks kasutamiseks, muutmiseks ja levitamiseks.

### Turvalisuse Lahtiütlus
- **Garantii Puudub**: Ghost on saadaval "nagu on" ilma igasuguse garantiita
- **Testimine Nõutav**: Testi alati esmalt mitte-tootmiskeskkondades
- **Professionaalne Juhendamine**: Konsulteeri turvaekspertidega tootmisjuurutuste jaoks
- **Töömõju**: Autorid ei vastuta töökatkestuste eest
- **Terviklik Turvalisus**: Ghost on üks osa täielikust turvastrateegist

### Tugi
- **GitHub Issues**: [Raporteeri vead või palu funktsionaalsusi](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentatsioon**: Kasuta `Get-Help <funktsioon> -Full` detailse abi jaoks
- **Kogukond**: PowerShell ja turvakogukonna foorumid

---

**🔒 Tugevda oma turvapositsiooni Ghost-iga - aga testi alati esmalt.**

```powershell
# Alusta hindamisega, mitte oletustega
Get-Ghost
```

**⭐ Anna sellele hoidlale täht, kui Ghost aitab parandada sinu turvapositsiooni!**