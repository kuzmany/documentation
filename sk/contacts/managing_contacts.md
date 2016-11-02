# Správa kontaktov

Stránka správcu kontaktov je hlavným rozhraním, prostredníctvom ktorého si môžete prezerať a komunikovať s Vašimi kontaktmi – ako návštevníkmi, tak aj bežnými kontaktmi.

## Segmenty

Segmenty sú prednastaveným tabuľkovým zobrazením všetkých kontaktov v systéme – prednastavené je **zobrazenie v tabuľke**, ale môžete tiež prepnúť na **zobrazenie v kartičkách** (tiež známe ako **zobrazenie v mriežke**), ktoré používa avatary pre vizuálne zobrazenie kontaktov prostredníctvom kartičiek. Kliknutie na príslušné tlačidlo hore vpravo Vám umožní prepnúť medzi obomi náhľadmi.

Tip: Ak preferujete použitie klávesových skratiek, môžete stlačiť “t“ na Vašej klávesnici pre dynamické prepnutie na tabuľkový náhľad a “c“ pre zobrazenie kartičiek.

## Vyhľadávanie kontaktov

Segmenty môžu byť prehľadávané použitím políčka v hornej časti zoznamu, a môžu byť zoradené prostredníctvom záhlavia tabuľky tým, že kliknete na záhlavie, na základe ktorého chcete zoradiť zoznam. 

![](/contacts/media/contacts-search.jpg)

Políčko vyhľadávania umožňuje rôzne typy vyhľadávania a funguje na rovnakom procese vyhľadávania a premenných, aký je možné nájsť vo všetkých ostatných hľadaniach. O možnostiach vyhľadávania sa môžete dozvedieť viac na stránke s dokumentáciou o vyhľadávaní.

## Rýchle pridanie kontaktov

Ak máte kontakty, ktoré by ste chceli rýchlo manuálne pridať do Mauticu, a dané kontakty nie sú súčasťou systému v rámci bežného workflow (napr. Vyplnením dotazníka alebo importovaním), môžete použiť tlačidlo rýchleho pridania kontaktu, aby ste ich pridali do systému.

Môžete ich pridať aj prostredníctvom formulára nových kontaktov a tým pridať množstvo detailov, ale rýchle zadanie je najjednoduchším a najrýchlejším spôsobom zapísania kontaktov do systému.

## Pridanie kontaktov bežným spôsobom

Ak máte kontakty, ktoré chcete importovať, a máte čas vyplniť všetky informácie, kliknite no šípku dropdown menu napravo od 'rýchleho pridania kontaktu ', a vyberte 'nové '. To otvorí obrazovku nového kontaktu, kde môžete zadať všetky informácie, ktoré o kontakte máte. Použite lišty v hornej časti pre pridanie špecifických polí a profilov zo sociálnych sietí.

## Importovanie kontaktov

Mautic ponúka možnosť importu kontaktov z iných zdrojov prostredníctvom CSV súboru - je to skvelý spôsob ako rýchlo začať, ak potrebujete naraz importovať veľké množstvo kontaktov.

Pred samotným importom sa uistite, že máte všetky polia nastavené pod 'správou polí ', čo zodpovedá informáciám, ktoré importujete – ak je to možné, nechcete prísť o žiadne dáta.

Keď ste už vytvorili všetky polia kontaktov, kliknite na dropdown šípku vpravo od tlačidla rýchleho pridania kontaktov a vyberte 'Import'.

Nahrajte svoj CSV súbor a uistite sa, že symboly pre oddelenie, uzavretie a únik sú zadefinované správne, aby importér pochopil dáta.

Keď kliknete na 'Nahrať', budete mať možnosť skontrolovať, či sa polia v CSV súbore súhlasia s poľami v Mauticu, čo zaručí, že dáta budú nahrané korektne.

Nasledujúce hodnoty budú mať pri importovaní logickú hodnotu: `1 `, `pravdivé `, `zapnuté ` a `áno `. Tieto hodnoty môžu byť kapitalizované a stále budú brané za PRAVDIVÉ. Akákoľvek iná hodnota bude uložená ako NEPRAVDIVÁ.

## Editovanie kontaktov
Pre editovanie kontaktu kliknite na meno kontaktu (alebo IP adresu návštevníka, ak je anonymný) pre otvorenie okna kontaktu.

V tomto okne si môžete pozrieť aktuálne udalosti a akékoľvek poznámky, ktoré boli urobené pre daný kontakt.

Pre editovanie kontaktu kliknite na “edit” tlačidlo v menu v pravo hore.

## Zdvojené kontakty

Keď Mautic sleduje aktivitu kontaktu, ako napr. Kliknutie na stránku alebo vyplnenie formulára, automaticky zlúči kontakty unikátnymi identifikátormi, ktoré sú:
- IP adresa
- Email (alebo iné kontaktné pole, ktoré označíte ako unikátny identifikátor)
- Cookie

Ak Mautic pozná len IP adresu, priradí konanie kontaktu (kliknutie na stránku, vyplnenie formulára, atď.) s kontaktom s rovnakou IP adresou. Ak IP adresa ešte neexistuje v Mautic databáze, vytvorí nový kontakt. Ale ak Mautic pozná unikátny cookie, spojí konanie s kontaktom, prostredníctvom toho istého cookie, alebo vytvorí nový.

Ak kontakt pošle formulár s emailovou adresou, spojí tento formulár s kontaktom s rovnakou emailovou adresou. Aj keď sa IP adresa alebo cookie zhodujú s iným kontaktom.

Takže Mautic sa postará o zdvojené kontakty vytvorené sledovaním udalostí. Avšak stále môžete vytvoriť zdvojený kontakt prostredníctvom správy Mauticu. Od verzie 2.1.0 budete upozornený, ak už existuje kontakt s rovnakým unikátnym identifikátorom.
