# 🐰 Le Grandi Avventure di Tatà - Stato del Progetto

**Data ultimo aggiornamento:** 20 Settembre 2026  
**File principale:** `tata_game.html`  
**Tecnologie:** HTML5 Canvas, Vanilla JavaScript (ES6+), Web Audio API (Sintetizzatore procedurale), CSS3.  
**Architettura:** 100% *Standalone / Single-File* (nessuna libreria esterna, nessun asset o file mp3/png da scaricare, funzionamento offline istantaneo).

---

## 1. Panoramica del Gioco

*Le Grandi Avventure di Tatà* è un videogioco a scorrimento orizzontale (2D platformer) dal design tenero e curato, ispirato ai pupazzi per la prima infanzia (dudù) e ai classici giochi arcade per famiglie.

Lo schermo di gioco è stato **ingrandito del 25%** (area visiva a 1000x562px su canvas HiDPI Retina con fattore `SCALE_25 = 1.25`) per un'esperienza ancora più immersiva, nitida e confortevole.

Il gioco include **cinque missioni complete e collegate narrativamente**:
1. **Missione 1: Il Ritorno a Casa:** Tatà attraversa la campagna, il bosco magico e le vette innevate, sconfigge il Grande Orso e riabbraccia il suo amico Totò.
2. **Missione 2: Tatà, Mulan e il Bosco di Introdacqua:** Tatà sale in groppa alla sua dolcissima asinella Mulan. Insieme partono dalla stalla, attraversano il fitto bosco di Introdacqua scivolando tra fango e rocce bagnate, sconfiggono il temibile Lupo Guardiano e conquistano il tanto desiderato sacco di avena dorata!
3. **Missione 3: La Fonte di Lama Bianca:** Tatà parte dalla caratteristica *Trattoria Majella* e attraversa il suggestivo borgo medievale in pietra di Sant'Eufemia a Maiella. La fontana del paese è rimasta a secco: gli abitanti chiedono a Tatà di oltrepassare l'antico arco in pietra e risalire la splendida faggeta autunnale fino alla sorgente di Lama Bianca per liberare il corso dell'acqua da un enorme masso, difeso da una simpatica ma dispettosa Lontra Gigante!
4. **Missione 4: Il Parco Avventura di Bocca di Valle:** Tatà indossa imbrago e caschetto presso lo Chalet d'accoglienza di Bocca di Valle (Guardiagrele). Per superare le spettacolari gole della Majella, affronta acrobatici ponti tibetani sospesi, teleferiche zip-line ad alta velocità, scale di corda oscillanti e pareti di reti d'arrampicata, schivando picchi e gazze ladre per conquistare la fantastica Bicicletta!
5. **Missione 5: In Bici verso Giulia (Discesa della Majella):** Tatà salta in sella alla fiammante bicicletta appena conquistata e affronta un'elettrizzante discesa in alta montagna tra salti panoramici, curve veloci e burroni mozzafiato. La bici corre da sola in discesa libera ed è calibrata per un bambino di 6 anni (non si ferma mai, ma si può rallentare e frenare). L'ultimo ostacolo è il pestifero *Gran Formaggio Puzzolente*, superato il quale Tatà raggiunge la sua amichetta Giulia per un tenero scambio di doni: lui le regala la bicicletta e lei gli dona un disegno di Tatà che mangia una carota!

---

## 2. Personaggi

### 🌸 Tatà (Protagonista)
- **Design:** Coniglietto di pezza / *dudù* rosa pastello (`#F8A4B8`) con interno orecchie e dettagli rosa panna (`#FFE6ED`).
- **Nella Missione 5:** Mantiene fedelmente il suo aspetto iconico da dudù rosa pastello con corpicino a copertina, nodini, cuciture a vista, toppa a cuore sul petto, fiocchetto e le sue caratteristiche orecchie lunghe e morbide che ondeggiano aerodinamicamente al vento della discesa.
- **Fisica & Controlli standard (M1, M3, M4):**
  - `A` / `D` o Frecce `⬅️` `➡️`: Cammina orizzontalmente.
  - `W` / `⬆️` / `Spazio`: Salto con gravità calibrata.
  - `S` / `⬇️`: Scivolata a terra con inerzia.
- **Fisica in Bici (M5 - Discesa Libera):**
  - Auto-cruise continuo in avanti verso destra (`facing = 1`, velocità di crociera 3.9 px/frame).
  - `⬅️` / `A` o `⬇️` / `S`: Freni a tamburo con cigolio di gomma (`playBrakeSound`) e scintille, rallentando fino al minimo di sicurezza (1.8 px/frame). Non si ferma mai del tutto per evitare blocchi.
  - `➡️` / `D`: Scatto di pedalata veloce fino a 5.8 px/frame.
  - `Spazio` / `⬆️` / `W`: Salto acrobatico alto (-13.2 px/frame).
  - Rampa di lancio: Super-salto balistico ad alta quota (-14.4 px/frame).
  - Salvataggio dai burroni: Sistema elastico morbido anti-frustrazione che rimette Tatà sulla carreggiata.

