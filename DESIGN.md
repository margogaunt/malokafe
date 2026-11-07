# DESIGN.md – Malö kafe

Pravidla vzhledu a chování webu kavárny Malö kafe (výběrová kavárna, snídaně, dorty, dětský koutek; 28. října 106/18, Ostrava).
Vzniklo podle skillu `web-design` a upravuje se podle zpětné vazby. Kód ([styles.css](styles.css), [script.js](script.js)) se řídí tímto souborem.

- **Zadání:** [Malocafe.txt](Malocafe.txt). Úvodní fotka s nadpisem je `head.jpg`, menu v levé části na kraji, animovaná cedulka „hledáme zaměstnance“, která vyskočí po otevření webu.
- **Barvy:** tmavě zelená jako v příspěvcích na IG (křesla, stolky, stěna za barem).
- **Písmo:** podobné nápisu v `head.jpg` (úzké, tenké verzálky s velkým prostrkáním).
- **Úroveň interaktivity:** L2 plynulá (zvoleno 8. 11. 2026). Pořád ale bez věcí ze seznamu „Zakázané“.
- **Recenze:** na webu nejsou (rozhodnutí uživatele, hodnocení na Mapách je 4,3).
- **Fotky:** z uloženého Instagramu, jen snímky bez nápisů.

---

## 1. Atmosféra

Světlá kavárna se šalvějově zelenými stěnami, světlým dřevem a lahvově zelenými křesly. Klidná, vzdušná, „žádný kýč“.

- **Klíčová slova:** lahvová zelená · šalvěj · světlé dřevo · ovesná béžová · úzké verzálky · hodně vzduchu
- **Jednou větou:** „Malö kafe, velké ráno.“
- **Nerozložení klasickým způsobem:** menu je svislý pruh na levém okraji, úvod je čtvercová fotka `head.jpg` s nápisem MALO KAFE a vedle ní krátký text.
- **Motiv dřevěných lišt:** ceník na stěně kavárny je z dřevěných latěk. Na webu se z toho stávají tenké „dřevěné“ linky pod položkami nabídky.

## 2. Barvy

Všechny barvy jsou CSS proměnné v `:root`, v kódu se hex nepíše. K hlavním barvám existuje RGB varianta (`--x-rgb`) pro průhlednost.

| Proměnná | Hex | Role |
|---|---|---|
| `--forest` | #2c4433 | hlavní tmavě zelená: boční menu, úvod, záhlaví, tlačítka |
| `--forest-deep` | #1f3126 | hover tmavých tlačítek, patička |
| `--moss` | #4d6a55 | oddělovače na zelené, aktivní položka menu |
| `--sage` | #93aa98 | barva stěny, vedlejší text na zelené |
| `--sage-light` | #dfe8e0 | světlé plochy (stránka Práce, mapa) |
| `--oat` | #e7ddc9 | cedulka, štítky, plochy jako v IG příspěvcích |
| `--wood` | #c79a69 | dřevěné linky v nabídce, provázek cedulky |
| `--wood-deep` | #8a5f33 | malý zvýrazněný text na světlém (kicker, ceny) |
| `--cream` | #f6f2ea | pozadí stránky |
| `--ink` | #1c2820 | text |
| `--ink-soft` | #4b5a50 | vedlejší text |
| `--white` | #ffffff | text na zelené, rámečky |
| `--open` | #8fd19e | jen tečka „Právě máme otevřeno“ |

**Kontrast:** bílý a ovesný text na `--forest` je čitelný. Na krémové se používá `--ink`, malý barevný text jen `--wood-deep`. `--wood` je jen na linky a dekoraci.

## 3. Typografie

- **Nadpisy:** Oswald 200–500, VERZÁLKY, prostrkání 0,14–0,3 em (podobné nápisu MALO KAFE v `head.jpg`)
- **Text:** Manrope 400–700
- **Načtení:** `https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700&family=Oswald:wght@200..600&display=swap`
- **Záloha:** `"Oswald", "Arial Narrow", sans-serif` / `"Manrope", system-ui, sans-serif`

