# Sledovanie kontaktov
Sledovanie prenosu dát a aktivity kontaktov môže byť niekedy príliš technické a frustrujúce na pochopenie. Mautic robí toto sledovanie jednoduché a ľahko nastaviteľné.

## Sledovanie webstránky

Sledovanie  prenosu dát na webstránke môže byť zrealizované nahraním javascrip súboru (od verzie 1.4) alebo pridaním sledovacieho pixelu na webstránku. Je treba poznamenať, že aktivita prihlásených Mautic užívateľov nebude sledované. Na prekontrolovanie toho, či JS/pixel funguje, použite inkognito alebo súkromné okno v prehliadači, alebo jednoducho sa odhláste z Mauticu pred tým, ako ho otestujete.

### Sledovanie prostredníctvom javascriptu (JS)

Sledovanie prostredníctvom JS bolo implementované vo verzii 1.4 a odporúča sa ako hlavný spôsob sledovania webstránky. Aby ste ho implementovali, choďte v mautiku do *Mautic nastavenia* > *nastavenia vstupnej stránky* aby ste našli sledovací JS kód napísaný pre vašu Mautic inštanciu, a vložte kód pred ukončujúci `<body/> ` tag webstránky, ktorú chcete sledovať. Alebo prekopírujte nižšie uvedený kód a zmeňte URL na Vašu inštanciu Mauticu.

```
<script>
    (function(w,d,t,u,n,a,m){w['MauticTrackingObject']=n;
        w[n]=w[n]||function(){(w[n].q=w[n].q||[]).push(arguments)},a=d.createElement(t),
        m=d.getElementsByTagName(t)[0];a.async=1;a.src=u;m.parentNode.insertBefore(a,m)
    })(window,document,'script','http(s)://yourmautic.com/mtc.js','mt');

    mt('send', 'pageview');
</script>
```

_Nezabudnite zmeniť schému (http(s)) buď na http alebo https v závislosti od toho, akú schému používate pre váš Mautic. Rovnako zmeňte [yourmautic.com] na doménu, kde beží váš Mautic._

Výhodou JS sledovania je, že žiadosť o sledovanie, ktorej môže trvať dlho, pokým sa nahrá, sa nahráva asynchrónne, takže nespomalí sledovanú stránku. JS tiež umožňuje automaticky sledovať viacero informácií:

- **Názov stránky** je text napísaný medzi `</title>` tagmi.
- **Jazyk stránky** je jazyk definovaný v browseri.
- **Odkazovač stránky** je URL, z ktorej kontakt prišiel na aktuálnu webstránku.
- **URL stránky** je URL aktuálnej webstránky.


#### mt() Udalosti

Od verzie 2.2.0, mt() podporuje dva callbacky: `onload` a `onerror` akceptované ako štvrtý argument. `Onload` metóda bude vykonaná akonáhle sa nahraje sledovací pixel. Ak z nejakého dôvodu pixel zlyhá, vykoná sa `onerror`.
```
mt('send', 'pageview', {}, {
    onload: function() {
        redirect();
    },
    onerror: function() {
        redirect();
    }
});
```

#### Cookie miestneho kontaktu

Od verzie 2.2.0, ak CORS je nakonfigurovaný, aby umožnil prístup z domény, kde je mtc.js vložený, cookie s názvom `mtc_id` bude vložený na tú istú doménu. Tento cookie bude mať hodnotu ID pre aktuálne sledovaný kontakt. To poskytuje prístup na softvér na strane serveru k ID kontaktu a tým poskytuje možnosť integrovať sa aj s REST API Mauticu.

#### Sledovanie osobitých parametrov

Môžete pripojiť osobité parametre alebo prepísať automaticky vygenerované parametre aktivity pageview rovnako ako tomu je u žiadosti sledovacieho pixlu. Aby ste to dosiahli, zaktualizujte posledný riadok vyššie uvedeného JS kódu takto:

