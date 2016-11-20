## Fronta správ

Keď sa spustí _**marketingový**_ email z kampane, alebo newsletter (segmentové maily) a  keď má kontakt nastavené pravidlo frekvencie, alebo je pravidlo rozosielania nastavené dafultne v Konfigurácii, email môže byť poslaný do fronty na spracovanie.


### Priorita a počet pokusov

![](/contacts/media/marketing-email.png)

- Môžte nastaviť prioritu na Vysokú alebo Normálnu. Pri spracovaní správ budú všetky správy s prioritou vysoká zaradené na začiatok fronty. Emailové rozosielania sa vždy vkladajú ako normálna priorita.
- Podľa počtu pokusov sa bude Mautic snažiť poslať email znova, ak bol jeho dátum odoslania preložený, zapamätajte si, že ak bude email v stave čakajúci na vybavenie, ale množstvo zadaných pokusov už bolo dosiahnute, takáto správa nebude odoslaná.

### Spracovanie fronty správ
Správy sú zaradené do frondy so statusom čakajúce na vybavenie a teda všetky takéto správy, ktoré ešte nedosiahli ich maximálny počet pokusov budú spracované použitím tohto príkazu.

Nastavte si cron nasledovne:

`php app/console mautic:messages:send`
