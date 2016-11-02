# Kontakty

Vodidlá boli premenované na kontakty vo verzii Mautic 1.4.0.

Kontakty sú stredobodom platformy automatického marketingu. Sú to jednotlivci, ktorí navštívili Vašu stránku alebo nejakým spôsobom boli s Vami v kontakte. 

### Typy kontaktov

Existujú dva druhy kontaktov:
* **Návštevníci** (predtým anonymné vodidlá) — návštevníci Vašej stránky, ktorí ešte neboli identifikovaní formulárom alebo inou interakciou. 
  * Tieto kontakty sú sledované Mauticom, ale typicky sú skryté aby nezahltili Váš segment.
* **Štandardné kontakty** - kontakty, ktoré sa identifikovali prostredníctvom formulára alebo prostredníctvom iného zdroja. Preto majú kontakty typicky meno, email a iné identifikačné políčka.


#### Návštevníci (predtým anonymné vodidlá)

Anonymné vodidlá boli v Mauticu 1.4.0 premenované na návštevníkov

Návštevníkov si môžete prezrieť použitím tabuľkového náhľadu (použite “t” skratku na klávesnici aby ste si pozreli kontakty v tabuľke alebo “c” ako kartičky) v sekcii kontaktov. 

Návštevníci stoja za to, aby boli sledovaní, pretože to môžu byť budúci zákazníci. Tým, že ich budete sledovať ešte pred tým, ako s nimi budete komunikovať, môžete si vytvoriť záznam, kedy navštívili Vašu webstránku, čo Vám umožňuje vytvoriť si obraz o ich aktivite ešte pred tým, ako Vás kontaktujú.

##### Hľadať text

```
is:anonymous
```
##### Screenshoty

![](/contacts/media/contacts-anonymous.jpg)
Výsledný zoznam bude obsahovať IP adresy, ktoré ešte neposkytli identifikačné informácie.

#### Štandardné kontakty

Druhým typom kontaktov sú štandardné kontakty. Tieto kontakty sa identifikovali prostredníctvom formulára alebo použitím iného zdroja - môžete mať o nich ďalšie informácie z predchádzajúcich interakcií. V dôsledku toho majú kontakty typicky meno, email a iné identifikačné informácie, ktoré môžu byť asociované s kontaktom.

Štandardný kontakt je preferovaným kontaktom v Mauticu. Sú to kontakty, ktoré možno začali ako návštevníci, ale potom poskytli dodatočné informácie ako meno, emailovú adresu, prezývku na sociálnej siete, alebo iné identifikátory. O tieto kontakty sa môžete starať prostredníctvom platformy automatického marketingu Mautic.

Časť [Správa kontaktov](https://www.mautic.org/docs/en/contacts/managing_contacts.html) poskytuje viac informácií o tom, čo môžete robiť so štandardnými kontaktmi.