### 👓 Giulia (La Bimba di 6 Anni - Missione 5)
- **Design:** Amichetta coetanea di 6 anni dolcissima:
  - Capelli castani morbidi raccolti in due codini sbarazzini con elastici lilla e frangetta sulla fronte.
  - Occhiali tondi montatura lilla/viola pastello (`#AB47BC` / `#CE93D8`) con lenti trasparenti e riflessi luminosi.
  - Faccina dolce, occhioni castani, guance rosee e sorriso radioso.
  - Vestitino estivo giallo solare (`#FDD835`) con pois bianchi e colletto bianco.
  - Scarpette da ginnastica lilla con suola bianca.
- **Il Dono di Giulia:** Giulia mostra orgogliosa e regala a Tatà un autentico disegno a pastello: un foglio con cornice azzurra, il sole che sorride, un praticello fiorito, cuoricini e un coniglietto bianco (Tatà) felice che tiene tra le zampe una grande carota arancione!

### 🐴 Mulan (L'Asinella Carina - Missione 2)
- **Design:** Asinella dudù in morbido peluche grigio tortora (`#C4BBB4`), musetto allungato crema latte, occhioni grandi neri vellutati con 3 ciglia ricurve, orecchie lunghe con interno rosa tenue e criniera castano scuro.
- **Gualdrappa:** Lavanda pastello con frange dorate e toppa a cuore fucsia sul dorso.

### 💙 Totò (Migliore Amico - Missione 1)
- **Design:** Coniglietto dudù grigio perla (`#B0BEC5`) con copertina e rifiniture azzurro cielo (`#4FC3F7`). Attende Tatà davanti al rifugio di famiglia.

---

## 3. Le Missioni e i Mondi di Gioco (4800px per livello)

### 🌻 Missione 1: Il Ritorno a Casa
* **Campagna Rustica (0 - 1600px)** ➔ **Il Bosco Magico (1600 - 3200px)** ➔ **Vette Innevate (3200 - 4800px)**.
* **Boss:** Il Grande Orso (3 Cuori) a `x = 4290`.
* **Traguardo:** Rifugio montano a `x = 4520` con Totò.

### 🐴 Missione 2: Tatà, Mulan e il Bosco Fitto di Introdacqua
* **Intro Cutscene:** Uscita dalla stalla e salto in sella.
* **Faggeta di Introdacqua** ➔ **Sentiero Fangoso con scivolamento** ➔ **Rupi dell'Avena**.
* **Boss:** Il Lupo del Bosco (4 Cuori) e Barriera di Rovi.
* **Traguardo:** Sacco di Avena dorata per Mulan a `x = 4580`.

### 🍂 Missione 3: La Fonte di Lama Bianca (Sant'Eufemia a Maiella)
* **Intro Cutscene & Borgo:** Partenza dalla Trattoria Majella, transito per le vie lastricate e l'arco medievale di Sant'Eufemia a Maiella.
* **Faggeta Autunnale:** Manto ramato, foglie cadenti nel vento e raccolta di castagne.
* **Boss:** La Lontra Gigante (4 Cuori) che ostruisce la fonte con un grande masso.
* **Traguardo:** Liberazione del masso e zampilli cristallini che ripristinano l'acqua della fontana!

### 🧗 Missione 4: Il Parco Avventura di Bocca di Valle (Guardiagrele)
* **Intro Cutscene:** Chalet d'accoglienza, imbrago e caschetto con l'istruttore.
* **Ponti Tibetani** ➔ **Teleferiche Zip-Line (7.2 px/frame con ronzio metallico)** ➔ **Scale di corda e Reti sospese**.
* **Boss:** La Gazza Ladra Reale (4 Cuori).
* **Traguardo:** La splendida Bicicletta della Majella sbloccata con il suono del campanello!

