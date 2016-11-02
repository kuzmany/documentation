# Začíname

Super! Stiahli ste si nástroj pre zautomatizovanie marketingu. Je to skvelý začiatok, ale teraz určite rozmýšľate čo a ako ďalej. Postupujte podľa tohto jednoduchého návodu, aby ste mohli začať používať svoju prekrásnu novú hračku!

## Krok 1: Nainštalujte Mautic

Ak ste už stiahli zip súbor z príslušnej stránky, alebo už máte Mautic nainštalovaný z iného zdroja (Softaculous, Bitnami, Digital Ocean atď.) potom ste už vykonali prvý krok. Ak nie, potom musíte nahrať Mautic balík (zip súbor) na Váš server, rozbaliť súbory a potom prejsť na dané miesto vo Vašom prehľadávači. Objavíte, že Mautic má veľmi jednoduchý proces inštalácie, pri ktorej len postupujete podľa pokynov na obrazovke.

## Krok 2: Pridajte cron úlohy

Keď ste nainštalovali Mautic, budete musieť vytvoriť pár štandardných cron úloh aby Váš softvér mohol spracúvať rôzne úlohu. Tieto cron úlohy môžu byť vytvorené prostredníctvom cPanelu, alebo pridané cez príkazový riadok. Ak nepoznáte alebo si netrúfate na tento krok, potom Vám odporúčame opýtať sa na fórach alebo na Slack živom chate. Tu je zoznam cron úloh, ktoré musíte vytvoriť.

**Aktualizácia segmentov**

`php /path/to/mautic/app/console mautic:segments:update`

**Aktualizácia kampaní**

`php /path/to/mautic/app/console mautic:campaigns:rebuild`

**Vykonanie príkazov kampane**

`php /path/to/mautic/app/console mautic:campaigns:trigger`

Prezrite si [Cron úlohy](./../setup/cron_jobs.html) pre viac informácií o týchto a ďalších dostupných cron úlohách.
.

## Krok 3: Stiahnite si servisnú databázu IP lookup

Štandardne inštaluje Mautic súbory pre použitie bezplatnej MaxMind GeoLite2 IP lookup databázy. Z dôvodu licenčného viazania databázy nemôže byť zahrnutá v inštalačnom balíku Mauticu a musí byť siahnutá. Kliknite na ozubené koliesko v pravom hornom rohu Mauticu pre zobrazenie Admin menu, potom kliknite na Konfiguráciu. Na lište nastavení systému sa posuňte dole k nastaveniam služby IP lookup a kliknite na “stiahni dátové úložisko IP Lookup."

Môžete si tiež vybrať iným podporovanú IP lookup službu ak Vám vyhovuje.

## Krok 4: Inštalujte sledovací JavaScript

Po inštalácií a nastavení cron úloh môžete začať sledovať kontakty. Budete musieť pridať jednoduchý JavaScript na každú webstránku, ktorú budete chcieť sledovať prostredníctvom Mauticu. Je to veľmi jednoduchý proces a tento sledovací script môžete pridať do súboru Vašej web stránky, alebo môžete inštalovať Mautic integráciu pre bežnejšie CMS platformy. Tu je príklad sledovacieho javascriptu:

``` <script> (function(w,d,t,u,n,a,m){w['MauticTrackingObject']=n; w[n]=w[n]||function(){(w[n].q=w[n].q||[]).push(arguments)},a=d.createElement(t), m=d.getElementsByTagName(t)[0];a.async=1;a.src=u;m.parentNode.insertBefore(a,m) })(window,document,'script','http(s)://yourmautic.com/mtc.js','mt'); mt('send', 'pageview'); </script> ``` 

Budete musieť zmeniť URL stránky (nahraďte yourmautic.com Vašou vlastnou URL) vo vyššie uvedenom skripte.

Pozrite si [Kontaktujte Monitoring](./../contacts/contact_monitoring.html) pre viac informácií.
