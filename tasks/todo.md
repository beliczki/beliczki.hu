# Footer ikonok + Grafia szekció – 2026-11-11

## 1. A lap alján nem látszanak a social ikonok

**Gyökérok:** az `index.html` a `https://unpkg.com/lucide@latest` címről tölti a Lucide-ot, verzió nélkül. A Lucide 1.0.1 (2026-03-23) kivette a márkaikonokat (github, linkedin, twitter). Azóta a `<i data-lucide="github">` stb. üres marad, csak a JSFiddle (`code`) ikon jelenik meg. Az élő oldalon is így van. Most a `@latest` az 1.72.0-s verziót adja.

- Kis javítás: `lucide@1.0.0` rögzítése (ez az utolsó, amiben még benne vannak). Ezzel viszont egy régi verzión ragadunk, és a következő frissítésnél ugyanez a hiba visszajön.
- **Alapos javítás (ezt javaslom):** a mechanizmust zárja le.
  - [ ] A Lucide-ot pontos verzióra rögzítem (`lucide@1.72.0`), így a `@latest` többé nem tudja csendben eltörni a hold/nap/nyíl/projekt ikonokat.
  - [ ] A három márkaikon inline SVG-ként kerül a footerbe. A Lucide 0.577.0 saját rajzait használom (ISC licenc), így ugyanaz a vonalstílus marad. A meglévő `.social-links svg` szabály méretezi őket, új CSS nem kell.

## 2. Grafia szekció

Forrás (csak olvasás): `~/grafia/index.html` és `~/grafia/assets/grafia-eye.png`. Ugyanez a szöveg és szem él a grafia.hu-n.

- [ ] Új fejlécsor „Grafia” címmel (a meglévő `.projects-header` mintájára), alatta egy kártyasor a `.project-card` mintájára. Helye: a bemutatkozás után, a Projects előtt.
- [ ] Ikon: a Grafia-szem 45 fokban, -45°-ra forgatva, úgy, ahogy a grafia.hu-n beáll (animáció nélkül), a 40 px-es ikonhelyen.
  - A `grafia-eye.png`-nek fehér, nem átlátszó háttere van, ami sötét témában fehér dobozként látszana. Ezért készítek belőle egy átlátszó maszkváltozatot (`assets/grafia-eye.png`), és CSS-maszkkal színezem.
  - Alapértelmezés: kék, mint a többi projektikon. Kérésre lehet a márka fekete színe is, ami sötét témában fehér lesz.
- [ ] Cím: „Grafia Studio”. Szöveg a grafia repóból szó szerint: „2nd generation family business, keen on adding value to the economy through personal connections and original projects”.
- [ ] Gomb a meglévő `project-link` stílussal → https://grafia.hu
- [ ] Ellenőrzés: asztali és 375 px, világos és sötét téma, a footer ikonokkal együtt.

Élesítés (Plesk, kézzel): `index.html`, `style.css`, `assets/grafia-eye.png`. Commit és feltöltés csak Robi go-jára.

## Review

Robi jóváhagyta (kék szem). Mind a két rész elkészült, helyben ellenőrizve.

- A Lucide az 1.72.0-ra van rögzítve. A három márkaikon inline SVG, az útvonalakat gépi összevetéssel ellenőriztem a lucide-static 0.577.0 eredetijeivel. Mind a négy footer ikon látszik.
- A Grafia szekció a Projects előtt van, a meglévő fejléc- és kártyaosztályokkal. Új CSS csak a `.project-icon--grafia-eye` modifier.
- `assets/grafia-eye.png`: a `~/grafia` szem-képének átlátszó változata. A papír lett az átlátszó rész, a legsötétebb tinta teljesen fedő, a mérete ugyanúgy 462×131. CSS-maszkként használom, -45°-ra forgatva, így világos és sötét témában is a projektikonok kékjét kapja.
- Ellenőrzés helyi HTTP-szerverről (a maszk miatt; az élessel azonos, egy originről szolgál ki): asztali és 375 px, világos és sötét téma.
- A szem körvonala 40 px-en kb. 1 px vékony, vagyis vékonyabb, mint a Lucide-ikonok 2 px-es vonala. A szem így is felismerhető, de az írisz-kör ekkora méretben elvész.
- A grafia repóból vett mondat végén nincs pont, a projektleírások végén igen. Szó szerint hagytam.
