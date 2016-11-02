Správa segmentov
===============

Zoznmy vodítok boli premenované na segmenty vo verzii Mautic 1.4.0.

Segmenty poskytujú spôsoby ako jednoducho zorganizovať Vaše kontakty. Tieto segmenty môžu byť nakonfigurované z rôznych polí..

Keď si prezeráte všetky segmenty, všimnite si stĺpec napravo, ktorý ukazuje počet kontaktov, ktorý zodpovedá danému segmentu.

![](/contacts/media/contact-segments.jpg)

### Filtre segmentov

![](/contacts/media/segment-filters.jpg)

Tieto filtre tiež môžu byť nakombinované, aby boli zahŕňajúce alebo vylučujúce v závislosti na Vašich potrebách.

![](/contacts/media/multiple-segment-filters.jpg)

Keď ste si vybrali pole, môžete si vybrať typ operácie, ktorá sa má vykonať. Tieto sa líšia v závislosti od toho, ako chcete filtrovať svoje kontakty.

![](/contacts/media/segment-filters-dropdown.jpg)

Ak chcete rozdeliť segmenty na základe určitých kritérií, a nechcete (sub)segmentom posielať duplicitné emaily, môžete si ich prezrieť a upraviť napísaním aliasu mena kontaktných segmentov, oddelených len “+“. Kontaktné segmenty môžete pridať aby boli spoločné, ale vždy dostanete len výsledok prieniku podskupín. Potom môžete manipulovať s kontaktmi aby ste ich odstránili z konkrétnych podskupín alebo zo všetkých. Týmto sa vyhnete duplicitným emailom na rovnaké vodítka v podskupinách.

![](/contacts/media/common-leads-in-segments.jpg)

### Segmenty

Keď ste už vytvorili segmenty, akékoľvek použiteľné kontakty budú automaticky pridané vykonaním cron úlohy. To je podstata segmentov.
Aby boli segmenty aktuálne, vytvorte cron úlohu, ktorá vykonáva nasledovný príkaz v požadovaných intervaloch:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
php /path/to/mautic/app/console mautic:segments:update --env=prod
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Vykonaním tohto príkazu budú kontakty, ktoré zodpovedajú filtru pridané a kontakty, ktoré už nezodpovedajú filtru vyradené. Akékoľvek kontakty, ktoré boli manuálne pridané ostanú súčasťou zoznamu bez ohľadu na filtre.

### Manuálne pridanie

Okrem segmentov môžete manuálne pridať akýkoľvek kontakt do zoznamu kliknutím tlačidla Segmentov, a následne vybraním rádiového prepínača v pohľade na detaily kontaktov.