### 🚲 Missione 5: In Bici verso Giulia (Alta Montagna Majella)
* **Intro Cutscene:** Tatà parte dal cartello del *Passo della Majella (Alt. 2145m - Discesa Libera)* in cima alla vetta.
* **Bioma 1: Il Passo della Majella e le Prime Rampe (0 - 1300px):** Carreggiata panoramica in asfalto montano (`mountain_road`) con cordoli in pietra, guard-rail in legno con catarifrangenti rossi, stelle alpine e prime rampe di lancio (`ramp`).
* **Bioma 2: I Viadotti Panoramici sui Burroni (1300 - 2500px):** Ponti in muratura di pietra calcarea e legno sospesi sopra gole profonde (`mountain_bridge`), cartelli di pericolo pendenza e salti acrobatici.
* **Bioma 3: I Grandi Tornanti Veloci (2500 - 3600px):** Discesa rapida con curve e salti spettacolari tra pini e larici d'alta quota.
* **Bioma 4: Il Canyon del Gran Formaggio Puzzolente (3600 - 4450px):** Grande arena in pietra dove si annida il Boss finale.
* **Boss: Il Gran Formaggio Puzzolente (4 Cuori) a `x = 4310`:** Un'enorme fetta di formaggio stagionato brontolone, con buchi svizzeri, chiazze di muffa verde radioattiva, onde e bolle di puzzo animate nell'aria (`Math.sin(...)`), occhiacci arrabbiati e dentone buffo. Viene sconfitto saltandoci sopra e spiaccicandolo con un cartoon squish!
* **Traguardo Finale: La Casetta di Giulia (4480 - 4760px):** Accogliente chalet in legno con tetto spiovente a tegole rosse, comignolo con fumo animato, balcone fiorito di gerani, staccionata, rastrelliera per parcheggiare la bici e festoni colorati *"BENVENUTO TATÀ!"*. Giulia attende festosa a braccia aperte con il disegno di Tatà e la carota!

---

## 4. Nemici e Boss

| Nemico / Boss | Aspetto | Punti | Danno | Zona / Missione |
| :--- | :--- | :--- | :--- | :--- |
| **🧀 Formaggio Arrabbiato** | Fetta con buchi e sopracciglia | +20 | -10 | M1: Campagna / Bosco |
| **🦔 Riccio Spinoso** | Aculei a zig-zag e musetto | +25 | -15 | M1, M2, M3, M5 |
| **🐾 Talpa Scavatrice** | Cumulo di terra e occhialini | +30 | -15 | M1, M2, M5 |
| **🦨 Puzzola con Coda** | Coda alta con striscia bianca | +35 | -20 | M1, M2 |
| **🐗 Cinghialetto** | Pelo nocciola e zannette | +30 | -15 | M2, M3 |
| **🐿️ Scoiattolo** | Pelo fulvo e coda a pennacchio | +35 | -15 | M3: Faggeta |
| **🦉 Gufo Saggio** | Piumaggio bruno e occhi dorati | +40 | -15 | M3: Faggeta alta |
| **🪵 Picchio Acrobatico** | Ciuffo scarlatto e becco forte | +35 | -15 | M4: Tronchi aerei |
| **🦅 Gazza Ladra Volante** | Livrea bianca e blu notte | +40 | -15 | M4, M5 |
| **🐻 Il Grande Orso (Boss M1)** | Pelo bruno massiccio, 3 Cuori | +100 | -25 | M1: Vette Innevate |
| **🐺 Il Lupo Guardiano (Boss M2)**| Peluche ardesia, bandana rossa, 4 Cuori | +150 | -20 | M2: Avena di Mulan |
| **🦦 La Lontra Gigante (Boss M3)** | Bruna, baffetti, 4 Cuori | +180 | -20 | M3: Fonte Lama Bianca |
| **🦅 La Gazza Reale (Boss M4)** | Ali spiegate, becco dorato, 4 Cuori | +200 | -20 | M4: Bocca di Valle |
| **🧀 Gran Formaggio Puzzolente (Boss M5)** | Fetta gigante con muffa verde e onde di puzzo, 4 Cuori | +250 | -20 | M5: Passo della Majella |

---

## 5. Collezionabili

| Collezionabile | Aspetto | Punti | Missione |
| :--- | :--- | :--- | :--- |
| **🥕 Carota Fresca** | Radice arancione con ciuffo verde | +15 | Tutte le missioni |
| **🎁 Regalo a Sorpresa** | Scatolina fucsia con nastro oro | +50 | M1 |
| **🌸 Lampone del Bosco** | Grappolo fucsia vellutato | +25 | M2 |
| **🫐 Mora Selvatica** | Grappolo mora scura | +35 | M2 |
| **🌰 Castagna d'Autunno** | Riccio semi-aperto con castagna mogano | +30 | M3 |
| **🧗 Moschettone da Scalata** | Alluminio lucido e ghiera a vite | +30 | M4 |
| **🪖 Caschetto di Sicurezza** | Caschetto arancione con cinghietto | +40 | M4 |
| **🫐 Mirtillo di Montagna** | Bacca tonda blu ceruleo | +20 | M4 |
| **🔔 Campanello della Bici** | Campanello dorato cromato con nota musicale | +30 | M5 |
| **✏️ Matita da Disegno** | Matita lilla temperata per i disegni di Giulia | +25 | M5 |
| **🍪 Biscotto al Cioccolato** | Biscottino dorato con gocce di cioccolato | +35 | M5 |

