# Bootmark Simple

**Vlastné boot logo pre podporované UEFI firmvéry.**

Bootmark Simple je offline aplikácia pre Windows, ktorá vyhľadá obrázky vo firmvéri, zobrazí ich náhľad a umožní nahradiť podporovaný obrázok vlastným logom.

**Verzia:** 1.4 · **Systém:** Windows 11 x64 · **Licencia:** proprietárna

> [!WARNING]
> Úprava a následné flashovanie firmvéru môžu spôsobiť nefunkčnosť zariadenia. Uchovajte si pôvodný BIOS a overte presný model aj revíziu dosky. Bootmark nevykonáva flashovanie a nezaručuje kompatibilitu výsledného súboru so zariadením.

## Obsah

- [Funkcie](#funkcie)
- [Inštalácia](#inštalácia)
- [Použitie](#použitie)
- [Tvorba vlastného loga](#tvorba-vlastného-loga)
- [Podpora firmvérov](#podpora-firmvérov)
- [Overené súbory](#overené-súbory)
- [Jazyky a vzhľad](#jazyky-a-vzhľad)
- [Licencia a komponenty tretích strán](#licencia-a-komponenty-tretích-strán)

## Funkcie

- Vyhľadávanie obrázkov v UEFI vrátane komprimovaných vnorených objemov.
- Náhľad pôvodného obrázka a výber z viacerých nálezov.
- Import vlastného loga vo formáte PNG, JPG alebo BMP.
- Automatické prevzatie odporúčaných rozmerov a výstupného formátu.
- Zachovanie pomeru strán, čierne pozadie a voliteľné orezanie prázdnych okrajov.
- Vstavaný editor textových log s priebežným náhľadom a exportom PNG.
- Kontroly štruktúry firmvéru pred uložením aj po úprave.
- Odkazy na oficiálne stránky výrobcov na stiahnutie BIOSu.
- 17 jazykov, štyri farebné témy a uloženie nastavení.

## Inštalácia

### Požiadavky

- Windows 11, 64-bitová verzia.
- .NET Framework 4.8 a WPF.

### Inštalátor

Spustite `setup.exe` alebo `BootmarkSetup-1.4.exe` a postupujte podľa pokynov. Inštalátor podporuje aktualizáciu predchádzajúcej inštalácie a zachováva používateľské súbory.

## Použitie

1. Spustite Bootmark.
2. Vyberte súbor firmvéru alebo ho presuňte do okna aplikácie.
3. Zo zoznamu nájdených obrázkov vyberte ten, ktorý chcete upraviť. Pred výberom nového loga sa zobrazuje pôvodný obrázok.
4. Načítajte vlastný PNG, JPG alebo BMP, prípadne vytvorte textové logo. Skontrolujte náhľad a nastavenie orezania.
5. Uložte upravený firmvér do nového súboru.

Pôvodný súbor sa neprepíše a výstup si zachová jeho príponu. Pri exporte sa nevytvára sprievodný report.

### Získanie BIOSu

Tlačidlo **Stiahnuť BIOS** otvorí výber výrobcu s rozpoznaným modelom počítača alebo dosky. Dostupné sú oficiálne centrá podpory GIGABYTE, ASUS, MSI, ASRock, Dell, HP, Lenovo a Acer.

Presný model, revíziu a verziu firmvéru vyberte na stránke výrobcu. Stiahnutý archív rozbaľte a výsledný súbor otvorte v Bootmarku.

## Tvorba vlastného loga

Editor **Creator** otvoríte tlačidlom napravo od výberu obrázka. Umožňuje nastaviť text, písmo, veľkosť, tučné písmo a farbu textu. Pozadie zostáva čierne.

Rozmery sa preberajú z vybraného obrázka vo firmvéri. Bez načítaného BIOSu editor používa rozmer **1024 × 300 px**; pre správne odporúčané rozmery najprv načítajte firmvér.

Logo môžete použiť priamo alebo uložiť ako PNG. Pri použití loga s rovnakými rozmermi sa zachová kompozícia a automatické orezanie sa vypne. Zrušenie editora nemení logo v hlavnom okne.

### Písma

Pribalené písma **Goldman** a **Monocraft** fungujú offline bez systémovej inštalácie. Dostupné sú aj podporované systémové písma, napríklad Impact, Georgia, Consolas, Comic Sans MS a Segoe Script.

Písmo **Arcend** sa nepribaľuje. Ak máte oprávnenie ho používať, aplikácia ho načíta zo systému alebo zo súboru `%LOCALAPPDATA%\Bootmark\UserFonts\Arcend.ttf`.

## Podpora firmvérov

O podpore rozhoduje obsah a štruktúra súboru, nie jeho prípona ani zoznam konkrétnych dosiek.

| Oblasť | Podpora |
| --- | --- |
| Vyhľadávanie | Rozbalený strom UEFI, vnorené komprimované objemy a doplnkové fyzické PI FFS2/FFS3 objemy |
| Obrázky | JPEG, PNG a nekomprimovaný BMP so 40-bajtovou DIB hlavičkou, 1/4/8/24/32 bitov |
| Export | Samostatné raw/freeform obrázky s jednoznačným FFS kontajnerom |
| Rozpoznané kapsuly a chránené oblasti | Vyhľadávanie a náhľad; export je zablokovaný |
| Nerozpoznané alebo šifrované kontajnery | Odmietnuté |

Pri neznámom GUID aplikácia označí nález ako grafický zdroj. Nemusí ísť o boot logo. Obrázky v neznámych proprietárnych formátoch alebo uprostred spustiteľného kódu nemusia byť rozpoznané.

### Kontroly exportu

Pri exporte sa overujú:

- rovnaká veľkosť objemu a platné kontrolné súčty FV/FFS;
- nezmenené pozície a obsah ostatných FFS súborov;
- zhoda spätne extrahovaného obrázka s vloženým logom;
- štruktúra rozbaleného stromu a nezmenené bajty mimo upraveného objemu.

Ak je upravený kontajner menší, voľné miesto sa vyplní štandardným FFS PAD súborom. Ak sa väčší kontajner nezmestí bez posunutia iných súborov, export sa odmietne.

> [!IMPORTANT]
> Detekcia ochrany nie je úplná a nenahrádza autentifikáciu výrobcu. Aplikácia neupravuje podpisy. Úspešné softvérové overenie samo osebe nepotvrdzuje, že zariadenie upravený firmvér prijme alebo s ním nabootuje.

## Overené súbory

| Doska alebo súbor | Výsledok | Overenie na zariadení |
| --- | --- | --- |
| Gigabyte A520M K V2 rev. 1.1, FFa | Logo TITAN, JPEG 809 × 116 | Používateľ potvrdil prijatie Q-Flashom a úspešné bootovanie |
| `H81S2PV3.F2` | 4 obrázky; hlavný BMP 809 × 116; export SCOUT prešiel extrakciou a opätovným otvorením | Netestované |
| `ROG-STRIX-Z890-F-GAMING-WIFI-ASUS-3401.CAP` | 113 obrázkov; hlavné logo 672 × 378; podpísaná kapsula, export zablokovaný | Netestované |

Lokálny sken trval približne 2,4 s pri H81 a 7,2 s pri Z890. Časy závisia od hardvéru. Automatické testy zahŕňajú aj syntetické PI objemy, rôzne GUID a obrázky JPEG/PNG/BMP. Ostatné dosky neboli hardvérovo overené.

## Jazyky a vzhľad

Aplikácia a inštalátor podporujú 17 jazykov:

English, Slovenčina, Čeština, Deutsch, Français, Español, Italiano, Português, Polski, Magyar, Nederlands, Türkçe, Українська, Русский, 简体中文, 日本語, 한국어.

Predvolený jazyk sa vyberá podľa Windows; pri nepodporovanom jazyku sa použije angličtina. Jazyk aplikácie môžete zmeniť bez reštartu. Niektoré technické diagnostické správy môžu zostať v pôvodnom jazyku.

Nastavenia otvoríte ikonou ozubeného kolieska. K dispozícii sú témy **Obsidián**, **Perla**, **Les** a **Pomaranč**. Téma a jazyk sa ukladajú; zmena témy nemení obrazové dáta loga.

## Licencia a komponenty tretích strán

**Bootmark je proprietárny softvér a nie je open source.** Produkt sa distribuuje iba v skompilovanej forme ako aplikácia alebo EXE inštalátor so sprievodnými licenciami. Zdrojový kód sa neposkytuje. Podmienky používania upravuje [LICENSE.txt](LICENSE.txt).

Bootmark používa nasledujúce komponenty tretích strán, ktoré si zachovávajú vlastné licencie:

| Komponent | Použitie | Licencia |
| --- | --- | --- |
| LongSoft UEFIExtract A75 a UEFIReplace 0.28 z projektu UEFITool | Spracovanie UEFI firmvéru | [BSD, 2 podmienky](docs/UEFITool-LICENSE.md) |
| Goldman | Pribalené písmo | [SIL Open Font License](docs/fonts/Goldman-OFL.txt) |
| Monocraft | Pribalené písmo | [SIL Open Font License](docs/fonts/Monocraft-OFL.txt) |

Licenčné texty tretích strán sú súčasťou distribučného balíka. Proprietárna licencia Bootmarku nemení práva udelené licenciami týchto komponentov.
