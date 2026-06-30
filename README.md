<!doctype html>
<html lang="it"><head><script>window["__codeletBootstrap__"]=JSON.parse('{"A":"A","B":"20260630-05-8900874"}');</script><script src="/_sdk/e4192b04afde3ce7.telemetry_sdk.js" integrity="sha512-4eZpyKBd3YJnsIPrIpaBqo7QT5UZ6+KSFXkSu1IQiB7jKM8y67ChRhZ5Yh6JfuOJCbPdISiNcS6nLKZzIMG1uQ=="></script>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Regno di Haryel</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <link href="https://fonts.googleapis.com/css2?family=Cardo:ital,wght@0,400;0,700;1,400&amp;display=swap" rel="stylesheet">
  <style>
    body{font-family:'Cardo',serif}
    .npc-card{background:linear-gradient(160deg,#f5e6c8 0%,#e8d4a8 30%,#dbc492 70%,#cdb07a 100%);border:1px solid #a08050;box-shadow:inset 0 0 30px rgba(120,80,30,0.15),0 2px 8px rgba(0,0,0,0.3);position:relative;padding:1.25rem 1.5rem;border-radius:6px}
    .npc-card::before{content:'';position:absolute;inset:8px;border:1px solid rgba(160,128,80,0.3);pointer-events:none;border-radius:4px}
    .filter-tag{padding:0.25rem 0.7rem;border-radius:4px;cursor:pointer;border:1px solid #a08050;background:rgba(200,170,120,0.15);color:#c9a86a;font-size:0.8rem;transition:all 0.2s;user-select:none}
    .filter-tag:hover{background:rgba(200,170,120,0.3)}
    .filter-tag.active{background:#a08050;color:#2c1e0f;font-weight:700}
    .sort-btn{padding:0.25rem 0.75rem;border-radius:4px;cursor:pointer;border:1px solid #a08050;font-size:0.75rem;transition:all 0.2s}
    .sort-btn.active{background:#c9a86a;color:#1a0f05;font-weight:700}
    .search-input{background:rgba(30,20,10,0.6);border:1px solid #a08050;color:#e8d4a8;padding:0.5rem 1rem;border-radius:4px;font-family:'Cardo',serif;outline:none;width:100%}
    .search-input::placeholder{color:#8b7a5a}
    .search-input:focus{border-color:#c9a86a}
  </style>
  <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js" type="text/javascript"></script>
  <script src="/_sdk/48bf7c4c70d0d03c.data_sdk.js" type="text/javascript" integrity="sha512-e/yrQJz+prdXXt4yUvxXhl1WBGu3BRkP8X0fipGXI5gqiFClI7wI6K3TQnD7d63vx+BVhwzIvY6r8OrpX7lXJA=="></script>
  <script src="/_sdk/5d8c692e132d2125.resizing_sdk.js" type="text/javascript" integrity="sha512-/Du3Fqe12kKsCd3BrbaNQEPtMxQi9S5hbJhnTf09AAilpqYsGa4N0rnimSX1Ui4dwNElKlen6VlI+E1n/NEfrA=="></script>
 </head>
 <body data-template-id="__page-root" class="min-h-screen p-4 pt-8" style="background: linear-gradient(160deg, rgb(26, 15, 5), rgb(44, 30, 15), rgb(15, 10, 4));">
  <header class="text-center mb-6 max-w-3xl mx-auto px-4">
   <h1 data-template-id="page-title" class="canva-text text-3xl md:text-4xl tracking-widest mb-3" style="color: rgb(201, 168, 106); font-weight: 700; font-style: normal; font-size: 32px;">Regno di Haryel</h1>
   <p data-template-id="subtitle" class="canva-text text-sm md:text-base leading-relaxed opacity-90" style="color: rgb(160, 128, 80); font-weight: 400; font-style: normal; font-size: 16px;">Compendio degli NPC del reame</p>
  </header>
  <section class="w-full max-w-3xl mx-auto mb-4">
   <div class="flex gap-2 mb-4"><input type="text" id="search-input" class="search-input" placeholder="Cerca nome, razza, classe o descrizione"> <button data-template-id="reset-btn" id="reset-btn" class="canva-button px-4 py-2 rounded text-sm font-bold cursor-pointer whitespace-nowrap" style="background: rgb(160, 128, 80); color: rgb(26, 15, 5); font-weight: 700; font-style: normal; font-size: 16px;">Reset</button>
   </div>
   <div class="flex flex-wrap justify-center gap-2 mb-4"><button data-template-id="sort-name-asc" id="sort-name-asc" class="canva-button sort-btn" style="background: transparent; color: rgb(201, 168, 106); font-weight: 400; font-style: normal; font-size: 16px;">Nome A→Z</button> <button data-template-id="sort-name-desc" id="sort-name-desc" class="canva-button sort-btn" style="background: transparent; color: rgb(201, 168, 106); font-weight: 400; font-style: normal; font-size: 16px;">Nome Z→A</button> <button data-template-id="sort-age-asc" id="sort-age-asc" class="canva-button sort-btn" style="background: transparent; color: rgb(201, 168, 106); font-weight: 400; font-style: normal; font-size: 16px;">Età ↑</button> <button data-template-id="sort-age-desc" id="sort-age-desc" class="canva-button sort-btn" style="background: transparent; color: rgb(201, 168, 106); font-weight: 400; font-style: normal; font-size: 16px;">Età ↓</button>
   </div>
   <div class="mb-3">
    <h3 data-template-id="legend-race-title" class="canva-text text-sm mb-1 uppercase tracking-wider" style="color: rgb(201, 168, 106); font-weight: 400; font-style: normal; font-size: 19px;">Razza</h3>
    <div id="filter-race" class="flex flex-wrap gap-2"></div>
   </div>
   <div class="mb-3">
    <h3 data-template-id="legend-gender-title" class="canva-text text-sm mb-1 uppercase tracking-wider" style="color: rgb(201, 168, 106); font-weight: 400; font-style: normal; font-size: 19px;">Genere</h3>
    <div id="filter-gender" class="flex flex-wrap gap-2"></div>
   </div>
   <div class="mb-3">
    <h3 data-template-id="legend-class-title" class="canva-text text-sm mb-1 uppercase tracking-wider" style="color: rgb(201, 168, 106); font-weight: 400; font-style: normal; font-size: 19px;">Classe</h3>
    <div id="filter-class" class="flex flex-wrap gap-2"></div>
   </div>
  </section>
  <p data-template-id="page-counter" id="page-counter" class="canva-text text-center text-sm opacity-70 mb-4" style="color: rgb(139, 122, 90);"></p>
  <main id="npc-list" class="w-full max-w-3xl mx-auto space-y-4 pb-8"></main>
  <script src="/_sdk/c94a279e896d0a23.editing_sdk.js" integrity="sha512-uhzUP50YzTVKO+Zk7rEhhvjMMNFy592eHXVEXciJzhLpIQxrlwzWv/DQvyYWQ+AKpYwxxCvjgWkVa5LTga2NWg=="></script>
  <script>
const npcs=[
{nome:"Akra della Zanna",desc:"Dragonide blu, femmina, 30 anni. Fabbro! Lavora nella fucina centrale della città, dove batte il ferro e l'acciaio per ordini di nobili e avventurieri. Ha una cicatrice lunga il viso che dice le sia stata inflitta da un drago rivale nella sua gioventù, anche se potrebbe essere soltanto una bugia che ama raccontare ai clienti per farsi valere e attirare attenzione.",razza:"Dragonide",genere:"Donna",classe:""},
{nome:"Albina Sermane",desc:"Tiefling ritualista accumulatore seriale di conoscenza random di 32 anni. Sorella gemella di Astreus Sermane, tiefling, fabbro e artigiano. Albina è ossessionata dal raccogliere frammenti di informazioni su rituali antichi, magia minore e rimedi strani. Ha un'abitazione ingombra di libri, pergamene, e strani ingredienti conservati in vasi. Spesso la si trova nella biblioteca cittadina a rovistare tra gli archivi più polveredosi.",razza:"Tiefling",genere:"Donna",classe:"Ritualista"},
{nome:"Alexander Ulkior",desc:"32 anni, mezzorco, Monaco-barbaro, istruttore presso la caserma della città, figlio di madre umana e padre orco. Insegna arti marziali e tattiche di combattimento ai nuovi reclute. È severo ma giusto, con cicatrici di battaglia che raccontano di anni passati come mercenario prima di decidere di insegnare alle nuove generazioni.",razza:"Mezz'orco",genere:"Uomo",classe:"Monaco"},
{nome:"Alexaeus",desc:"Mezz'elfo, 75 anni, fabbro e arcanista, abbastanza schivo e diffidente un po' con tutti. Lavora nella sua fucina in una torre scura fuori dalle mura della città. Realizza armi magiche e oggetti incantati per chi ha il prezzo giusto e non fa troppe domande. Ha studiato arti arcane per decenni e il suo lavoro riflette quella conoscenza oscura e sofisticata.",razza:"Mezz'elfo",genere:"Uomo",classe:"Arcanista"},
{nome:"Alfred Von Ruprecht",desc:"Umano, età ignota, Imprenditore di nobili origini che vive da solo col suo maggiordomo. Si dice sia una delle persone più ricche della città e anche una delle più vecchie. In realtà è un automa costruito dall'originale Alfred Von Ruprecht morto ormai centinaia di anni fa. Nessuno sa come continui a funzionare o chi lo mantenga, ma il suo danaro è autentico e le sue affari sempre redditizi.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Andrix Ramospezzato",desc:"Kenku ranger, 15 anni (~24 umani), sesso maschile, viaggio alla scoperta del mondo e vivo di caccia, ho lasciato al \"nido natale\" i miei genitori e mio fratello. Affascinato dagli umani e dalla loro cultura, è curioso di natura e spesso combina guai per sua innocente ignoranza. Possiede un'ascia da caccia ben curata e ama raccontare storie della foresta da cui proviene.",razza:"Kenku",genere:"Uomo",classe:"Ranger"},
{nome:"Arakk Bloodyhammer",desc:"75 anni, nano eldritch knight. Soldato a capo della guardia che proteggeva le mura della fortezza di provenienza, ormai caduta. Ora si occupa di una locanda in cui vende alcolici da lui creati. Ha la tendenza a cantare luce su ogni boccale che serve e sulla sua parannanza urlando (o meglio, ruttando): \"LUCEEEEE!!\" I clienti lo amano per la sua gioia sfrenata e i suoi alcolici potenti.",razza:"Nano",genere:"Uomo",classe:"Guerriero"},
{nome:"Arturo Locke Harrow",desc:"30 anni umano, pirata contrabbandiere, non ha famiglia e la sua ciurma della \"Sirena Grigia\" è affondata in mare. L'unica cosa che gli è rimasto fare è il fattorino per una gilda di ladri i \"Quattro Quarti\": consegna per loro oggetti magici illegali tra le città del regno. Ha imparato a camminare nelle ombre e a non fare domande, anche se a volte il peso del suo passato lo tormenta di notte.",razza:"Umano",genere:"Uomo",classe:"Ladro"},
{nome:"Aurelion Solis",desc:"Dragonide Blu, Stregone Aberrante. Le sue scaglie sono di un blu notte intenso pieno di costellazioni ed astri in movimento, riflesso stesso dell'universo. Gestisce un pub con un gigantesco telescopio al centro, divenendo luogo di divulgazione e raduno di intellettuali, studiosi e filosofi. Affascinato dall'astronomia e dai misteri dell'universo, parla spesso di strani fenomeni celesti e cosmic knowledge con chiunque lo ascolti.",razza:"Dragonide",genere:"Uomo",classe:"Stregone"},
{nome:"Azog",desc:"Mezz'Orco, ritirato da un passato da marinaio. Gestisce un negozio di attrezzatura da pesca nel quartiere portuale della città. Ha mani callose e forti, sempre sporche di pesce e catrame. È un tipo tranquillo che preferisce il silenzio del mare alle chiacchiere della gente.",razza:"Mezz'orco",genere:"Uomo",classe:""},
{nome:"BarbaBong",desc:"Nano chierico, dominio della Guerra, 90 anni. Ogni volta che deve fare qualcosa prima fuma la pipa Bong. Ha un passato da marinaio traghettatore nelle grotte di Pietraluce. Ora prega Tyr la mattina al santuario, poi lo si può trovare a fumare la sua pipa sotto una qualsiasi grande quercia. La pipa lo rilassa e stimola il suo pensiero mistico.",razza:"Nano",genere:"Uomo",classe:"Chierico"},
{nome:"Beiren",desc:"32 anni, Harengon. Ex Chierico itinerante ora Sacerdote di Selûne nella chiesa della città, Chierico del crepuscolo. Ha un fratello: Banban, 20 anni, curioso e spirito libero, tende ad esplorare i dintorni della città, si mette spesso nei guai che poi tocca al fratello rimediare. Beiren è paziente ma stanco, sempre preoccupato dalle avventure pericolose di Banban.",razza:"Harengon",genere:"Uomo",classe:"Chierico"},
{nome:"Belpher Davbul \"Baffone\"",desc:"Halfling piede lesto, 50-55 anni, conosciuto come \"Baffone\" per via dei suoi lunghi rozzi baffi a manubrio. Proprietario di un carro ambulante stravagante che vende merce trovata o riciclata. Gira per le strade della città cantando urli di mercante, fermandosi davanti ai tavoli degli avventurieri. Ha sempre qualcosa di strano o utile nascosto tra i suoi affari.",razza:"Halfling",genere:"Uomo",classe:""},
{nome:"Benjen Blackdoor",desc:"Custode e guardiano del museo cittadino. Umano ladro, 37, maschio. Sposato con Reesa Sandalwood, halfling, 40 anni. Benjen ha rinunciato alla vita criminale per gestire il museo, ma la sua esperienza da ladro gli permette di sapere come proteggere i tesori dalla criminalità. È un uomo serio e conscenzioso che ama i reperti antichi.",razza:"Umano",genere:"Uomo",classe:"Ladro"},
{nome:"Brenjos",desc:"Loxodonte maschio di 350 anni, un tempo corsaro, ora burocrate responsabile del porto mercantile. Brenjos è un elefante intelligente e colto, che ha navigato i mari durante i suoi giovani giorni ma ha scelto la stabilità amministrativa in vecchiaia. Ha una memoria prodigiosa e ricorda ogni nave che ha visto nel porto negli ultimi due secoli.",razza:"Loxodonte",genere:"Uomo",classe:""},
{nome:"Brikelberry",desc:"Gnomo Insegnante di 50 anni, si occupa di includere relativi minori di tutte le razze nella scuola dove lavora. È una figura calorosa che crede fermamente nell'educazione per tutti, indipendentemente dall'origine o dalla ricchezza. I suoi studenti lo adorano per la sua pazienza e il suo umorismo.",razza:"Gnomo",genere:"Uomo",classe:""},
{nome:"Bucciaratiilgrande — Ro",desc:"Giovane adulto, Grung, maschio. Sta cercando lavoro ma per ammazzare il tempo per ora si allena al monastero dei monk. È atletico e ambizioso, sperando che il monachesimo gli insegni disciplina e scopo. Ha una voce stridula caratteristica e un senso dell'umorismo infantile.",razza:"Grung",genere:"Uomo",classe:"Monaco"},
{nome:"Cado Presye",desc:"Umana, vive nel bosco e fa la levatrice/guaritrice. È una druida dalla pelle scura, ha un'età indefinibile tra i 55 e i 65 anni. Cado è una donna solitaria che conosce ogni erba curativa e ogni rimedio naturale. Le donne della città la cercano quando è ora di partorire, fiduciosamente.",razza:"Umano",genere:"Donna",classe:"Druida"},
{nome:"Caelynn Alfhard",desc:"Elfa del bosco stregona. Da bambina una fata le ha donato i suoi poteri poiché i genitori di Caelynn le salvarono la vita. Caelynn è legata alla magia dei boschi e alle stregonerie fatate, un dono che continua a definire il suo rapporto con la natura e la magia. Porta il segno della benedizione fatata visibile nei suoi occhi luminosi.",razza:"Elfo",genere:"Donna",classe:"Stregone"},
{nome:"Cailan Sage",desc:"Umano di 34 anni. Venditore di tessuti nella bottega di famiglia ereditata dal padre. I tessuti Sage sono famosi in tutto il regno per la loro qualità, colore e fattura. Cailan è un uomo d'affari acuto che ha mantenuto e ampliato il commercio di famiglia, disponendo ora di carichi provenienti da terre lontane.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Carl O'sea",desc:"Dragonide Gemmato di quarzo. Medico della città, rispettato per la sua conoscenza dei rimedi e della chirurgia. Ha un aspetto trasparente e affascinante come il quarzo, e il suo ufficio è sterile e ordinato. I pazienti lo cercano per sua competenza e compassione.",razza:"Dragonide",genere:"Uomo",classe:""},
{nome:"Carm — Kaermyn",desc:"Elfo alto, maschio, età 2000 anni. Studioso della magia oscura e cultore delle lingue. Carm è uno studioso antico con accesso a testi e conoscenze che pochi nel reame comprendono. È riservato e spesso sembra distratto dai pensieri dei millenni che ha vissuto.",razza:"Elfo",genere:"Uomo",classe:"Mago"},
{nome:"Carys",desc:"Tabaxi tigre, gigolò. Figlio di una prostituta e un cavaliere. Vissuto tra i quartieri del piacere della città. Carys è affascinante e seducente, ma dietro il suo sorriso c'è la profonda conoscenza del dolore e dello sfruttamento. Cerca sempre una via d'uscita da questo lavoro.",razza:"Tabaxi",genere:"Uomo",classe:""},
{nome:"Cheesis Godstrength",desc:"Umano erudito, precettore di nobili rampolli e inventore di meccanismi per l'irrigazione dei campi. Cheesis è un genio pratico che combina sapere accademico con ingegneria inventiva. Mira a migliorare la produttività agricola del regno con i suoi dispositivi idraulici.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Claire",desc:"Maga umana, 30 anni, lavora nella biblioteca della città e si diverte a consigliare libri a chiunque la visiti. Ha un dono naturale nel comprendere cosa ogni persona cerca leggendo, e dedica tempo a trovare il tomo perfetto. La biblioteca è il suo tempio e i libri la sua religione.",razza:"Umano",genere:"Donna",classe:"Mago"},
{nome:"Clea Sithis",desc:"100+ anni, Damphir, Artefice Battlesmith. Come difensore di acciaio ha una viverna. Clea è una forza della natura, metà vampirica e metà umana, con abilità martellante straordinarie. La sua viverna è una creatura fedele che combatte al suo fianco nei momenti di pericolo.",razza:"Damphir",genere:"Donna",classe:"Artefice"},
{nome:"Cora Gentrield",desc:"27 anni, halfling. È una curatrice in una comunità monastica dove si prende cura dei malati e dei feriti. Cora è compassionevole e saggia, capace di offrire conforto fisico e spirituale. I monaci la rispettano profondamente.",razza:"Halfling",genere:"Donna",classe:""},
{nome:"Cornelia",desc:"Tiefling, falconiera, ranger cacciatore delle tenebre. Addestra animali per uso quotidiano e per il combattimento. Ha una connessione sovrumana con i rapaci e conosce il linguaggio dei predatori notturni. I suoi uccelli sono formidabili alleati in battaglia.",razza:"Tiefling",genere:"Donna",classe:"Ranger"},
{nome:"Custode del Nexus",desc:"Risiede nella Torre del Nexus, nessuno sa da quanto. È il custode dove avventurieri senza compagnia e mastri senza seguito si incontrano. Il Custode è una figura enigmatica, a volte saggio, a volte bizzarro. Si dice conosca il destino di ogni avventuriero che entra nella Torre.",razza:"Umano",genere:"",classe:""},
{nome:"Davide — Gurt Kappenbox",desc:"Maniscalco e allevatore di cavalli. 4 figli. Gurt è un uomo robusto che conosce ogni cavallo del regno per nome e temperamento. La sua famiglia vivace e rumorosa riempie la sua fattoria di vita e movimento. È conosciuto per la qualità straordinaria dei suoi cavalli da battaglia.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Dodger",desc:"Drow preadolescente (circa 10 anni età umana) ladro fiero. Fu abbandonato in un orfanotrofio quando era neonato. Dodger è precoce e scaltro, con un cuore dolce nascosto sotto lo scudo di un ladro professionista. Spera segretamente di trovare una famiglia vera.",razza:"Drow",genere:"Uomo",classe:"Ladro"},
{nome:"Do'",desc:"Medico templare che lavora presso il tempio principale della città. Do' è un guaritore dedicato che combina medicina con spiritualità. I poveri lo cercano per i suoi servizi gratuiti.",razza:"Umano",genere:"Uomo",classe:"Chierico"},
{nome:"Dorian",desc:"Bardo mezzelfo saccente e curioso scaltro, insegnante scolastico nella scuola cittadina. Insegna musica, storia e arti liberali ai giovani studenti. È stimolante e a volte esasperante, sempre con una risposta spiritosa pronta. I suoi studenti lo amano e lo odiano allo stesso tempo.",razza:"Mezz'elfo",genere:"Uomo",classe:"Bardo"},
{nome:"Drahmor D. Terzo",desc:"Dragonide Paladino! Cartografo e Disegnatore, scrive e illustra mostri e disegna le mappe dei sentieri inesplorati. 128 anni. Drahmor ha dedicato la sua vita a mappare le terre selvagge e a preservare il sapere dei mostri che ha incontrato. I suoi atlanti sono tesori di conoscenza geografica e zoologica.",razza:"Dragonide",genere:"Uomo",classe:"Paladino"},
{nome:"Drew Hart",desc:"30 anni, umano. Scrivano di annunci da bacheca per avventurieri. Drew trascorre i suoi giorni nella taverna principale, annotando richieste di lavoro e missioni. Conosce ogni avventuriero di talento e ha l'occhio per i lavori che si adattano a ogni persona.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Ek Ki Me",desc:"Vagabondo umano barbone che dorme per le strade della città. Ek Ki Me è una figura solitaria e apparentemente folle, ma con una saggezza strana e impenetrabile. Alcuni dicono abbia poteri psichici.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Elyon Aldaron",desc:"Elfo alto nato e cresciuto in una famiglia umile. Fabbro molto bravo nella creazione di armi e infusione magiche. Ha elevato l'artigianato della famiglia a uno status di maestria, creando pezzi che sono ricercati da guerrieri e maghi. Il suo laboratorio emana sempre di calore e potenza magica.",razza:"Elfo",genere:"Uomo",classe:""},
{nome:"Emerald Huntwood",desc:"30 anni, un cangiante che mantiene l'aspetto di un umano dai capelli bianchi. Esperto cacciatore che lavora per la corte reale. Emerald è segreto sulla sua vera natura e preferisce rimanere anonimo, anche se i sussurri sulla sua vera forma si diffondono tra i tavoli.",razza:"Cangiante",genere:"Uomo",classe:"Ranger"},
{nome:"Eos Glimmerfield",desc:"20 anni, elfa, druida della luna. Crea bambole veneratorie e voodoo con materiali del bosco per rituali mistici e cure. È una praticante della magia primitiva e ancestrale, connessa profondamente alla luna e alla terra. I suoi manufatti sono belli e bizzarri allo stesso tempo.",razza:"Elfo",genere:"Donna",classe:"Druida"},
{nome:"Erim Holkol",desc:"Halfling costruttore e venditore di trappole. Ha un negozio chiamato \"Il Grimaldello Incrinato\". Erim è un ingegno meccanico che progetta trappole per ladri e difese per i ricchi. Il suo negozio è un labirinto affascinante di meccanica inventiva.",razza:"Halfling",genere:"Uomo",classe:""},
{nome:"Estiel",desc:"Elfo, 2900 anni. Maestro d'armi che ha combattuto in guerre dimenticate. Ha una grazia letale e una saggezza profonda derivante da millenni di pratica. I suoi studenti lo temono e lo rispettano profondamente.",razza:"Elfo",genere:"Uomo",classe:"Guerriero"},
{nome:"Fabrizio — Kallax",desc:"Ghitzerai, fornaio di 120 anni, senza famiglia, bandito dalla comunità originale. Fabrizio ha trovato pace nel fare il pane, usando le ricette antiche della sua gente. È un uomo solitario che parla poco ma che dona cibo a chi ha fame.",razza:"Ghitzerai",genere:"Uomo",classe:""},
{nome:"Finn Morningstar",desc:"Umano guerriero, 21 anni, guardia cittadina. Finn è giovane e idealista, determinato a proteggere la città e i suoi cittadini. È abile con la spada e coraggioso, anche se a volte la sua inesperienza lo mette in situazioni difficili.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
{nome:"Flavius Aribaldov",desc:"Umano, 40 anni, commerciante di scarpe. Nel tempo libero costruisce passaggi segreti sotto la città. Flavius è un doppio gioco, un uomo con una vita ordinaria e segreti straordinari. I suoi passaggi sono usati da molte fazioni in città.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Fofò Purtùsu",desc:"70 anni, Umano, Paladino dei quartieri poveri della città. Fofò ha consacrato la sua vita a proteggere i miserabili e gli oppressi dai crudeli e dai ricchi senza cuore. È una figura leggendaria nei bassifondi, quasi un santo vivente.",razza:"Umano",genere:"Uomo",classe:"Paladino"},
{nome:"Franco",desc:"Umano 45 anni carpentiere e mezzo calvo. Odia gli elfi. Franco è un uomo grezzo e diretto, con un pregiudizio profondo verso la razza elfica. Nonostante questo, è un lavoratore competente e affidabile, anche se le sue opinioni sono di cattivo gusto.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Galius il Rosso",desc:"Stregone, mezza età. In origine un drago rosso antico trasformato in forma umana. Gestisce un orfanotrofio e alleva api. Galius è un paradosso vivente: una creatura di guerra e fuoco che ha trovato pace nella cura dei bambini. Alza le sue api per il miele, che usa come medicina.",razza:"Umano",genere:"Uomo",classe:"Stregone"},
{nome:"Gash Purpuris",desc:"25 anni, mezz'orco, maschio, aggiusta-carrozze nella zona portuale. Gash è un lavoratore manuale appassionato che prende profondamente a cuore ogni veicolo che ripara. Ha le mani macchiate di grasso e una barba riccia che non rasa mai.",razza:"Mezz'orco",genere:"Uomo",classe:""},
{nome:"Gelica",desc:"Drow, giovane donna. Bottega di ceramiche e spettacoli di burattini per i bimbi. Gelica ha abbandonato il Sottosuolo per la luce, portando con sé l'arte del teatro di marionette. I bambini della città la adorano per le sue storie magiche e fantastiche.",razza:"Drow",genere:"Donna",classe:""},
{nome:"Ghan Nesbitt",desc:"Umano, 26 anni, Cacciatore. Vive in una capanna al limitare della città, al confine tra civiltà e natura selvaggia. Ghan è un solitario che fornisce carne selvaggina e pelli ai macellai della città. È silenzioso e osservatore, con occhi che vedono tutto della foresta.",razza:"Umano",genere:"Uomo",classe:"Ranger"},
{nome:"Goran",desc:"Mezzorco dall'animo gentile. Conosciuto come L'ombra gentile nella comunità. Goran è una contraddizione vivente: una creatura dall'aspetto feroce ma dal cuore mite. Lavora come infermiere e assistente ai bisognosi, guadagnandosi il rispetto universale.",razza:"Mezz'orco",genere:"Uomo",classe:""},
{nome:"Hulkvard Barbagrigia",desc:"Nano, barbaro, 130 anni. Armaiolo famoso per la martelascia nanica che rappresenta il culmine della maestria nanica. Hulkvard è una montagna di muscoli e follia controllata, il guerriero perfetto. La sua fucina produce le armi più belle del regno.",razza:"Nano",genere:"Uomo",classe:"Barbaro"},
{nome:"Icy Hurricane",desc:"30 anni, dragonide argento femmina. Druida, possiede l'emporio del paese dove vende erbe, pozioni e oggetti magici. Icy è fredda come il ghiaccio nel carattere ma affettuosa verso i suoi clienti leali. Il suo emporio è un rifugio per chi cerca il strano e il mistico.",razza:"Dragonide",genere:"Donna",classe:"Druida"},
{nome:"Insengard e Urtu",desc:"Umano e mezzorco addetti alla guardia cittadina che lavorano insieme come una squadra. Sono amici inseparabili e forma un binomio perfetto. Insengard è il brains, Urtu è la forza.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
{nome:"Ishika Tomari",desc:"Tabaxi, 36 anni, ladra. Una senzatetto strana che tutti conoscono e che la comunità ha adottato nel cuore. Ishika è astuta e agile, con un cuore sorprendentemente buono nonostante il suo commercio. Ruba dai ricchi per sopravvivere.",razza:"Tabaxi",genere:"Donna",classe:"Ladro"},
{nome:"Jack Whitewinter",desc:"33 anni, Oni, maschio, Capo delle Guardie dell'archivio magico della città. Jack è una creatura spaventosa che ha trovato purpose nel proteggere i segreti arcani della città. È rigido e senza emozioni, ma straordinariamente competente.",razza:"Oni",genere:"Uomo",classe:"Guerriero"},
{nome:"Jana Serpefiero",desc:"29 anni, Tiefling. Marionettista circense che gira per le piazze della città con il suo spettacolo. Jana è una artista appassionata, capace di incantare folle intere con i suoi burattini e le sue storie. Ha un talento narrativo straordinario.",razza:"Tiefling",genere:"Donna",classe:""},
{nome:"Jorgha di Valdombra",desc:"58 anni, mezzelfa, barda collegio della sapienza. Jorgha è una donna di vasta cultura e sapienza, che ha passato la vita a studiar antiche canzoni e storie. La sua voce ha potenza arcana e i suoi insegnamenti formano i bardi della città.",razza:"Mezz'elfo",genere:"Donna",classe:"Bardo"},
{nome:"Josef Lambari",desc:"Giovane umano di 21, assistente dell'erborista e alchimista del paese. Josef è entusiasta e dedito al suo mestiere, apprendendo i segreti della distillazione e della tintura. Ha una memoria eccezionale per le ricette.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Kestel",desc:"Kender di 15 anni adottata da una famiglia di umani. Curiosa e senza paura, ha la voglia irrefrenabile di toccare e esaminare ogni cosa. È ingenua e innocente nonostante le intenzioni kender di raccogliere oggetti. I suoi genitori umani l'amano profondamente.",razza:"Kender",genere:"Donna",classe:""},
{nome:"Kinson",desc:"Elfo, mastro birraio e detentore della taverna e bordello di Kinson. Kinson è un uomo astuto che ha costruito un impero commerciale sulla base di piaceri carnali e alcol. È affascinante e pericoloso allo stesso tempo.",razza:"Elfo",genere:"Uomo",classe:""},
{nome:"Kliarn Scaglia d'Argento",desc:"26 anni, dragonide. Custode della biblioteca cittadina con una passione profonda per i libri e l'apprendimento. Kliarn è un dragonide argento raro, noto per l'intelligenza e la saggezza. Ordina i tomi con precisione quasi ossessiva.",razza:"Dragonide",genere:"Uomo",classe:""},
{nome:"Kurzum Fall",desc:"Legale neutrale, umano, stregone evocatore, 33 anni. Dà consigli imparziali a chi si ferma a parlare con lui nel suo ufficio. Kurzum non giudica e ascolta con comprensione, offrendo soluzioni logiche a problemi complessi.",razza:"Umano",genere:"Uomo",classe:"Stregone"},
{nome:"Lacrimis Lakeblue",desc:"Genasi dell'acqua, 30 anni, chierico della vita. Lacrimis è connesso profondamente ai cicli dell'acqua e della vita, guarendo i malati e i feriti. Ha una serenità quasi aquatica nel suo comportamento e un amore infinito per tutte le creature viventi.",razza:"Genasi",genere:"Uomo",classe:"Chierico"},
{nome:"Leif Dagsson",desc:"25 anni, Umano, bardo. Assiste gli operai nelle costruzioni della città con canzoni che danno ritmo al lavoro. Leif è un giovane ottimista che vede la bellezza nel lavoro manuale. La sua musica rende ogni compito più leggero.",razza:"Umano",genere:"Uomo",classe:"Bardo"},
{nome:"Loki",desc:"Ladra ciarlatana, mezzelfa. 29 anni, avventuriera e mercenaria che accetta lavori da molte fazioni diverse. Loki è affascinante e bugiarda, con un sorriso sempre pronto e un pugnale nascosto. Nessuno sa realmente da quale parte stia.",razza:"Mezz'elfo",genere:"Donna",classe:"Ladro"},
{nome:"Lorimbur Barbargento",desc:"Nano, 110 anni, fornaio pasticcere. Celebre per il pane nanico da assedio che può stare fresco per mesi. Lorimbur è un maestro della cottura, capace di infondere magia minore nei suoi pani. I soldati del regno lo cercano per il suo pane energizzante.",razza:"Nano",genere:"Uomo",classe:""},
{nome:"Lucilla",desc:"Mezzelfa, 80 anni. Attraggo le persone nel mio antro e le spedisco nelle missioni che nessun altro vuole fare. Lucilla è una intermediaria misteriosa che conosce gli avventurieri disperati e i lavori impossibili. Ha una rete di informatori attraverso il regno.",razza:"Mezz'elfo",genere:"Donna",classe:""},
{nome:"Luka Russor",desc:"Nano di 26 anni, giudice della corte cittadina. Luka è giovane per il suo ruolo ma straordinariamente imparziale e saggio. Applica la legge con fermezza e compassione, rispettato da entrambi i lati.",razza:"Nano",genere:"Uomo",classe:""},
{nome:"Maximilian Regulus",desc:"Mago di 24 anni proprietario del Verdant dove vende rimedi erboristici e pozioni magiche. Maximilian è un giovane genio che combina conoscenza arcana con sapere botanico. Il suo negozio emana di aromi exotici e potenza magica.",razza:"Umano",genere:"Uomo",classe:"Mago"},
{nome:"Mehtaar Zar",desc:"Aarakocra, messaggero capo di un'associazione di consegne messaggi e spionaggio. Mehtaar è un essere alato che domina i cieli della città. Conosce i segreti di ogni famiglia importante grazie al suo lavoro come messaggero.",razza:"Aarakocra",genere:"Uomo",classe:""},
{nome:"Merlock",desc:"36 anni. Umano, Mastro birraio e locandiere della locanda principale della città. Merlock è un uomo affabile che conosce ogni cliente per nome e memoria. La sua locanda è il cuore sociale della comunità.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Mett Brunor",desc:"21 anni, tiefling, maschio, mastro costruttore. Mett è un giovane talento che progetta edifici innovativi per il regno. Ha una visione moderna dell'architettura e una passione per le strutture eleganti.",razza:"Tiefling",genere:"Uomo",classe:""},
{nome:"Mikalin Dimplecheek",desc:"32 anni, Halfling, maschio, Artefice fabbro da battaglia. Mikalin costruisce armature e armi magiche su ordinazione da nobili e guerra. È un maestro della sua arte, capace di incantare metallo e crearne forme straordinarie.",razza:"Halfling",genere:"Uomo",classe:"Artefice"},
{nome:"Mildred Cuorefiero",desc:"Umana 53 anni. Gestisce la locanda \"Il Boccale Incrinato\" con pugno di ferro e cuore di oro. Mildred è una matrona che non prende nonsense dai clienti ma che amichevolmente accoglie i viandanti stanchi.",razza:"Umano",genere:"Donna",classe:""},
{nome:"Milo Tealeaf",desc:"40 anni, Halfling, commerciante di spezie provenienti dalle terre lontane. Milo è un avventuriero in riposo che ha usato i suoi guadagni per aprire il negozio di spezie più raffinato del regno. Conosce le proprietà culinarie e medicinali di ogni spezia.",razza:"Halfling",genere:"Uomo",classe:""},
{nome:"Moona",desc:"Elfa dei boschi, 1200 anni, discendente della nobile famiglia Lavaris. Moona è una anziana elfa che ha visto il regno trasformarsi nel corso dei secoli. È una biblioteca vivente di storia e tradizione.",razza:"Elfo",genere:"Donna",classe:""},
{nome:"Munch",desc:"Nano archeologo che scava nei siti antichi attorno alla città in cerca di reperti. Munch è ossessionato da segreti sepolti e artefatti perduti. Ha una collezione privata di scoperte che lo rendono ricco e famoso tra gli eruditi.",razza:"Nano",genere:"Uomo",classe:""},
{nome:"Myklaar il Rosso",desc:"Goliath arcanista dai lunghi capelli rossi. Gestisce un negozio di articoli arcani nel cuore della città. Myklaar è un gigante intelligente che conosce la natura della magia profondamente. Il suo negozio è una caverna di meraviglie magiche.",razza:"Goliath",genere:"Uomo",classe:"Arcanista"},
{nome:"Na'ak",desc:"Goliath, maschio. Ex soldato ora garzone/buttafuori di locanda. Na'ak è un gigante dalla corporatura massiccia e dal cuore gentile. Ha visto battaglie orribili e ora preferisce la pace della locanda.",razza:"Goliath",genere:"Uomo",classe:"Guerriero"},
{nome:"Nesta \"Ombra Verde\"",desc:"Elfa dei boschi, Druida del circolo della Luna. Nomade e cacciatrice di taglie che non rimane in un luogo a lungo. Nesta è una creatura selvaggia, connessa profondamente ai cicli lunari e ai misteri della foresta.",razza:"Elfo",genere:"Donna",classe:"Druida"},
{nome:"Nikoras",desc:"Ex paladina/templare mezz'orca, salumiera. Ti disossa un crudo a mani nude. Nikoras è una donna di forza tremenda che ha abbandonato la vita militare per la pace della macelleria. Conserva l'onore e la disciplina nei suoi affari.",razza:"Mezz'orco",genere:"Donna",classe:"Paladina"},
{nome:"Nikolaj il Protettore",desc:"68 anni, umano, chierico della forgia. Ha edificato un tempio dedicato a Yondalla nel quartiere dei seminati. Nikolaj è un uomo pio che crede nel potere della comunità e della costruzione. Il suo tempio è un rifugio per i poveri.",razza:"Umano",genere:"Uomo",classe:"Chierico"},
{nome:"Nives Grey",desc:"Strega, umana. 28 anni. Gestisce una bottega da erborista nel quartiere più anziano della città. Nives è una praticante di magia naturale che utilizza erbe e rituali per guarire. Ha una reputazione di eccellenza e integrità.",razza:"Umano",genere:"Donna",classe:"Stregone"},
{nome:"Noha",desc:"Mezz'orchessa, 20 anni, artigiana. Crea oggetti sempre diversi e complessi che vendono ai collezionisti e agli artigiani. Noha è un genio creativo che può fare qualsiasi cosa con le mani.",razza:"Mezz'orco",genere:"Donna",classe:""},
{nome:"Obscurius",desc:"Dragonide Warlock Hexblade. Sicario costretto dalla sua falce magica a fare omicidi. Obscurius è una creatura malvagia legata a un'arma che lo controlla. È temuto e evitato da molti.",razza:"Dragonide",genere:"Uomo",classe:"Warlock"},
{nome:"Orso Maria",desc:"Apprendista mago che lavora sotto un mago più anziano della città. Orso Maria è entusiasta e dedito, con una affinità naturale per la magia evocatrice. Speranza nella gioventù della comunità magica.",razza:"Umano",genere:"Uomo",classe:"Mago"},
{nome:"Pamela",desc:"Nobildonna amante dei libri, direttrice della biblioteca cittadina. Pamela è una donna di rango che ha dedicato la sua vita all'apprendimento e alla preservazione della conoscenza. La biblioteca è la sua passione e il suo regno.",razza:"Umano",genere:"Donna",classe:"Mago"},
{nome:"Phealin Babanoi",desc:"Tiefling, 21 anni, maschio. Apprendista giornalista del regno che scrive articoli per il giornale cittadino. Phealin è giovane e idealista, determinato a raccontare la verità. A volte si mette in pericolo per una storia.",razza:"Tiefling",genere:"Uomo",classe:""},
{nome:"Phill Be'alla Sio",desc:"Umano. Lavora per la riscossione delle tasse per conto della corona. Phill è un uomo freddo e efficiente, temuto dai debitori e rispettato dal governo. Non ha amici ma ha efficienza.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Ramón Reven",desc:"Umano mago bibliotecario sui 30/35 che aiuta la direttrice della biblioteca. Ramón è un erudito gentile che conosce la posizione di ogni libro. Ha una memoria prodigiosa e una pazienza infinita con i ricercatori.",razza:"Umano",genere:"Uomo",classe:"Mago"},
{nome:"Rhutt Kor",desc:"Nano di 194 anni. Fabbro. Costantemente a petto nudo. Rhutt è una figura iconica della città, noto per la sua forza e il suo aspetto insolito. La sua fucina produce capolavori di metallurgia.",razza:"Nano",genere:"Uomo",classe:""},
{nome:"Rughdar Altocalice",desc:"Umano, 32 anni, guardia cittadina e mercenario che lavora per la paga. Rughdar è un combattente esperto con cicatrici di molte battaglie. Ha poco senso dell'onore ma è straordinariamente competente.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
{nome:"Selina Dreifus",desc:"Elfa dei boschi, druida del circolo della fame. Condivide l'anima con un wendigo. Selina è una creatura spaventosa e meravigliosa allo stesso tempo, legata a forze primitive della natura. È temuta e circondata di mistero.",razza:"Elfo",genere:"Donna",classe:"Druida"},
{nome:"Sir Andr D'Allegrez",desc:"26 anni. Addestratore di combattenti che prepara i giovani guerrieri per il servizio militare. Sir Andr è un cavaliere di rango che mantiene standard alti. La sua accademia produce i migliori guerrieri del regno.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
{nome:"Sirzechs Jailbreak",desc:"Tiefling locandiere. Gestisce la locanda \"Il Nido del Drago\" dove molti avventurieri si ritrovano. Sirzechs è un uomo affabile ma astuto, che sa tutto quello che succede nella città. La sua locanda è un punto di incontro cruciale.",razza:"Tiefling",genere:"Uomo",classe:""},
{nome:"Spakkabot 494",desc:"Forgiato juggernaut attivo da 89 anni. Buttafuori nella bisca locale. Spakkabot è una macchina di metallo e magia, praticamente indistruttibile. È silenzioso e efficiente nel suo lavoro.",razza:"Forgiato",genere:"Uomo",classe:""},
{nome:"Sssertisss Raw",desc:"32 anni, Lizardfolk. Fabbro che crea armi per la guardia cittadina e i guerrieri locali. Sssertisss è un artefice metodico e calmo, con la precisione della sua specie. Il suo accento sibilante è inconfondibile.",razza:"Lizardfolk",genere:"Uomo",classe:""},
{nome:"Standus Colimar Sinfurr",desc:"Elfo di 452 anni, archivista e bibliotecario che mantiene gli archivi storici della città. Standus è una figura antiquata ma rispettata, con una memoria straordinaria per i dettagli. Gli archivi sono il suo dominio assoluto.",razza:"Elfo",genere:"Uomo",classe:""},
{nome:"Stenar",desc:"Mezzorco mercenario. Intrattiene gli avventori con i suoi canti da scaldo nella locanda principale. Stenar è un narratore straordinario che sa come tenere il pubblico incantato. Le sue storie di battaglia e amore risuonano nei cuori dei bevitori.",razza:"Mezz'orco",genere:"Uomo",classe:""},
{nome:"Stephen Umbra",desc:"Mezzelfo custode e gestore di stazioni di trasporto passeggeri attraverso il regno. Stephen è un uomo efficiente che coordina il flusso di persone e merci. Ha una reputazione per l'affidabilità e la precisione.",razza:"Mezz'elfo",genere:"Uomo",classe:""},
{nome:"Strike",desc:"Warforged di 20 anni, Monaco Ranger. Lavora come postino del governo nella città. Strike è un essere sentiente di ferro e magia, dedito al suo lavoro. Ha una logica fredda ma è capace di sorprese emotive.",razza:"Warforged",genere:"Uomo",classe:"Monaco"},
{nome:"Thorgrim",desc:"Nano degli scudi, 205 anni. Addetto alla gestione della forgia principale della città. Thorgrim è un artigiano antico che conosce ogni segreto della lavorazione dei metalli. La sua autorità nella forgia è assoluta.",razza:"Nano",genere:"Uomo",classe:""},
{nome:"Torak Bearclaw",desc:"30 anni, Goliath. Guardia personale su commissione per nobili ricchi della città. Torak è un guerriero fedele che protegge i suoi clienti con dedizione feroce. Ha un codice d'onore personale rigido.",razza:"Goliath",genere:"Uomo",classe:"Guerriero"},
{nome:"Torth \"il Drago Artiglio\"",desc:"Artefice errante, 25 anni. Cerca oggetti per il suo maestro, un arcanista potente. Torth è un giovane talentuoso che costruisce e ripara oggetti magici. È sempre in viaggio, cercando i componenti rari che il suo maestro richiede.",razza:"Umano",genere:"Uomo",classe:"Artefice"},
{nome:"Ulkian Safforz",desc:"Un monello orfano di strada, umano, 15 anni. Ulkian è sveglio e scaltro, sempre un passo avanti ai problemi. Dorme nei vicoli della città e ruba per sopravvivere. Ha il potenziale di diventare qualcosa di più.",razza:"Umano",genere:"Uomo",classe:""},
{nome:"Varax",desc:"Monaco della forma astrale, dragonborn bianco, 27 anni. Artista di strada che esegue acrobazie straordinarie nelle piazze della città. Varax è una creatura disciplinata che canalizza l'energia attraverso il movimento. I bambini lo amano.",razza:"Dragonide",genere:"Uomo",classe:"Monaco"},
{nome:"Vert & Braas",desc:"Due coboldi gemelli ossessionati dalla realizzazione di oggetti in ossa. Creano ornamenti, armi e decorazioni che vendono nel loro piccolo negozio. Sono intelligenti e laboriosi, con un linguaggio sibilante affascinante.",razza:"Coboldo",genere:"Uomo",classe:""},
{nome:"Willow",desc:"Aasimar, bardo, proprietaria di una taverna dove si esibisce ogni sera. Willow è una creatura sovrumana di bellezza e grazia, con una voce che tocca l'anima. La sua taverna è il luogo più raffinato della città.",razza:"Aasimar",genere:"Donna",classe:"Bardo"},
{nome:"Xyravy",desc:"60 anni, Dragonborn d'Ottone, mendicante. Gestisce un piccolo orfanotrofio con i soldi che raccoglie mendicando. Xyravy è una creatura nobile ristretta alle circostanze, che dedica la sua vita ai bambini abbandonati. È amato dalla comunità.",razza:"Dragonide",genere:"Uomo",classe:""},
{nome:"Yama San",desc:"Monaco/samurai umano ritirato. Insegna nel suo dojo agli aspiranti guerrieri la disciplina e l'arte della spada. Yama San è una maestro antico che crede nel potere della tradizione e della ricerca personale.",razza:"Umano",genere:"Uomo",classe:"Monaco"},
{nome:"Yüki",desc:"22 anni, umano, maschio. Mago Bladesinger che combina arti marziali con magia arcana. Yüki è un praticante giovane e talentuoso di una disciplina rara. Sogna di diventare una leggenda.",razza:"Umano",genere:"Uomo",classe:"Mago"},
{nome:"Yushiro Koheda",desc:"21 anni, bardo, mezz'elfo. La sua musa è la gatta Akuma che lo accompagna sempre. Yushiro è un musicista sensibile che trovato ispirazione nella felina elegante. Le sue composizioni sono affascinanti e complesse.",razza:"Mezz'elfo",genere:"Uomo",classe:"Bardo"},
{nome:"Zessil",desc:"Yuan-Ti, femmina, 33 anni, Warlock legata a un antico potere primordiale. Zessil è una creatura dal sangue freddo che commercia con forze oscure. È temuta e misteriosa, con intenti sempre dubbi.",razza:"Yuan-Ti",genere:"Donna",classe:"Warlock"},
{nome:"Zubi Ignis",desc:"Umano, pistolero. Ingaggiato solo per missioni stupide e pericolose che pagano poco. Zubi è un avventuriero senza sorte, sempre al limite della sopravvivenza. Ha una reputazione di caos e esili fortunate.",razza:"Umano",genere:"Uomo",classe:""}
];

npcs.sort((a,b)=>a.nome.localeCompare(b.nome,'it'));

const races=[...new Set(npcs.map(n=>n.razza).filter(Boolean))].sort((a,b)=>a.localeCompare(b,'it'));
const genders=[...new Set(npcs.map(n=>n.genere).filter(Boolean))].sort((a,b)=>a.localeCompare(b,'it'));
const classes=[...new Set(npcs.map(n=>n.classe).filter(Boolean))].sort((a,b)=>a.localeCompare(b,'it'));

const activeFilters={razza:new Set(),genere:new Set(),classe:new Set()};
let searchQuery='';
let filtered=[...npcs];
let currentSort=null;

function buildTags(container,items,filterKey){
  items.forEach(item=>{
    const tag=document.createElement('span');
    tag.className='filter-tag';
    tag.textContent=item;
    tag.addEventListener('click',()=>{
      if(activeFilters[filterKey].has(item)){activeFilters[filterKey].delete(item);tag.classList.remove('active')}
      else{activeFilters[filterKey].add(item);tag.classList.add('active')}
      applyFilters();
    });
    container.appendChild(tag);
  });
}

buildTags(document.getElementById('filter-race'),races,'razza');
buildTags(document.getElementById('filter-gender'),genders,'genere');
buildTags(document.getElementById('filter-class'),classes,'classe');

function extractAgeNumber(desc){
  const match=desc.match(/(\d+)\s*(?:anni|years|\+)/i);
  return match?parseInt(match[1]):Infinity;
}

function applyFilters(){
  const q=searchQuery.toLowerCase();
  filtered=npcs.filter(n=>{
    if(activeFilters.razza.size&&!activeFilters.razza.has(n.razza))return false;
    if(activeFilters.genere.size&&!activeFilters.genere.has(n.genere))return false;
    if(activeFilters.classe.size&&!activeFilters.classe.has(n.classe))return false;
    if(q){
      const hay=(n.nome+' '+n.desc+' '+n.razza+' '+n.classe).toLowerCase();
      if(!hay.includes(q))return false;
    }
    return true;
  });
  if(currentSort)applySortToFiltered();
  renderList();
}

function applySortToFiltered(){
  switch(currentSort){
    case 'name-asc':filtered.sort((a,b)=>a.nome.localeCompare(b.nome,'it'));break;
    case 'name-desc':filtered.sort((a,b)=>b.nome.localeCompare(a.nome,'it'));break;
    case 'age-asc':filtered.sort((a,b)=>extractAgeNumber(a.desc)-extractAgeNumber(b.desc));break;
    case 'age-desc':filtered.sort((a,b)=>extractAgeNumber(b.desc)-extractAgeNumber(a.desc));break;
  }
}

function renderList(){
  const container=document.getElementById('npc-list');
  container.innerHTML='';
  document.getElementById('page-counter').textContent=filtered.length+' schede';
  if(filtered.length===0){
    container.innerHTML='<p class="text-center py-8" style="color:#c9a86a;font-style:italic">Nessun risultato. Prova a cambiare i filtri.</p>';
    return;
  }
  filtered.forEach(npc=>{
    const card=document.createElement('div');
    card.className='npc-card';
    const age=npc.desc.match(/(\d+)\s*(?:anni|years|\+)/i);
    const ageStr=age?age[1]+' anni':'';
    card.innerHTML=`
      <h3 style="color:#5a3000;font-weight:700;font-size:1.1rem;margin-bottom:0.3rem">${npc.nome}</h3>
      <p style="color:#6b4e1f;font-size:0.8rem;margin-bottom:0.4rem">${[npc.razza,npc.classe,ageStr].filter(Boolean).join(' · ')}</p>
      <p style="color:#3d2b10;font-size:0.85rem;line-height:1.5">${npc.desc}</p>
    `;
    container.appendChild(card);
  });
}

const searchInput=document.getElementById('search-input');
searchInput.addEventListener('input',e=>{searchQuery=e.target.value;applyFilters()});

document.getElementById('reset-btn').addEventListener('click',()=>{
  searchQuery='';searchInput.value='';
  activeFilters.razza.clear();activeFilters.genere.clear();activeFilters.classe.clear();
  document.querySelectorAll('.filter-tag.active').forEach(t=>t.classList.remove('active'));
  currentSort=null;
  clearSortActive();
  applyFilters();
});

const sortBtns=document.querySelectorAll('.sort-btn');
function clearSortActive(){sortBtns.forEach(b=>b.classList.remove('active'))}

document.getElementById('sort-name-asc').addEventListener('click',function(){clearSortActive();this.classList.add('active');currentSort='name-asc';applySortToFiltered();renderList()});
document.getElementById('sort-name-desc').addEventListener('click',function(){clearSortActive();this.classList.add('active');currentSort='name-desc';applySortToFiltered();renderList()});
document.getElementById('sort-age-asc').addEventListener('click',function(){clearSortActive();this.classList.add('active');currentSort='age-asc';applySortToFiltered();renderList()});
document.getElementById('sort-age-desc').addEventListener('click',function(){clearSortActive();this.classList.add('active');currentSort='age-desc';applySortToFiltered();renderList()});

renderList();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'a13bf4cba1ebfc3e',t:'MTc4MjgwOTc3MC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script>
</body></html>