| Úroveň | Velikost | Řez |
|---|---|---|
| H1 podstránky | clamp(2.8rem, 6.5vw, 5.6rem) | Oswald 300, +0.12em |
| H2 | clamp(2rem, 4.2vw, 3.4rem) | Oswald 300, +0.1em |
| Položka nabídky | clamp(1.15rem, 1.8vw, 1.45rem) | Oswald 400, +0.08em |
| Text | 1rem–1.125rem, řádkování 1.65 | Manrope 400 |
| Kicker | 0.78rem, VERZÁLKY, +0.22em | Manrope 700 |
| Logo „MALÖ / kafe“ | 1.9rem / 0.8rem | Oswald 300, +0.3em / +0.6em |

## 4. Komponenty

- **Logo:** text „MALÖ / kafe“ (Oswald) a za ním (vrstvou pod textem) jejich logo Ö se zrnkem kávy. Soubor `logo-svetle.png` je z `logo.jpg` převedený na ovesnou barvu s průhledností, velikost 118 px, průhlednost 0,32. `logo.jpg` slouží jako ikona záložky.
- **Boční menu (`.rail`):** pevný pruh 248 px na levém okraji, `--forest`, bez okraje, aby splýval s úvodním pásem fotky. Nahoře logo, pod ním odkazy pod sebou (text vodorovně): Úvod, Nabídka, Kontakt. Aktuální stránka má `aria-current="page"`, světlejší podklad `--moss` a dřevěnou linku vlevo. Dole stav otevřeno/zavřeno a Instagram. U „Kontakt“ svítí štítek „hledáme“. **Telefon v menu není.**
- **Tlačítko (`.btn`):** min. výška 48 px, zaoblení 999 px. Plné: `--forest` + bílý text, hover `--forest-deep`. Na zelené: `--oat` + `--ink`, hover bílé. Obrysové: rámeček 1,5 px. Focus: obrys 3 px `--wood`, odsazení 3 px.
- **Úvod (od 8. 11. 2026):** nahoře vodorovný pás čisté fotky `head-bar.jpg` (spodní výřez z `head.jpg` bez nápisu a rámečku: bar s kávovarem, mlýnkem a ceníkem), výška clamp(220px, 38vh, 420px). Levý okraj pásu přechází do zelené menu, spodní se rozplyne do zelené plochy. Pod ním kicker, velký nadpis „MALÖ KAFE“ (Oswald 200, prostrkání 0,3 em jako původní nápis), podnadpis, text, stav a tlačítka, vše na jedné obrazovce. Na mobilu stejný pás, nahoře splývá s lištou. Původní `head.jpg` s nápisem se už nepoužívá. Svislý pás byl zamítnut (uživatelka chtěla vodorovný).
- **Cedulka „Hledáme posilu“ (`.sign`):** jen na úvodní stránce. Ovesná dřevěná cedulka na dvou provázcích vpravo nahoře. Po načtení úvodu spadne shora (1,1 s), 1,5 s visí a pak odjede nahoru. Znovu až po novém načtení úvodu. Když je nad ní myš nebo fokus, počká. Tlačítko vede na `kontakt.html#prace`. Má křížek a tlačítko na `prace.html`. Na stránce Práce se neukazuje. Po zavření zůstane v menu štítek „hledáme“.
- **Ceník kávy:** řádky název – cena s dřevěnou linkou pod každým, jako latě na stěně.
- **Snídaně:** řádek s názvem, složením a cenou, vedle dvě fotky (avo toast, lívanec).
- **Fotky:** zaoblené obdélníky 18–28 px, poměr 4:5, jemný stín.

## 5. Rozvržení

- **Kontejner:** `min(1120px, 100% − 48px)` uvnitř plochy vpravo od menu
- **Svislé mezery sekcí:** clamp(4rem, 9vw, 7.5rem)