```
    mt('send', 'pageview', {email: 'my@email.com', firstname: 'John'});

```
Tento kód pošle všetky automatické dáta do Mauticu a pridá tiež email a meno. Hodnoty týchto polí musia byť vygenerované Vašim systémom.

#### Nahranie udalosti

Počas toho, ako je žiadosť JS o sledovanie nahrávaná asynchrónne, môžete požiadať JS aby zavolal funkciu, keď je žiadosť nahrávaná. Aby ste to dosiahli, definujte *onload* funkciu v nastaveniach takto:

```
    mt('send', 'pageview', {email: 'my@email.com', firstname: 'John'}, {onload: function() { alert("Tracking request is loaded"); }});

```

#### Odtlačok prsta (beta funkcia)

Mautic 1.4.0 je dodávaný so sledovacou funkciou nazvanou Odtlačok prsta. Bola použitá knižnica [Fingerprint2](https://github.com/Valve/fingerprintjs2). Mala by fungovať spolu s, alebo nahradiť aktuálne sledovacie identifikátory ako IP adresa a/alebo cookie ID. Táto metóda ešte nie je hlboko implementovaná v systéme, ale už teraz môžete vidieť viac informácií na stránke s históriou udalostí v detailoch o kontakte:

- **Odtlačok prsta** - unikátny hash vypočítaný z nastavení browsera a iných premenných prostredia.
- **Rozlíšenie** - s x výškou rozlíšenia displeja zariadenia,
- **Posun časového pásma** - množstvo minút, plus alebo mínus v porovnaní s UTC.
- **Platforma** - platforma zariadenia. Obvykle OS a architektúra procesora.
- **Adblock** - logická hodnota, či kontakt používa plugin blokujúci reklamu v prehliadači
- **Nesledovať** - logická hodnota, či je zapnutá funkcia nesledovať.

Ak chcete uložiť ktorúkoľvek z vyššie uvedených hodnôt do detailov kontaktu, vytvorte nové osobité pole, nazvite ho presne ako je nazvané vo vyššie uvedenom zozname a urobte pole verejne aktualizovateľným. Môžete sa tiež pokúsiť urobiť pole Odtlačku prsta unikátny a týmto spôsobom môžete simulovať budúce sledovanie odtlačku prsta. Avšak nie je to ešte otestovaná funkcia. Nepoužívajte ju v produkcii, ak ste ju najprv neotestovali.

### Sledovanie sledovacím pixelom

Táto metóda je sekundárna od verzie 1.4.
```
http://yourdomain.com/mtracking.gif
```

#### Dotazovanie sledovacieho pixelu

Aby ste zo sledovacieho pixelu vyťažili čo možno najviac, odporúča sa preposlať informácie o webovej požiadavke cez URL obrázka.

#### Informácie o stránke

Mautic aktuálne podporuje `page_url`, `referrer`, `language`, a `page_title` (všimnite si, že použitie `url` a `title` sú zamietnuté v dôsledku konfliktu s poľami kontaktu).

### UTM Kódy 

Podpora UTM kódov v histórii kontaktu bola predstavená vo verzii 1.2.1. `utm_medium`, `utm_source`, a `utm_campaign` sú používané na generovanie záznamu v histórii.

`utm_campaign` bude použitý ako názov záznamu v histórii.

`utm_medium` hodnoty sú zmapované do nasledujúcich tried Font Awesome:

 
<table>
<thead>
<tr>
    <th>Hodnoty</th>
    <th>Trieda</th>
</tr>
</thead>
<tbody>
   <tr><td>sociálne, sociálne médiá</td><td>fa-share-alt ak <code>utm_source</code> nie je dostupný, inak bude ako trieda použitý <code>utm_source</code> Napr., ak <code>utm_source</code> is Twitter, použije sa fa-twitter.</td></tr>
   <tr><td>email, newsletter</td><td>fa-envelope-o</td></tr>
   <tr><td>banner, ad</td><td>fa-bullseye</td></tr>
   <tr><td>cpc</td><td>fa-money</td></tr>
   <tr><td>location</td><td>fa-map-marker</td></tr>
   <tr><td>device</td><td>fa-tablet ak <code>utm_source</code> nie je dostupný, inak bude ako trieda použitý <code>utm_source</code> Napr., ak <code>utm_source</code> is Mobile, použije sa fa-mobile.</td></tr>   
</tbody>
</table>


#### Vloženie pixelu

Ak používate CMS, najjednoduchšie je nechať jedne z našich pluginov, aby to urobil za Vás (viď nižšie). Všimnite si, že pluginy nemusia podporovať všetky polia kontaktu, utm kódy alebo tagy kontaktu.

Tu je pár útržkov kódu, ktoré Vám môžu pomôcť:

HTML

```
<img src="http://yourdomain.com/mtracking.gif?page_url=http%3a%2f%2fyourdomain.com%2fyour-product-page&page_title=Some%20Cool%20Product&email=user%40theirdomain.com&tags=ProductA,-ProductB" style="display: none;"  alt="mautic is open source marketing automation" />
```

PHP

```
$d = urlencode(base64_encode(serialize(array(
    'page_url'   => 'http://' . $_SERVER[HTTP_HOST] . $_SERVER['REQUEST_URI'],
    'page_title' => $pageTitle,    // Use your website's means of retrieving the title or manually insert it
    'email' => $loggedInUsersEmail // Use your website's means of user management to retrieve the email
))));

echo '<img src="http://your-mautic.com/mtracking.gif?d=' . $d . '" style="display: none;" />';
```

Javascript

```
<script>
var mauticUrl = 'http://your-mautic.com';
var src = mauticUrl + '/mtracking.gif?page_url=' + encodeURIComponent(window.location.href) + '&page_title=' + encodeURIComponent(document.title);
var img = document.createElement('img');
img.style.width  = '1px';
img.style.height  = '1px';
img.style.display = 'none';
img.src = src;
var body = document.getElementsByTagName('body')[0];
body.appendChild(img);
</script>
```

### Polia kontaktu

Informácie špecifické pre Váš kontakt môžete posunúť tým, že polia kontaktu v Mauticu nastavíte tak, aby boli verejne aktualizovateľné. Všimnite si, že hodnoty priradené k sledovaciemu pixelu by mali byť URL kódované (%20 pre medzery, %40 pre @, atď.).

### Tagy

Tagy kontaktu sa môžu zmeniť použitím parametrov dotazovania sa na `tagy`. Jednotlivé tagy môžu byť oddelené čiarkou. Ak chcete odstrániť tag, dajte pred neho čiarku (mínus).

Napríklad, `mtracking.gif?tags=ProductA,-ProductB` by bolo pridanie tagu ProductA ku kontaktu a odstránenie ProductB.

### Dostupné pluginy

Mautic to zjednodušuje tým, že poskytuje kľúčové integrácie do mnohých existujúcich systémov správy obsahu. Môžete stiahnuť a používať ktorýkoľvek z nasledujúcich pluginov aby ste automaticky pridali sledovací pixel na Vašu webstránku.

* [Joomla!](http://mautic.org/integration/joomla)
* [Drupal](http://mautic.org/integration/drupal)
* [WordPress](http://mautic.org/integration/wordpress)
* [Typo3](http://mautic.org/integration/typo3)
* [Concrete5](http://mautic.org/integration/concrete5)
* [Grav](https://github.com/mautic/mautic-grav)

Je to len malá ukážka integrácií už vytvorených Mautic komunitou. Ďalšie budú pridané v budúcnosti a developeri sú povzbudzovaní aby podali svoje vlastné integrácie.

**Poznámka:** Je dôležité poznamenať, že nie ste obmedzení týmito pluginmi, a že sledovací pixel môžete umiestniť priamo na akúkoľvek HTML stránku pre jej sledovanie.

### Mobilné sledovanie

Základom sledovania toho, čo sa v Appke deje sa podobá sledovaniu toho, čo sa deje na webstránke. Mautic obsahuje stavebné bloky potrebné pre natívne (alebo pseudonatívne) a HTML5 Appky, bez ohľadu na platformu.

V skratke povedané, použite pomenované náhľady obrazoviek (napr. hlavná obrazovka) vo Vašej Appke ako Vaše page_url pole v trackeri, a email kontaktu ako unikátny identifikátor. Viď nasledujúcu časť pre podrobnejšie pokyny.

#### Kroky v Mauticu

1. Spravte emailové pole verejne editovateľným. To znamená, že volanie sledovacieho GIF  v premennom emaili bude správne rozoznané Mauticom.

2. Vytvorte formulár, ktorý bude vstupným bodom Vašej kampane (napr. nový kontaktný email). Urobte tento formulár tak jednoduchý, ako je to len možné, keďže ho budete zverejňovať z vašej Appky. Typická forma URL na ktorú budete odkazovať je:

```
http://your_mautic/form/submit?formId=<form_id>
```

ID môžete získať s URL Mauticu ako si prezeráte/editujete formulár v rozhraní Mauticu (alebo v tabuľkách formulárov, posledný stĺpec), a polia formulára môžete získať pozretím sa na HTML “manuálnej kópie” na stránke editovania formulárov.

3. Vo svojej kampani definujte obrazovky, ktoré chcete použiť ako spúšťače (napr. 'obrazovka s nákupným košíkom ', atď.). Mautic sa nepozerá na skutočnú URL vo formulári 'http://<url>' pre page_url, postačí akýkoľvek typický reťazec, napr.:

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

#### Vo vašej Appke

Najlepší možný prístup je mať triedu (napr. 'mautic '), ktorá zabezpečuje všetky vaše sledovacie potreby. V tomto príklade by daná metóda volania zverejnila formulár s ID3 - viď predchádzajúcu časť (poznámka: pre stručnosť a všadeprítomnosť sú tieto ukážky kódu napísané v Javascripte / ECMAScript-type jazyku, použite podobné volanie v jazyku Vašej mobilnej Appky).

```
mautic.addContact("myemail@somehwere.com",3)
```

A potom aby ste sledovali aktivitu užívateľa v Appke, táto ukážka volania by vytvorila HTTP požiadavku na tracker:

```
mautic.track("cart_screen", "myemail@somewhere.com")
```

Čo nie je o nič viac, ako HTTP požiadavka pre túto GET-formátovanú URL (ako je tiež ukázané v predchádzajúcej časti):

```
http://yourdomain.com/mtracking.gif?page_url=cart_screen&email=myemail@somewhere.com
```

Dôležité: Uistite sa vo svojej Appke, že vyššie uvedená HTTP žiadosť používa cookie (ak je to možné, znova použite cookie z predchádzajúcej mautic.addcontact POST žiadosti), a že tento cookie použijete znova od jednej žiadosti k nasledujúcej. Takto Mautic (a iný sledovací softvér) vie, že sa v skutočnosti jedná o toho istého užívateľa. Ak to nedokážete urobiť, môže sa stať (nepravdepodobné ale možné), že skončíte s mnohými kontaktmi z tej istej IP adresy a Mautic ich zlúči do jediného kontaktu, pretože bez cookie nevie povedať kto je kto.

### Iné online sledovanie

Existuje niekoľko iných spôsobov ako sledovať aktivitu kontaktu a priradiť body týmto aktivitám. Sledovanie webstránky je len jedným zo spôsobov sledovania kontaktov. Iné aktivity sledovania kontaktu môžu pozostávať z príspevkov na fórach, správ v chatovacích miestnostiach, diskusných príspevkov na konferenciách, GitHub/Bitbucket správach, podaniach kódu, príspevkov na sociálnych médiách a mnohých iných možnostiach.

### Riešenie problémov

Ak sledovanie nefunguje, pozrite sa na [Riešeia problémov so stránkami](./../pages/troubleshooting.html) alebo [Riešenia problémo s emailami](./../emails/troubleshooting.html)
