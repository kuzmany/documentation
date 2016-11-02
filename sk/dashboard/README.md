# Dashboard

Mautic 1.4.0 predstavil opraviteľnú dashboard, kde si každý užívateľ môže zostaviť widgety s informáciami, ktoré chce sledovať. Mautic 2.0 predstavil množstvo vylepšení Dashboardu.

## Filter dátového obdobia

Všetky widgety zobrazujú dáta na základe obdobia filtra globálneho dátumu v hornej časti zoznamu widgetov. Štandardné obdobie je nastavené za posledných 30 dní. Linkové grafy zmenia jednotku času automaticky v závislosti na počte zvolených dní v časovom filtri nasledovne:

Dátové obdobie sa rovná 1 dňu: hodiny, 
Dátové obdobie je medzi 1 až 31 dní: dni
Dátové obdobie je 32 až 100 dní: týždne
Dátové obdobie je 101 až 1000 dní: mesiace
Dátové obdobie je väčšie ako 1001 dní: roky
 
Jediná výnimka vo widgetoch, ktoré zobrazujú rovnaké informácie v závislosti na období sú *Nadchádzajúce emaily* a *Posledná aktivita*.

## Widgety

*Varovanie: Nevytvárajte príliš veľa widgetov. Môže to spomaliť dobu natiahnutia stránky widgetov. Ak máte problémy s výkonom, zmenšite počet widgetov.*

Nový widget môže byť pridaný na Vašu dashboard keď kliknete na tlačidlo “Pridaj widget”. Vo formulári “Pridaj widget”, ktoré sa zobrazí po každom widgete budete môcť zadefinovať:

- **Názov**: Popíšte čo widget zobrazuje. Ak to nie je zadefinovaný, Mautic ho nazve rovnaký ako typ widgetu, ktorý ste zvolili.
- **Typ**: Zvoľte aké informácie chcete zobraziť z predefinovaných druhov widgetov.
- **Šírka**: Zvoľte šírku widgetu. Možnosti sú 25%, 50%, 75%, 100%. Predefinovaných je 100%. Optimálna šírka linkových grafov je 100%, pre tabuľky 50% a pre koláčové grafy 25%.
- **Výška**: Každý widget môže mať rôznu výšku. 5 výšok je predefinovaných. Dashboard bude vyzerať najlepšie ak vyberiete rovnakú výšku pre každý widget v riadku.

Niektoré widgety majú ďalšie možnosti:


**História vytvorených kontaktov**
- Ukáž všetky kontakty: Zobrazí jeden riadok so všetkými vytvorenými kontaktmi.
- Len identifikované: Zobrazí jeden riadok s len vytvorenými identifikovanými kontaktmi.
- Len anonymné: Zobrazí jeden radok s len vytvorenými návštevníkmi.
- Všetky identifikované vs. anonymné: zobrazí 2 riadky s vytvorenými identifikovanými kontaktmi a návštevníkmi.
- Top segmenty: Zobrazí až 6 riadkov s kontaktmi, ktoré boli pridelené k top 6 segmentom. Ak takéto segmenty neexistujú pre vybrané obdobie, graf sa nezobrazí.
- Top segmenty s identifikovanými kontaktmi vs. anonymnými: Zobrazí až 6 riadkov top 3 segmentov pre vybrané obdobie. Každý segment zobrazí 2 riadky s identifikovanými kontaktmi a návštevníkmi.


**História emailov**
- Len poslané emaily: zobrazí 1 riadok poslaných emailov.
- Len otvorené emaily: zobrazí 1 riadok otvorených emailov.
- Len zlyhané emaily: zobrazí 1 riadok zlyhaných emailov.
- Poslané a otvorené emaily: zobrazí 2 riadky s poslanými a otvorenými emailami.
- Poslané, otvorené a zlyhané emaily: zobrazí 3 riadky s poslanými, otvorenými a zlyhanými emailami.


**História návštevnosti**
- Celková návštevnosť: zobrazí 1 riadok všetkých návštev (klikov na stránku).
- Unikátne návštevy: zobrazí 1 riadok s unikátnymi návštevami (kontakty).
- Celkové a unikátne návštevy: zobrazí 2 riadky s unikátnymi a všetkými návštevami.


### Zoradenie widgetov

Každý widget môže zmeniť svoje miesto pomocou drag and drop. Prezývka je jeho názov.

## Dashboard export

Každá dashboard môže byť exportovaná do jediného súboru tak, ako ju nakonfigurujete. Môžete tiež urobiť zálohu na neskôr, poslať ju kolegovi, alebo ju zdieľať  on-line. Exportuje sa len konfigurácia widgetov, nie dáta v nich.

## Dashboard import

If you export a dashboard, you can then upload it and import it again in the Dashboard Import page.

Stock Mautic installation comes with 3 pre-defined dashboards. The one called *default.json* is imported automatically, when your dashboard doesn't contain any widget. The other 2 predefined dashboards are there as an example. You can export and import any other dashboard and then switch between them. Pre-defined dashboards can be:

Prezreté v náhľade - Zobrazí dashboard widgetov ako náhľad. Nahrá do nich skutočné Mautic dáta. Nič sa neuloží a ani nezmení stlačením tlačidla Použi. 
Použité - Použije dashboard ako Vašu dashboard. Varovanie: Vaše aktuálne widgety budú týmto zmazané! Exportujte aktuálnu dashboard ak sa ku nej chcete vrátiť neskôr.
Zmazané - Zmaže predefinovanú dashboard.


## Vyrovnávacia pamäť widgetov

WidgetDetailEvent automaticky nahráva podrobné údaje o widgetoch na určitú dobu do vyrovnávacej pamäte, čo sa dá nastaviť v nastaveniach. Prednastavená doba exspirácie vyrovnávacej pamäte je 10 minút.

## Dashboard oprávnenia

Ak Mautic užívateľ nemá oprávnenia, aby videl vlastný zväzok, alebo aby videl oprávnenia iných, užívateľ nebude môcť vytvoriť widgety pre daný zväzok. Avšak widgety sú stále viditeľné na dashboarde daného užívateľa. Napríklad ak užívateľ vytvorí widgety a potom mu administrátor odstráni oprávnenia. V tom prípade sú widgety tam, ale užívateľ vidí len správu, že nemá dostatočné oprávnenia na to, aby ich videl.

Ak má Mautic užívateľ oprávnenia vidieť len vlastné dáta zo zväzku, daný užívateľ uvidí len vlastné dáta vo widgetoch Dashboardu. Napríklad len kontakty, ktoré má, náhľady stránky, ktorú vytvoril, atď.
