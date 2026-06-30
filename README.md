<!doctype html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Regno di Haryel</title>
    <script src="https://cdn.tailwindcss.com/3.4.17"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cardo:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Cardo', serif; background-color: #fdfaf6; color: #1a0f05; }
        .npc-card { background: linear-gradient(160deg,#f5e6c8 0%,#e8d4a8 30%,#dbc492 70%,#cdb07a 100%); border: 1px solid #a08050; box-shadow: inset 0 0 30px rgba(120,80,30,0.15),0 2px 8px rgba(0,0,0,0.3); position:relative; padding:1.25rem 1.5rem; border-radius:6px }
        .filter-tag { padding:0.25rem 0.7rem; border-radius:4px; cursor:pointer; border:1px solid #a08050; background:rgba(200,170,120,0.15); color:#c9a86a; font-size:0.8rem; transition:all 0.2s; user-select:none }
        .filter-tag:hover { background:rgba(200,170,120,0.3) }
        .filter-tag.active { background:#a08050; color:#2c1e0f; font-weight:700 }
        .sort-btn { padding:0.25rem 0.75rem; border-radius:4px; cursor:pointer; border:1px solid #a08050; font-size:0.75rem; transition:all 0.2s }
        .sort-btn.active { background:#c9a86a; color:#1a0f05; font-weight:700 }
        .search-input { background:rgba(30,20,10,0.6); border:1px solid #a08050; color:#e8d4a8; padding:0.5rem 1rem; border-radius:4px; font-family:'Cardo',serif; outline:none; width:100% }
    </style>
</head>
<body class="min-h-screen p-4 pt-8">
    <header class="text-center mb-6 max-w-3xl mx-auto px-4">
        <h1 class="text-3xl md:text-4xl tracking-widest mb-3">Regno di Haryel</h1>
        <p class="text-sm md:text-base leading-relaxed opacity-90">Archivio Ufficiale dei Cittadini</p>
    </header>

    <section class="w-full max-w-3xl mx-auto mb-4">
        <div class="flex gap-2 mb-4">
            <input type="text" id="search-input" class="search-input" placeholder="Cerca nome, razza, classe o descrizione">
            <button id="reset-btn" class="bg-[#a08050] text-[#1a0f05] px-4 py-2 rounded text-sm font-bold cursor-pointer">Reset</button>
        </div>
        <div class="flex flex-wrap justify-center gap-2 mb-4">
            <button id="sort-name-asc" class="sort-btn">A-Z</button>
            <button id="sort-name-desc" class="sort-btn">Z-A</button>
            <button id="sort-age-asc" class="sort-btn">Età ↑</button>
            <button id="sort-age-desc" class="sort-btn">Età ↓</button>
        </div>
        <div id="filter-race" class="flex flex-wrap gap-2 mb-2"></div>
        <div id="filter-gender" class="flex flex-wrap gap-2 mb-2"></div>
        <div id="filter-class" class="flex flex-wrap gap-2 mb-2"></div>
    </section>

    <p id="page-counter" class="text-center text-sm opacity-70 mb-4"></p>
    <main id="npc-list" class="w-full max-w-3xl mx-auto space-y-4 pb-8"></main>

    <script>
        const npcs = [
            {nome:"Akra della Zanna",desc:"Dragonide blu, femmina, 30 anni. Fabbro!",razza:"Dragonide",genere:"Donna",classe:""},
            {nome:"Albina Sermane",desc:"Tiefling ritualista di 32 anni.",razza:"Tiefling",genere:"Donna",classe:"Ritualista"},
            {nome:"Alexander Ulkior",desc:"32 anni, mezzorco, Monaco-barbaro.",razza:"Mezz'orco",genere:"Uomo",classe:"Monaco"},
            {nome:"Alexaeus",desc:"Mezz'elfo, 75 anni, fabbro e arcanista.",razza:"Mezz'elfo",genere:"Uomo",classe:"Arcanista"},
            {nome:"Alfred Von Ruprecht",desc:"Umano, età ignota, Imprenditore.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Andrix Ramospezzato",desc:"Kenku ranger, 15 anni.",razza:"Kenku",genere:"Uomo",classe:"Ranger"},
            {nome:"Arakk Bloodyhammer",desc:"75 anni, nano eldritch knight.",razza:"Nano",genere:"Uomo",classe:"Guerriero"},
            {nome:"Arturo Locke Harrow",desc:"30 anni umano, pirata contrabbandiere.",razza:"Umano",genere:"Uomo",classe:"Ladro"},
            {nome:"Aurelion Solis",desc:"Dragonide Blu, Stregone Aberrante.",razza:"Dragonide",genere:"Uomo",classe:"Stregone"},
            {nome:"Azog",desc:"Mezz'Orco, ritirato da un passato da marinaio.",razza:"Mezz'orco",genere:"Uomo",classe:""},
            {nome:"BarbaBong",desc:"Nano chierico, dominio della Guerra, 90 anni.",razza:"Nano",genere:"Uomo",classe:"Chierico"},
            {nome:"Beiren",desc:"32 anni, Harengon. Chierico del crepuscolo.",razza:"Harengon",genere:"Uomo",classe:"Chierico"},
            {nome:"Belpher Davbul \"Baffone\"",desc:"Halfling piede lesto, 50-55 anni.",razza:"Halfling",genere:"Uomo",classe:""},
            {nome:"Benjen Blackdoor",desc:"Custode del museo, umano ladro, 37 anni.",razza:"Umano",genere:"Uomo",classe:"Ladro"},
            {nome:"Brenjos",desc:"Loxodonte maschio di 350 anni.",razza:"Loxodonte",genere:"Uomo",classe:""},
            {nome:"Brikelberry",desc:"Gnomo Insegnante di 50 anni.",razza:"Gnomo",genere:"Uomo",classe:""},
            {nome:"Bucciaratiilgrande — Ro",desc:"Giovane adulto, Grung, maschio.",razza:"Grung",genere:"Uomo",classe:"Monaco"},
            {nome:"Cado Presye",desc:"Umana druida, 55-65 anni.",razza:"Umano",genere:"Donna",classe:"Druida"},
            {nome:"Caelynn Alfhard",desc:"Elfa del bosco stregona.",razza:"Elfo",genere:"Donna",classe:"Stregone"},
            {nome:"Cailan Sage",desc:"Umano di 34 anni, venditore di tessuti.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Carl O'sea",desc:"Dragonide Gemmato, Medico.",razza:"Dragonide",genere:"Uomo",classe:""},
            {nome:"Carm — Kaermyn",desc:"Elfo alto, 2000 anni, Mago.",razza:"Elfo",genere:"Uomo",classe:"Mago"},
            {nome:"Carys",desc:"Tabaxi tigre, gigolò.",razza:"Tabaxi",genere:"Uomo",classe:""},
            {nome:"Cheesis Godstrength",desc:"Umano erudito, inventore.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Claire",desc:"Maga umana, 30 anni.",razza:"Umano",genere:"Donna",classe:"Mago"},
            {nome:"Clea Sithis",desc:"100+ anni, Damphir, Artefice.",razza:"Damphir",genere:"Donna",classe:"Artefice"},
            {nome:"Cora Gentrield",desc:"27 anni, halfling curatrice.",razza:"Halfling",genere:"Donna",classe:""},
            {nome:"Cornelia",desc:"Tiefling, falconiera, ranger.",razza:"Tiefling",genere:"Donna",classe:"Ranger"},
            {nome:"Custode del Nexus",desc:"Umano enigmmatico.",razza:"Umano",genere:"",classe:""},
            {nome:"Davide — Gurt Kappenbox",desc:"Maniscalco, umano.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Dodger",desc:"Drow preadolescente, 10 anni.",razza:"Drow",genere:"Uomo",classe:"Ladro"},
            {nome:"Dorian",desc:"Bardo mezzelfo.",razza:"Mezz'elfo",genere:"Uomo",classe:"Bardo"},
            {nome:"Drahmor D. Terzo",desc:"Dragonide Paladino, 128 anni.",razza:"Dragonide",genere:"Uomo",classe:"Paladino"},
            {nome:"Drew Hart",desc:"30 anni, umano scrivano.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Elyon Aldaron",desc:"Elfo alto, fabbro.",razza:"Elfo",genere:"Uomo",classe:""},
            {nome:"Emerald Huntwood",desc:"30 anni, cangiante.",razza:"Cangiante",genere:"Uomo",classe:"Ranger"},
            {nome:"Eos Glimmerfield",desc:"20 anni, elfa druida.",razza:"Elfo",genere:"Donna",classe:"Druida"},
            {nome:"Erim Holkol",desc:"Halfling costruttore trappole.",razza:"Halfling",genere:"Uomo",classe:""},
            {nome:"Estiel",desc:"Elfo, 2900 anni, guerriero.",razza:"Elfo",genere:"Uomo",classe:"Guerriero"},
            {nome:"Fabrizio — Kallax",desc:"Ghitzerai fornaio, 120 anni.",razza:"Ghitzerai",genere:"Uomo",classe:""},
            {nome:"Finn Morningstar",desc:"Umano guerriero, 21 anni.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
            {nome:"Flavius Aribaldov",desc:"Umano, 40 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Fofò Purtùsu",desc:"70 anni, Umano Paladino.",razza:"Umano",genere:"Uomo",classe:"Paladino"},
            {nome:"Franco",desc:"Umano carpentiere, 45 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Galius il Rosso",desc:"Stregone, mezza età.",razza:"Umano",genere:"Uomo",classe:"Stregone"},
            {nome:"Gash Purpuris",desc:"25 anni, mezz'orco.",razza:"Mezz'orco",genere:"Uomo",classe:""},
            {nome:"Gelica",desc:"Drow, giovane donna, ceramista.",razza:"Drow",genere:"Donna",classe:""},
            {nome:"Ghan Nesbitt",desc:"Umano cacciatore, 26 anni.",razza:"Umano",genere:"Uomo",classe:"Ranger"},
            {nome:"Goran",desc:"Mezzorco infermiere.",razza:"Mezz'orco",genere:"Uomo",classe:""},
            {nome:"Hulkvard Barbagrigia",desc:"Nano, barbaro, 130 anni.",razza:"Nano",genere:"Uomo",classe:"Barbaro"},
            {nome:"Icy Hurricane",desc:"30 anni, dragonide druida.",razza:"Dragonide",genere:"Donna",classe:"Druida"},
            {nome:"Ishika Tomari",desc:"Tabaxi, 36 anni, ladra.",razza:"Tabaxi",genere:"Donna",classe:"Ladro"},
            {nome:"Jack Whitewinter",desc:"33 anni, Oni, guerriero.",razza:"Oni",genere:"Uomo",classe:"Guerriero"},
            {nome:"Jana Serpefiero",desc:"29 anni, Tiefling.",razza:"Tiefling",genere:"Donna",classe:""},
            {nome:"Jorgha di Valdombra",desc:"58 anni, mezzelfa barda.",razza:"Mezz'elfo",genere:"Donna",classe:"Bardo"},
            {nome:"Josef Lambari",desc:"Umano, 21 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Kestel",desc:"Kender, 15 anni.",razza:"Kender",genere:"Donna",classe:""},
            {nome:"Kinson",desc:"Elfo, mastro birraio.",razza:"Elfo",genere:"Uomo",classe:""},
            {nome:"Kliarn Scaglia d'Argento",desc:"26 anni, dragonide.",razza:"Dragonide",genere:"Uomo",classe:""},
            {nome:"Kurzum Fall",desc:"Umano stregone, 33 anni.",razza:"Umano",genere:"Uomo",classe:"Stregone"},
            {nome:"Lacrimis Lakeblue",desc:"Genasi acqua, 30 anni.",razza:"Genasi",genere:"Uomo",classe:"Chierico"},
            {nome:"Leif Dagsson",desc:"25 anni, Umano bardo.",razza:"Umano",genere:"Uomo",classe:"Bardo"},
            {nome:"Loki",desc:"Ladra mezzelfa, 29 anni.",razza:"Mezz'elfo",genere:"Donna",classe:"Ladro"},
            {nome:"Lorimbur Barbargento",desc:"Nano, 110 anni.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Lucilla",desc:"Mezzelfa, 80 anni.",razza:"Mezz'elfo",genere:"Donna",classe:""},
            {nome:"Luka Russor",desc:"Nano, 26 anni.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Maximilian Regulus",desc:"Mago, 24 anni.",razza:"Umano",genere:"Uomo",classe:"Mago"},
            {nome:"Mehtaar Zar",desc:"Aarakocra.",razza:"Aarakocra",genere:"Uomo",classe:""},
            {nome:"Merlock",desc:"Umano, 36 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Mett Brunor",desc:"21 anni, tiefling.",razza:"Tiefling",genere:"Uomo",classe:""},
            {nome:"Mikalin Dimplecheek",desc:"32 anni, Halfling Artefice.",razza:"Halfling",genere:"Uomo",classe:"Artefice"},
            {nome:"Mildred Cuorefiero",desc:"Umana, 53 anni.",razza:"Umano",genere:"Donna",classe:""},
            {nome:"Milo Tealeaf",desc:"40 anni, Halfling.",razza:"Halfling",genere:"Uomo",classe:""},
            {nome:"Moona",desc:"Elfa, 1200 anni.",razza:"Elfo",genere:"Donna",classe:""},
            {nome:"Munch",desc:"Nano archeologo.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Myklaar il Rosso",desc:"Goliath arcanista.",razza:"Goliath",genere:"Uomo",classe:"Arcanista"},
            {nome:"Na'ak",desc:"Goliath, guerriero.",razza:"Goliath",genere:"Uomo",classe:"Guerriero"},
            {nome:"Nesta Ombra Verde",desc:"Elfa, druida.",razza:"Elfo",genere:"Donna",classe:"Druida"},
            {nome:"Nikoras",desc:"Mezz'orco paladina.",razza:"Mezz'orco",genere:"Donna",classe:"Paladina"},
            {nome:"Nikolaj il Protettore",desc:"68 anni, umano chierico.",razza:"Umano",genere:"Uomo",classe:"Chierico"},
            {nome:"Nives Grey",desc:"Strega, 28 anni.",razza:"Umano",genere:"Donna",classe:"Stregone"},
            {nome:"Noha",desc:"Mezz'orchessa, 20 anni.",razza:"Mezz'orco",genere:"Donna",classe:""},
            {nome:"Obscurius",desc:"Dragonide Warlock.",razza:"Dragonide",genere:"Uomo",classe:"Warlock"},
            {nome:"Orso Maria",desc:"Apprendista mago.",razza:"Umano",genere:"Uomo",classe:"Mago"},
            {nome:"Pamela",desc:"Nobildonna maga.",razza:"Umano",genere:"Donna",classe:"Mago"},
            {nome:"Phealin Babanoi",desc:"Tiefling, 21 anni.",razza:"Tiefling",genere:"Uomo",classe:""},
            {nome:"Phill Be'alla Sio",desc:"Umano.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Ramón Reven",desc:"Mago bibliotecario, 30/35.",razza:"Umano",genere:"Uomo",classe:"Mago"},
            {nome:"Rhutt Kor",desc:"Nano, 194 anni.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Rughdar Altocalice",desc:"Umano, 32 anni.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
            {nome:"Selina Dreifus",desc:"Elfa druida.",razza:"Elfo",genere:"Donna",classe:"Druida"},
            {nome:"Sir Andr D'Allegrez",desc:"26 anni, guerriero.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
            {nome:"Sirzechs Jailbreak",desc:"Tiefling locandiere.",razza:"Tiefling",genere:"Uomo",classe:""},
            {nome:"Spakkabot 494",desc:"Forgiato, 89 anni.",razza:"Forgiato",genere:"Uomo",classe:""},
            {nome:"Sssertisss Raw",desc:"32 anni, Lizardfolk.",razza:"Lizardfolk",genere:"Uomo",classe:""},
            {nome:"Standus Colimar Sinfurr",desc:"Elfo, 452 anni.",razza:"Elfo",genere:"Uomo",classe:""},
            {nome:"Stenar",desc:"Mezzorco.",razza:"Mezz'orco",genere:"Uomo",classe:""},
            {nome:"Stephen Umbra",desc:"Mezzelfo.",razza:"Mezz'elfo",genere:"Uomo",classe:""},
            {nome:"Strike",desc:"Warforged, 20 anni.",razza:"Warforged",genere:"Uomo",classe:"Monaco"},
            {nome:"Thorgrim",desc:"Nano, 205 anni.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Torak Bearclaw",desc:"30 anni, Goliath.",razza:"Goliath",genere:"Uomo",classe:"Guerriero"},
            {nome:"Torth",desc:"Artefice, 25 anni.",razza:"Umano",genere:"Uomo",classe:"Artefice"},
            {nome:"Ulkian Safforz",desc:"Orfano, 15 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Varax",desc:"Dragonide, 27 anni.",razza:"Dragonide",genere:"Uomo",classe:"Monaco"},
            {nome:"Vert & Braas",desc:"Coboldi gemelli.",razza:"Coboldo",genere:"Uomo",classe:""},
            {nome:"Willow",desc:"Aasimar barda.",razza:"Aasimar",genere:"Donna",classe:"Bardo"},
            {nome:"Xyravy",desc:"Dragonide, 60 anni.",razza:"Dragonide",genere:"Uomo",classe:""},
            {nome:"Yama San",desc:"Monaco umano.",razza:"Umano",genere:"Uomo",classe:"Monaco"},
            {nome:"Yüki",desc:"Mago Bladesinger, 22 anni.",razza:"Umano",genere:"Uomo",classe:"Mago"},
            {nome:"Yushiro Koheda",desc:"Bardo, 21 anni.",razza:"Mezz'elfo",genere:"Uomo",classe:"Bardo"},
            {nome:"Zessil",desc:"Yuan-Ti, 33 anni.",razza:"Yuan-Ti",genere:"Donna",classe:"Warlock"},
            {nome:"Zubi Ignis",desc:"Umano pistolero.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Do'",desc:"Medico templare.",razza:"Umano",genere:"Uomo",classe:"Chierico"},
            {nome:"Ek Ki Me",desc:"Vagabondo.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Insengard e Urtu",desc:"Guardia cittadina.",razza:"Umano",genere:"Uomo",classe:"Guerriero"}
        ];

        // LOGICA JS (copia da qui in poi dal tuo script originale)
        npcs.sort((a,b)=>a.nome.localeCompare(b.nome,'it'));
        const races=[...new Set(npcs.map(n=>n.razza).filter(Boolean))].sort((a,b)=>a.localeCompare(b,'it'));
        const genders=[...new Set(npcs.map(n=>n.genere).filter(Boolean))].sort((a,b)=>a.localeCompare(b,'it'));
        const classes=[...new Set(npcs.map(n=>n.classe).filter(Boolean))].sort((a,b)=>a.localeCompare(b,'it'));
        const activeFilters={razza:new Set(),genere:new Set(),classe:new Set()};
        let searchQuery='';
        let filtered=[...npcs];

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
            renderList();
        }

        function renderList(){
            const container=document.getElementById('npc-list');
            container.innerHTML='';
            document.getElementById('page-counter').textContent=filtered.length+' schede';
            filtered.forEach(npc=>{
                const card=document.createElement('div');
                card.className='npc-card';
                card.innerHTML=`<h3 class="font-bold">${npc.nome}</h3><p class="text-sm">${[npc.razza,npc.classe].filter(Boolean).join(' · ')}</p><p class="mt-2 text-sm">${npc.desc}</p>`;
                container.appendChild(card);
            });
        }

        document.getElementById('search-input').addEventListener('input',e=>{searchQuery=e.target.value;applyFilters()});
        document.getElementById('reset-btn').addEventListener('click',()=>{
            searchQuery=''; document.getElementById('search-input').value='';
            activeFilters.razza.clear();activeFilters.genere.clear();activeFilters.classe.clear();
            document.querySelectorAll('.filter-tag.active').forEach(t=>t.classList.remove('active'));
            applyFilters();
        });

        renderList();
    </script>
</body>
</html>