---

## 6. Audio e Sintesi Web Audio API

Tutti gli effetti sonori e le musiche sono generati interamente da codice con la Web Audio API:
- **Musica di Sottofondo:** Melodia allegra e rilassante a 140 BPM procedurale.
- **SFX:**
  - Salto (*boing*), raccolta collezionabili personalizzata per ogni tipologia, schiacciamento nemici (*squish*).
  - Teleferica zip-line (*ronzio metallico carrucola*).
  - Campanello bicicletta (*doppio squillo cristallino drin-drin*).
  - Frenata della bicicletta (*fischio d'attrito gomma-asfalto controllato*).
  - Squish del Formaggio Puzzolente (*cartoon squelch umido e morbido*).
  - Suoni dei Boss: Orso, Lupo (ululato), Lontra (squittio e spruzzi), Gazza (cinguettio metallico).
  - Jingle di Vittoria e fanfare di fine livello.

---

## 7. Interfaccia e Navigazione

- **Schermo Ingrandito (+25%):** Dimensioni 1000x562px, top-bar e istruzioni coordinate a 1000px, rendering Retina 2x scalato a 1.25x senza alterare i calcoli fisici interni.
- **Top Bar a 5 Pillole:** Accesso diretto istantaneo a tutte le 5 missioni:
  `[🌻 Missione 1]` `[🐴 Missione 2]` `[🍂 Missione 3]` `[🧗 Missione 4]` `[🚲 Missione 5]`
- **Progressione Narrativa Continua:** M1 ➔ M2 ➔ M3 ➔ M4 ➔ M5 ➔ Ritorno a M1, con modali celebrative illustrate e testi immersivi.
- **HUD Glassmorphic:** Badge punteggio con icona a tema (`🐰`, `🐴`, `🍂`, `🧗`, `🚲`) e indicatore del bioma in tempo reale.
- **Risoluzione Bug Focus Tasti (Missione 4):** Risolto il problema per cui premendo la barra spaziatrice (o i tasti di salto/movimento) Tatà veniva reimpostato al punto di partenza: i pulsanti dell'interfaccia (top-bar e modali) ora rilasciano immediatamente il focus (`blur()`, `tabindex="-1"`), l'evento `keydown` previene le azioni predefinite del browser (`e.preventDefault()`), il canvas di gioco mantiene il focus attivo e le coordinate di spawn della Missione 4 sono allineate coerentemente a `(170, 336)` con supporto a `ArrowUp` per il salto dell'intro.

---

## 8. Modalità Mobile / Tablet, Hamburger Menu e Fix Audio iOS

- **Esperienza Fullscreen Mobile:** Il gioco ora occupa il 100% dell'area visibile dello schermo (`100vw x 100dvh` con `overflow: hidden`), eliminando scrollbar o tagli visivi su iPhone e tablet in qualsiasi orientamento (landscape/portrait).
- **Hamburger Menu Semi-Trasparente:** Sostituita la barra superiore ingombrante con un elegante pulsante ☰ posizionato in alto a destra in sovrimpressione glassmorphic (`rgba(255,255,255,0.78)` con `backdrop-filter: blur(10px)`). Cliccandolo si apre un drawer laterale scorrevole con:
  - Toggle Audio (`🎵 Musica: ON/OFF`)
  - Selettore istantaneo delle 5 missioni con evidenziazione attiva
  - Toggle dei comandi touch a schermo
  - Scheda con la guida e gli obiettivi della missione corrente
- **Controlli Touch in Semitrasparenza (Overlay):** I pulsanti virtuali fluttuano ora sopra il fondale in basso a sinistra (D-Pad direzioni) e in basso a destra (Salta e Scivola/Frena) con trasparenza elegante (`opacity: 0.82`), lasciando l'intera visuale di gioco aperta e sgombra.
- **Risoluzione Audio iOS Safari (iPhone / iPad):**
  - Risolto il blocco audio tipico di iOS WebKit tramite riproduzione immediata di un silent buffer sincrono al primo tap (`unlockIOSAudio`).
  - Sblocco Web Audio universale agganciato a `['touchstart', 'touchend', 'click', 'keydown']` su `window`.
  - Risolto il disallineamento temporale (`audioCtx.currentTime > nextNoteTime`) che causava il freeze o il collasso dei nodi audio su Safari.
  - Schedulazione musicale sincronizzata anche all'interno del game loop principale `update()`, garantendo continuità della melodia anche se Safari riduce la frequenza dei `setInterval` in background.
  - Gestione dell'evento `visibilitychange` per sospendere e riprendere correttamente l'audio quando si cambia tab.
- **File di ingresso `index.html`:** Generato `index.html` allineato a `tata_game.html` per l'accesso immediato da root su GitHub Pages.