| Stránka | Obsah |
|---|---|
| `index.html` | úvod s vodorovným pásem fotky, cedulka, „Co u nás najdete“ (výběrovka, snídaně, sladké, dětský koutek, pivo) |
| `nabidka.html` | zelené záhlaví, ceník kávy, snídaně s cenami a fotkami |
| `kontakt.html` | adresa, telefon, e-mail, otevírací doba se zvýrazněným dneškem, mapa, Navigovat; pod tím sekce `#prace` (dvě pozice a jak se přihlásit) |

Samostatná stránka Práce byla 8. 11. 2026 zrušena, nabídka práce je v Kontaktu.

Patička je stejná na všech stránkách (`--forest-deep`).

## 6. Hloubka a stíny

| Proměnná | Hodnota | Kde |
|---|---|---|
| `--shadow-soft` | `0 18px 40px rgb(ink / .10)` | fotky, mapa |
| `--shadow-sign` | `0 24px 50px rgb(ink / .28)` | cedulka |

## 7. Animace a interakce (L2 plynulá)

| Co | Kde | Jak |
|---|---|---|
| Objevení úvodu | fotka a text | při načtení, fotka se odkryje zdola (clip-path) 1,1 s, text posun 20 px + zprůhlednění |
| Cedulka | jen úvod | po 0,6 s spadne a dohoupe se (1,1 s), 1,5 s visí, odjede nahoru (0,5 s) |
| Pás fotky | úvod | při načtení se odkryje zleva od menu (clip-path 1,2 s), na mobilu shora |
| Objevení sekcí | nadpisy, řádky, fotky | při scrollu, posun 28 px + zprůhlednění 0,8 s, řádky postupně po 60 ms |
| Dřevěné linky | ceník | při objevení se linka natáhne zleva |
| Menu | odkazy | hover: posun textu o 6 px a dřevěná linka |
| Fotky | hover | jemné zesvětlení stínu, bez zvětšování |
| Lišta na mobilu | nahoře | menu se vysune zleva |

**Zakázané:** marquee a běžící pásy, písmena naskakující po jednom, magnet, parallax, světlo pod kurzorem, zvětšování/natáčení fotek, pulzující prvky, nekonečné animace.

**Omezení pohybu:** při `prefers-reduced-motion` se vše vypne a cedulka se jen zobrazí.

## 8. Co dělat a co ne

**Dělat:**
1. Skutečné fotky Malö kafe bez nápisů.
2. Úzké tenké verzálky v nadpisech, hodně vzduchu.
3. Zelenou držet jako hlavní plochu, krémovou pro obsah.
4. Ceny jen ze skutečných podkladů (tabule v `head.jpg`, menu snídaní z IG).
5. Česky, rodově neutrálně, vykat v textu webu (jako na IG „pro Vás“), u inzerátu tykat (jako v inzerátu na IG).
6. Hover i focus u každého prvku, dotyková plocha ≥ 44 px.

**Nedělat:**
1. Žádné vymyšlené ceny, služby ani recenze.
2. Žádné fotky s nápisy (kromě `head.jpg`, která je nadpis).
3. Žádný telefon v menu.
4. Žádné emoji v textu webu.
5. Hex jen v `:root`.
6. Žádná stránka s recenzemi (rozhodnutí 8. 11. 2026).
7. Cedulka nikde jinde než na úvodu a nesmí zůstat viset (8. 11. 2026).
8. Žádná samostatná stránka Práce (8. 11. 2026).
9. Na úvodu žádná fotka s nápisem ani rámečkem a žádný čtverec vpravo (8. 11. 2026).

## 9. Responzivita

| Zlom | Změna |
|---|---|
| ≤ 960 px | menu se schová, nahoře úzká zelená lišta s logem a tlačítkem menu, menu se vysune zleva; úvod v jednom sloupci (fotka nahoře) |
| ≤ 760 px | snídaně: fotky pod seznamem vedle sebe; pozice na stránce Práce pod sebou |
| ≤ 480 px | tlačítka na celou šířku, menší cedulka |

- **Kontrola:** žádný vodorovný scroll na 375 px, otestovat 375 a 1280 px.
