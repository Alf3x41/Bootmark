# Bootmark 1.5.0

Vlastné boot logo pre podporované UEFI firmvéry.

Bootmark je aplikácia pre Windows, ktorá vyhľadá obrázky v súbore BIOS/UEFI, zobrazí ich náhľad a umožní nahradiť podporovaný obrázok vlastným logom. Súbory spracúva lokálne.

## Požiadavky

- Windows 11, 64-bitová verzia.
- .NET Framework 4.8 s WPF.
- Súbor firmvéru pre presný model a revíziu zariadenia.

## Inštalácia a spustenie

Spustite `Bootmark-Setup-1.5.0.exe` alebo `setup.exe` a postupujte podľa pokynov. Inštalátor umožňuje vytvoriť odkaz na pracovnej ploche.

Prenosnú verziu rozbaľte z `Bootmark-portable.zip` a spustite `Bootmark.App.exe`. Ponechajte pri nej sprievodné licencie a oznámenia. Odinštalovanie nainštalovanej verzie je dostupné v nastaveniach aplikácií Windows; používateľské údaje zostávajú zachované.

## Ako zmeniť logo

1. Uchovajte si pôvodný súbor BIOSu.
2. Otvorte firmvér v Bootmarku alebo ho presuňte do okna aplikácie.
3. Vyberte nájdený obrázok a skontrolujte jeho náhľad.
4. Načítajte vlastný PNG, JPG alebo BMP, prípadne vytvorte textové logo v Creatore.
5. Skontrolujte rozmery, kompozíciu a nastavenie orezania.
6. Uložte upravený firmvér do nového súboru.

Tlačidlo **Stiahnuť BIOS** otvára oficiálne stránky výrobcov. Model, revíziu dosky a vhodnú verziu firmvéru overte na stránke výrobcu. Internet je potrebný na otvorenie týchto stránok.

## Creator

Creator vytvára textové logá s priebežným náhľadom. Môžete meniť text, písmo, veľkosť, farbu a tučné písmo. Pozadie je čierne. Logo môžete použiť v aplikácii alebo uložiť ako PNG.

Odporúčané rozmery vychádzajú z vybraného obrázka vo firmvéri. Pre logo určené do BIOSu najprv načítajte firmvér a vyberte obrázok.

Súčasťou aktuálnej zostavy sú **Goldman**, **Monocraft** a **Ethnocentric Regular**. Ethnocentric Italic nie je súčasťou výberu ani balíka. Dostupné sú aj podporované systémové písma. Voliteľný Arcend sa načíta zo systému alebo zo súboru `%LOCALAPPDATA%\Bootmark\UserFonts\Arcend.ttf`; nie je pribalený.

Goldman a Monocraft majú priložené licencie SIL OFL. Ethnocentric sa riadi samostatnou licenciou svojho autora; licencia Bootmarku neudeľuje práva k tomuto písmu. K dodanému OTF nebola v projekte priložená jeho pôvodná licencia. Pred ďalšou distribúciou balíka s týmto písmom treba doložiť oprávnenie na jeho vloženie do aplikácie.

## Podpora a obmedzenia

Podpora závisí od štruktúry firmvéru. Samotná prípona súboru ani značka dosky nezaručujú možnosť úpravy.

- Aplikácia vyhľadáva podporované JPEG, PNG a BMP obrázky v UEFI.
- Export vyžaduje podporovaný kontajner a úspešné kontroly štruktúry.
- Pri rozpoznanej podpísanej kapsule alebo chránenej oblasti môže byť export zablokovaný.
- Nie každý nájdený grafický zdroj je boot logo.
- Bootmark nevykonáva flashovanie a neupravuje digitálne podpisy výrobcu.

Pri exporte aplikácia kontroluje okrem iného objemy, kontrolné súčty, pozície ostatných súborov a spätne extrahovaný obrázok. Úspešné kontroly nezaručujú prijatie firmvéru zariadením ani úspešné spustenie.

**Úprava a flashovanie firmvéru môžu spôsobiť stratu dát alebo nefunkčnosť zariadenia. Uchovajte pôvodný BIOS a riaďte sa postupom výrobcu zariadenia.**

## Jazyk a vzhľad

V nastaveniach môžete zmeniť jazyk a farebnú tému. Aplikácia podporuje 17 jazykov a témy Obsidián, Perla, Les a Pomaranč. Jazyk a téma sa ukladajú.

## Licencia

Bootmark je proprietárny softvér. Podmienky používania sú v `LICENSE.txt`. Zdrojový kód sa neposkytuje ako súčasť distribučného balíka.

