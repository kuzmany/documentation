# Prehľad kontaktov

Každý kontakt má stránku s podrobnosťami, kde môžete vidieť, čo vie Mautic o danom užívateľovi.

## Zapájanie sa/Bodovacia schéma

Čiarový graf zapájania sa zobrazuje ako veľmi aktívny bol daný kontakt za posledných 6 mesiacov. Zapojenie sa je akákoľvek aktivita, ktorú daný kontakt vykonal, napr. kliknutie na stránku, podanie formulára, otvorenie emailu, atď. Graf zobrazuje aj body, ktoré daný kontakt obdržal.

## Avatar

Mautic sa bude snažiť stiahnuť obrázok avatara daného užívateľa na základe jeho/jej emailovej adresy zo služby [Gravatar](https://en.gravatar.com/). Avšak môže byť stiahnutý aj zo sociálnych sietí.

## História

Hlavná tabuľka zobrazuje históriu aktivít daného užívateľa od najnovšej po najstaršiu. Pri každej aktivite sa zobrazí toľko podrobností, koľko o nej je. Napríklad podanie formulára zobrazí aké hodnoty kontakt zadal, aktivita poslania emailu bude informovať o tom, či bol email otvorený, kedy, atď. Prostredníctvom filtra aktivít môžete v danom období zahrnúť aktivity, ktoré chcete, a vyradiť tie, ktoré nechcete, ak hľadáte konkrétnu aktivitu.

## Poznámky

Mautic môže byť použitý ako základný CRM. Vy alebo Vaši kolegovia môžu písať poznámky ku konkrétnemu kontaktu. Poznámka môže byť označená konkrétnym účelom: obecná, email, telefonát, porada. Je tiež možné zadefinovať dátum stretnutia alebo telefonátu. Ak tak urobíte, poznámka sa objaví aj v Mautic kalendári.

## Sociálne

Ak sú aktivované a autorizované sociálne pluginy ako Facebook alebo Twitter a daný kontakt Vám poskytol užívateľské meno pre sociálnu sieť, Mautic dokáže zobraziť jeho/jej kanál na sociálnej sieti na Sociálnej lište. Väčšina sociálnych sietí obmedzila svoje API, od kedy bola táto funkcia vyvinutá, takže vyhľadávanie na základe emailov nefunguje.

## Mapa

Ak Mautic pozná koordináty kontaktu prostredníctvom služby geolokácie IP, zobrazí štvrtú lištu s mapou, takže môžete jednoducho vidieť, kde na svete sa kontakt nachádza. Ak Mautic pozná viac polôh tohto kontaktu ako kontakt cestuje, uvidíte tu všetky polohy. Ak Mautic nepozná žiadnu polohu, lišta sa nezobrazí.

## Zmeniť segmenty kontaktov
![](/contacts/media/change-segments.jpg)

Kliknite na drop down šípku v pravom hornom rohu podrobností kontaktu. Vyberte *Segmenty*. Zobrazí sa modálna tabuľka, kde uvidíte všetky segmenty. Zelený prepínač znamená, že kontakt patrí do segmentu, oranžový prepínač znamená opak. Kliknite na prepínač, aby ste pridali/odstránili kontakt k/zo segmentu.

## Zmeniť kampane kontaktov

Kliknite na drop down šípku v pravom hornom rohu podrobností kontaktu. Vyberte *Kampane*. Zobrazí sa modálna tabuľka, kde uvidíte všetky kampane. Zelený prepínač znamená, že kontakt patrí do kampane, oranžový prepínač znamená opak. Kliknite na prepínač, aby ste pridali/odstránili kontakt k/z kampane.

## Zlučiť dva kontakty

Ak máte v Mautic databáze 2 kontakty, ktoré sú fyzicky jednou osobou, môžete ich zlúčiť prostredníctvom funkcie Zlúčenia. Kliknite na drop down šípku v pravom hornom rohu podrobností kontaktu, vyberte *Zlúčiť* položku, zobrazí sa modálna tabuľka. Vyhľadajte kontakt, ktorý chcete zlúčiť s aktuálnym kontaktom. Zvolená položka sa počas hľadania aktualizuje. Zvoľte správny kontakt a stlačte tlačidlo *Zlúčiť*.

## Poslať email kontaktu

Drop down menu v pravom hornom rohu podrobností kontaktu tiež umožňuje poslať email priamo kontaktu. Môžete zdať *Meno odosielateľa*, *od* (emailovú adresu), *Predmet* a *Telo správy*. Môžete tiež *Importovať z existujúcej predlohy*. Ak si z tejto ponuky vyberiete nejaký email, Predmet a Telo správy už budú vyplnené z danej predefinovanej emailovej predlohy. Emaily posielané touto metódou nie sú sledované Mauticom.
