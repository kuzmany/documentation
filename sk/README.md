# Dokumentácia systému Mautic

### Úvod
Táto príručka slúži ako [dokumentácia pre Mautic](https://www.mautic.org/docs/index.html), systém pre automatický marketing s otvoreným zdrojovým kódov. Dokumentácia je dostupná s otvorenými zdrojovým kódom a každý môže vylepšiť tieto informácie.

### Stiahnite ako PDF

[Kliknite sem](https://mautic.org/docs/mautic_docs_en.pdf) pre stiahnutie tejto príručky ako PDF.

### Ako prispieť k dokumentácii

Táto príručka je vytvorená s nástrojom [Gitbook](https://www.gitbook.com/) a je zverejnená na [www.mautic.org/docs](https://www.mautic.org/docs/index.html). Zdrojový kód je zdieľaný na GitHube, takže ktokoľvek môže prispieť k dokumentácii rovnakým spôsobom, ako programátori prispievajú k Mautic kódu. 

#### Prečo je na dokumentáciu použitý git

- *verziovateľnosť*. Každý si môže pozrieť históriu a pozrieť si, ako vyzeral text pred úpravou.
- *autorstvo*. Nielen každý súbor, ale aj každý riadok má svojho autora.
- *prispievanie komunity*. Nemusíte sa báť, že zmažete prácu niekoho iného, zatiaľ čo pracujete na tom istom dokumente.

Aj keď práca s gitom vyžaduje znalosti príkazov ako klonovanie, upravenie, potvrdenie a zverejnenie zmien, existuje spôsob ako sa tomu vyhnúť, a upravovať súbory priamo cez GitHub web rozhranie. Ak ovládate git, workflow môžete použiť ako len chcete. Ak nie, postupujte podľa týchto inštrukcií aby ste mohli jednoducho prispieť.

#### Úprava dokumentov v prehliadači

1. [Uložte](https://github.com/mautic/documentation#fork-destination-box) si túto príručku pod Váš účet aby ste boli oprávanený ju upravovať.
2. Vyberte si súbor na úpravu. Štruktúra súborov je vysvetlená nižšie. Teraz upravte *README.md* súbor, aby sme si vysvetlili základy. Kliknite naň.
3. Obsah *README.md* by mal byť editovateľný pomocou tlačidla úpravy (ikona s ceruzkou). Kliknite naň.
4. Obsh je písaný v [Markdowne](https://daringfireball.net/projects/markdown/). Ide o jednoduché formátovanie textu.
5. Urobte zmeny v súbore. Napríklad napíšte na koniec `Toto je môj prvý príspevok`.
6. Keď ste vykonali zmeny, posuňte sa dole a nájdite formulku *Zadať zmeny*. Toto je dôležité. Aby ste uložili zmeny, musíte popísať čo ste zmenili a prečo. Napíšte napríklad `Pridaný riadok na účely testovania`.  Toto ešte neukladajte!
7. Pretože GitHub webové rozhranie neposkytuje všetky funkcie gitu, nemáme jednoduchý spôsob ako vrátiť zmeny do pôvodného stavu. Museli by zmeniť zadaný riadok a znova zadať zmeny, a to by urobilo neporiadok v histórii zmien. Takže namiesto toho urobíme novú vetvu. Existuje na to políčko “Vytvor novú vetvu…”. Vetva musí mať názov. {vašeuživateľskémeno}-patch-1 bude ponúkané štandardne. Zmeňme to na {vašeuživateľskémeno}-testing. Kliknite na *Navrhni zmenu súboru* teraz.
8. OK, takže zmena existuje vo Vašich zdrojoch. Aby ste navrhli zmenu v oficiálnych zdrojoch, musíte poslať žiadosť o publikovanie (Pull Request). Budete tam presmerovaní. Tu popíšete navrhované zmeny a kliknete (prosíme neposielajte testovacie PR) na tlačidlo *Vytvor Pull Request*.

Ak si chcete po tomto teste upratať, choďte do sekcie *Vetví* (Branch) a zmažte testovaciu vetvu.

#### Štruktúra súborov

V predchádzajúcej časti sme pracovali s *README.md* súborom. Tento súbor je zobrazený na domovskej stránke GitHug a práve teraz čítate jeho obsah. S dokumentáciou o Mauticu nemá nič spoločné.

*SUMMARY.md* súbor definuje obsah dokumentácie. Ak pridáte nové stránky do dokumentácie, musíte tiež pridať nové riadky definujúce názov a odkaz na súbor. Je to celkom jednoduché  uvdiíte aktuálne položky v menu.

Priečinky existujú aby zoskupili témy. Otvorte napríklad priečinok *Asset*. Uvidíte, že má vlastný *README.md* súbor. Je to hlavný obsah, keď kliknite na menu *Asset*. *manage_assets.md* súbor je podpoložkou. Podpriečinok *médií* obsahuje všetky obrázky použité v *md* súboroch.

#### Odkazy

Často chcete odkázať na iné miesto v dokumentácii použitím odkazu. V Markdowne vyzerá odkaz takto:

```
[názov odkazu](http://example.com)
```

To vytvorí externý odkaz s absolútnou URL. Ak chcete vytvoriť interná odkaz, požite relatívnu URL takto:

```
[tieto kroky](./../plugins/integration_test.html)
```
Tento odkaz na `plugins/integration_test.html ` na stránke dokumentácie bol vytvorený zo zdrojového md súboru.

#### Obrázky

Ako je uvedené vyššie, obrázky môžu byť uložené v podpriečinkoch médií. Pravdepodobne nie je možné nahrať obrázky prostredníctvom webového rozhrania GitHubu, ale môžete ich nahrať na akúkoľvek verejnú URL a odkázať na nich.

```
![alternatívny text sem](http://example.com/images/apple.png "Text nástroja sem")
```
Alebo ak by ste chceli zobraziť obrázok už nahraný v zdrojoch dokumentácie, môžete použiť relatívnu cestu:
```
![alternatívny text sem](/assets/media/assets-newcategory.png "Text nástroja sem")
```
