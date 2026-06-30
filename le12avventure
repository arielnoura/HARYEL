<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Regno di Haryel</title>
    <script src="https://cdn.tailwindcss.com/3.4.17"></script>
    <link href="https://fonts.googleapis.com/css2?family=Cardo:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Cardo', serif; background: linear-gradient(160deg, #1a0f05, #2c1e0f, #0f0a04); color: #c9a86a; min-height: 100vh; padding-bottom: 2rem; }
        .npc-card { background: linear-gradient(160deg, #f5e6c8 0%, #e8d4a8 30%, #dbc492 70%, #cdb07a 100%); color: #1a0f05; border: 1px solid #a08050; padding: 1.25rem; border-radius: 6px; box-shadow: 0 2px 8px rgba(0,0,0,0.3); }
        .filter-tag { padding: 0.25rem 0.7rem; border-radius: 4px; cursor: pointer; border: 1px solid #a08050; color: #c9a86a; font-size: 0.8rem; transition: all 0.2s; user-select: none; }
        .filter-tag.active { background: #a08050; color: #1a0f05; font-weight: 700; }
        .sort-btn { padding: 0.25rem 0.75rem; border-radius: 4px; cursor: pointer; border: 1px solid #a08050; color: #c9a86a; font-size: 0.75rem; transition: all 0.2s; }
        .sort-btn.active { background: #c9a86a; color: #1a0f05; font-weight: 700; }
        .search-input { background: rgba(30,20,10,0.6); border: 1px solid #a08050; color: #e8d4a8; padding: 0.5rem 1rem; border-radius: 4px; width: 100%; outline: none; }
    </style>
</head>
<body class="p-4 pt-8">
    <header class="text-center mb-8 max-w-3xl mx-auto">
        <h1 class="text-4xl tracking-widest mb-3 font-bold text-[#c9a86a]">Regno di Haryel</h1>
        <p class="text-[#a08050]">Archivio Ufficiale dei Personaggi</p>
    </header>

    <section class="w-full max-w-3xl mx-auto mb-6">
        <div class="flex gap-2 mb-4">
            <input type="text" id="search-input" class="search-input" placeholder="Cerca nome, razza, classe o descrizione...">
            <button id="reset-btn" class="px-4 py-2 rounded text-sm font-bold bg-[#a08050] text-[#1a0f05]">Reset</button>
        </div>
        <div class="flex flex-wrap justify-center gap-2 mb-4">
            <button id="sort-name-asc" class="sort-btn">Nome A→Z</button>
            <button id="sort-name-desc" class="sort-btn">Nome Z→A</button>
            <button id="sort-age-asc" class="sort-btn">Età ↑</button>
            <button id="sort-age-desc" class="sort-btn">Età ↓</button>
        </div>
        <div id="filter-race" class="flex flex-wrap gap-2 mb-2"></div>
        <div id="filter-gender" class="flex flex-wrap gap-2 mb-2"></div>
        <div id="filter-class" class="flex flex-wrap gap-2 mb-2"></div>
    </section>

    <p id="page-counter" class="text-center opacity-70 mb-4 text-[#c9a86a]"></p>
    <main id="npc-list" class="w-full max-w-3xl mx-auto space-y-4"></main>

    <script>
        const npcs = [
            {nome:"Akra della Zanna",desc:"Dragonide blu, femmina, 30 anni. Fabbro!",razza:"Dragonide",genere:"Donna",classe:""},
            {nome:"Albina Sermane",desc:"Tiefling ritualista, 32 anni.",razza:"Tiefling",genere:"Donna",classe:"Ritualista"},
            {nome:"Alexander Ulkior",desc:"32 anni, mezzorco, Monaco-barbaro.",razza:"Mezz'orco",genere:"Uomo",classe:"Monaco"},
            {nome:"Alexaeus",desc:"Mezz'elfo, 75 anni, fabbro e arcanista.",razza:"Mezz'elfo",genere:"Uomo",classe:"Arcanista"},
            {nome:"Alfred Von Ruprecht",desc:"Umano, età ignota, Imprenditore.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Andrix Ramospezzato",desc:"Kenku ranger, 15 anni.",razza:"Kenku",genere:"Uomo",classe:"Ranger"},
            {nome:"Arakk Bloodyhammer",desc:"75 anni, nano, Guerriero.",razza:"Nano",genere:"Uomo",classe:"Guerriero"},
            {nome:"Arturo Locke Harrow",desc:"30 anni umano, pirata.",razza:"Umano",genere:"Uomo",classe:"Ladro"},
            {nome:"Aurelion Solis",desc:"Dragonide Blu, Stregone Aberrante.",razza:"Dragonide",genere:"Uomo",classe:"Stregone"},
            {nome:"Azog",desc:"Mezz'Orco, ex marinaio.",razza:"Mezz'orco",genere:"Uomo",classe:""},
            {nome:"BarbaBong",desc:"Nano chierico, 90 anni.",razza:"Nano",genere:"Uomo",classe:"Chierico"},
            {nome:"Beiren",desc:"32 anni, Harengon. Chierico.",razza:"Harengon",genere:"Uomo",classe:"Chierico"},
            {nome:"Belpher Davbul \"Baffone\"",desc:"Halfling, 50-55 anni.",razza:"Halfling",genere:"Uomo",classe:""},
            {nome:"Benjen Blackdoor",desc:"Umano ladro, 37 anni.",razza:"Umano",genere:"Uomo",classe:"Ladro"},
            {nome:"Brenjos",desc:"Loxodonte, 350 anni.",razza:"Loxodonte",genere:"Uomo",classe:""},
            {nome:"Brikelberry",desc:"Gnomo insegnante, 50 anni.",razza:"Gnomo",genere:"Uomo",classe:""},
            {nome:"Bucciaratiilgrande — Ro",desc:"Giovane adulto, Grung.",razza:"Grung",genere:"Uomo",classe:"Monaco"},
            {nome:"Cado Presye",desc:"Umana druida, 55-65 anni.",razza:"Umano",genere:"Donna",classe:"Druida"},
            {nome:"Caelynn Alfhard",desc:"Elfa del bosco stregona.",razza:"Elfo",genere:"Donna",classe:"Stregone"},
            {nome:"Cailan Sage",desc:"Umano di 34 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Carl O'sea",desc:"Dragonide, Medico.",razza:"Dragonide",genere:"Uomo",classe:""},
            {nome:"Carm — Kaermyn",desc:"Elfo alto, 2000 anni.",razza:"Elfo",genere:"Uomo",classe:"Mago"},
            {nome:"Carys",desc:"Tabaxi, gigolò.",razza:"Tabaxi",genere:"Uomo",classe:""},
            {nome:"Cheesis Godstrength",desc:"Umano erudito.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Claire",desc:"Maga umana, 30 anni.",razza:"Umano",genere:"Donna",classe:"Mago"},
            {nome:"Clea Sithis",desc:"100+ anni, Damphir, Artefice.",razza:"Damphir",genere:"Donna",classe:"Artefice"},
            {nome:"Cora Gentrield",desc:"27 anni, halfling.",razza:"Halfling",genere:"Donna",classe:""},
            {nome:"Cornelia",desc:"Tiefling, ranger.",razza:"Tiefling",genere:"Donna",classe:"Ranger"},
            {nome:"Custode del Nexus",desc:"Umano, età ignota.",razza:"Umano",genere:"",classe:""},
            {nome:"Davide — Gurt Kappenbox",desc:"Maniscalco, 40 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Dodger",desc:"Drow, 10 anni.",razza:"Drow",genere:"Uomo",classe:"Ladro"},
            {nome:"Do'",desc:"Medico templare, umano.",razza:"Umano",genere:"Uomo",classe:"Chierico"},
            {nome:"Dorian",desc:"Bardo mezzelfo.",razza:"Mezz'elfo",genere:"Uomo",classe:"Bardo"},
            {nome:"Drahmor D. Terzo",desc:"Dragonide Paladino, 128 anni.",razza:"Dragonide",genere:"Uomo",classe:"Paladino"},
            {nome:"Drew Hart",desc:"Umano scrivano, 30 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Ek Ki Me",desc:"Vagabondo umano.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Elyon Aldaron",desc:"Elfo alto, fabbro.",razza:"Elfo",genere:"Uomo",classe:""},
            {nome:"Emerald Huntwood",desc:"30 anni, cangiante.",razza:"Cangiante",genere:"Uomo",classe:"Ranger"},
            {nome:"Eos Glimmerfield",desc:"20 anni, elfa druida.",razza:"Elfo",genere:"Donna",classe:"Druida"},
            {nome:"Erim Holkol",desc:"Halfling, 40 anni.",razza:"Halfling",genere:"Uomo",classe:""},
            {nome:"Estiel",desc:"Elfo, 2900 anni.",razza:"Elfo",genere:"Uomo",classe:"Guerriero"},
            {nome:"Fabrizio — Kallax",desc:"Ghitzerai, 120 anni.",razza:"Ghitzerai",genere:"Uomo",classe:""},
            {nome:"Finn Morningstar",desc:"Umano, 21 anni.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
            {nome:"Flavius Aribaldov",desc:"Umano, 40 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Fofò Purtùsu",desc:"Umano, 70 anni.",razza:"Umano",genere:"Uomo",classe:"Paladino"},
            {nome:"Franco",desc:"Umano, 45 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Galius il Rosso",desc:"Stregone, mezza età.",razza:"Umano",genere:"Uomo",classe:"Stregone"},
            {nome:"Gash Purpuris",desc:"Mezz'orco, 25 anni.",razza:"Mezz'orco",genere:"Uomo",classe:""},
            {nome:"Gelica",desc:"Drow, donna.",razza:"Drow",genere:"Donna",classe:""},
            {nome:"Ghan Nesbitt",desc:"Umano, 26 anni.",razza:"Umano",genere:"Uomo",classe:"Ranger"},
            {nome:"Goran",desc:"Mezz'orco gentile.",razza:"Mezz'orco",genere:"Uomo",classe:""},
            {nome:"Hulkvard Barbagrigia",desc:"Nano, 130 anni.",razza:"Nano",genere:"Uomo",classe:"Barbaro"},
            {nome:"Icy Hurricane",desc:"Dragonide, 30 anni.",razza:"Dragonide",genere:"Donna",classe:"Druida"},
            {nome:"Insengard e Urtu",desc:"Guardia cittadina.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
            {nome:"Ishika Tomari",desc:"Tabaxi, 36 anni.",razza:"Tabaxi",genere:"Donna",classe:"Ladro"},
            {nome:"Jack Whitewinter",desc:"Oni, 33 anni.",razza:"Oni",genere:"Uomo",classe:"Guerriero"},
            {nome:"Jana Serpefiero",desc:"Tiefling, 29 anni.",razza:"Tiefling",genere:"Donna",classe:""},
            {nome:"Jorgha di Valdombra",desc:"Mezzelfa, 58 anni.",razza:"Mezz'elfo",genere:"Donna",classe:"Bardo"},
            {nome:"Josef Lambari",desc:"Umano, 21 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Kestel",desc:"Kender, 15 anni.",razza:"Kender",genere:"Donna",classe:""},
            {nome:"Kinson",desc:"Elfo, mastro birraio.",razza:"Elfo",genere:"Uomo",classe:""},
            {nome:"Kliarn Scaglia d'Argento",desc:"Dragonide, 26 anni.",razza:"Dragonide",genere:"Uomo",classe:""},
            {nome:"Kurzum Fall",desc:"Umano, 33 anni.",razza:"Umano",genere:"Uomo",classe:"Stregone"},
            {nome:"Lacrimis Lakeblue",desc:"Genasi, 30 anni.",razza:"Genasi",genere:"Uomo",classe:"Chierico"},
            {nome:"Leif Dagsson",desc:"Umano, 25 anni.",razza:"Umano",genere:"Uomo",classe:"Bardo"},
            {nome:"Loki",desc:"Mezz'elfa, 29 anni.",razza:"Mezz'elfo",genere:"Donna",classe:"Ladro"},
            {nome:"Lorimbur Barbargento",desc:"Nano, 110 anni.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Lucilla",desc:"Mezz'elfa, 80 anni.",razza:"Mezz'elfo",genere:"Donna",classe:""},
            {nome:"Luka Russor",desc:"Nano, 26 anni.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Maximilian Regulus",desc:"Umano, 24 anni.",razza:"Umano",genere:"Uomo",classe:"Mago"},
            {nome:"Mehtaar Zar",desc:"Aarakocra.",razza:"Aarakocra",genere:"Uomo",classe:""},
            {nome:"Merlock",desc:"Umano, 36 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Mett Brunor",desc:"Tiefling, 21 anni.",razza:"Tiefling",genere:"Uomo",classe:""},
            {nome:"Mikalin Dimplecheek",desc:"Halfling, 32 anni.",razza:"Halfling",genere:"Uomo",classe:"Artefice"},
            {nome:"Mildred Cuorefiero",desc:"Umana, 53 anni.",razza:"Umano",genere:"Donna",classe:""},
            {nome:"Milo Tealeaf",desc:"Halfling, 40 anni.",razza:"Halfling",genere:"Uomo",classe:""},
            {nome:"Moona",desc:"Elfa, 1200 anni.",razza:"Elfo",genere:"Donna",classe:""},
            {nome:"Munch",desc:"Nano archeologo.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Myklaar il Rosso",desc:"Goliath, 30 anni.",razza:"Goliath",genere:"Uomo",classe:"Arcanista"},
            {nome:"Na'ak",desc:"Goliath, 30 anni.",razza:"Goliath",genere:"Uomo",classe:"Guerriero"},
            {nome:"Nesta Ombra Verde",desc:"Elfa, 100 anni.",razza:"Elfo",genere:"Donna",classe:"Druida"},
            {nome:"Nikoras",desc:"Mezz'orco, 30 anni.",razza:"Mezz'orco",genere:"Donna",classe:"Paladina"},
            {nome:"Nikolaj il Protettore",desc:"Umano, 68 anni.",razza:"Umano",genere:"Uomo",classe:"Chierico"},
            {nome:"Nives Grey",desc:"Umana, 28 anni.",razza:"Umano",genere:"Donna",classe:"Stregone"},
            {nome:"Noha",desc:"Mezz'orco, 20 anni.",razza:"Mezz'orco",genere:"Donna",classe:""},
            {nome:"Obscurius",desc:"Dragonide, 30 anni.",razza:"Dragonide",genere:"Uomo",classe:"Warlock"},
            {nome:"Orso Maria",desc:"Umano, 20 anni.",razza:"Umano",genere:"Uomo",classe:"Mago"},
            {nome:"Pamela",desc:"Umana, 40 anni.",razza:"Umano",genere:"Donna",classe:"Mago"},
            {nome:"Phealin Babanoi",desc:"Tiefling, 21 anni.",razza:"Tiefling",genere:"Uomo",classe:""},
            {nome:"Phill Be'alla Sio",desc:"Umano, 40 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Ramón Reven",desc:"Umano, 30 anni.",razza:"Umano",genere:"Uomo",classe:"Mago"},
            {nome:"Rhutt Kor",desc:"Nano, 194 anni.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Rughdar Altocalice",desc:"Umano, 32 anni.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
            {nome:"Selina Dreifus",desc:"Elfa, 100 anni.",razza:"Elfo",genere:"Donna",classe:"Druida"},
            {nome:"Sir Andr D'Allegrez",desc:"Umano, 26 anni.",razza:"Umano",genere:"Uomo",classe:"Guerriero"},
            {nome:"Sirzechs Jailbreak",desc:"Tiefling, 30 anni.",razza:"Tiefling",genere:"Uomo",classe:""},
            {nome:"Spakkabot 494",desc:"Forgiato, 89 anni.",razza:"Forgiato",genere:"Uomo",classe:""},
            {nome:"Sssertisss Raw",desc:"Lizardfolk, 32 anni.",razza:"Lizardfolk",genere:"Uomo",classe:""},
            {nome:"Standus Colimar Sinfurr",desc:"Elfo, 452 anni.",razza:"Elfo",genere:"Uomo",classe:""},
            {nome:"Stenar",desc:"Mezz'orco, 30 anni.",razza:"Mezz'orco",genere:"Uomo",classe:""},
            {nome:"Stephen Umbra",desc:"Mezz'elfo, 35 anni.",razza:"Mezz'elfo",genere:"Uomo",classe:""},
            {nome:"Strike",desc:"Warforged, 20 anni.",razza:"Warforged",genere:"Uomo",classe:"Monaco"},
            {nome:"Thorgrim",desc:"Nano, 205 anni.",razza:"Nano",genere:"Uomo",classe:""},
            {nome:"Torak Bearclaw",desc:"Goliath, 30 anni.",razza:"Goliath",genere:"Uomo",classe:"Guerriero"},
            {nome:"Torth",desc:"Umano, 25 anni.",razza:"Umano",genere:"Uomo",classe:"Artefice"},
            {nome:"Ulkian Safforz",desc:"Umano, 15 anni.",razza:"Umano",genere:"Uomo",classe:""},
            {nome:"Varax",desc:"Dragonide, 27 anni.",razza:"Dragonide",genere:"Uomo",classe:"Monaco"},
            {nome:"Vert & Braas",desc:"Coboldi gemelli.",razza:"Coboldo",genere:"Uomo",classe:""},
            {nome:"Willow",desc:"Aasimar, 30 anni.",razza:"Aasimar",genere:"Donna",classe:"Bardo"},
            {nome:"Xyravy",desc:"Dragonide, 60 anni.",razza:"Dragonide",genere:"Uomo",classe:""},
            {nome:"Yama San",desc:"Umano, 50 anni.",razza:"Umano",genere:"Uomo",classe:"Monaco"},
            {nome:"Yüki",desc:"Umano, 22 anni.",razza:"Umano",genere:"Uomo",classe:"Mago"},
            {nome:"Yushiro Koheda",desc:"Mezz'elfo, 21 anni.",razza:"Mezz'elfo",genere:"Uomo",classe:"Bardo"},
            {nome:"Zessil",desc:"Yuan-Ti, 33 anni.",razza:"Yuan-Ti",genere:"Donna",classe:"Warlock"},
            {nome:"Zubi Ignis",desc:"Umano, 30 anni.",razza:"Umano",genere:"Uomo",classe:""}
        ];

        // LOGICA DI FILTRAGGIO
        let filtered = [...npcs];
        function extractAge(d) { const m = d.match(/(\d+)/); return m ? parseInt(m[1]) : 999; }

        function render() {
            const list = document.getElementById('npc-list');
            list.innerHTML = '';
            document.getElementById('page-counter').textContent = filtered.length + ' schede trovate';
            filtered.forEach(n => {
                list.innerHTML += `<div class="npc-card">
                    <h3 class="font-bold text-lg">${n.nome}</h3>
                    <p class="text-sm opacity-80">${n.razza} · ${n.classe || 'Nessuna classe'}</p>
                    <p class="mt-2 text-sm">${n.desc}</p>
                </div>`;
            });
        }

        document.getElementById('search-input').addEventListener('input', e => {
            const q = e.target.value.toLowerCase();
            filtered = npcs.filter(n => (n.nome+n.desc+n.razza).toLowerCase().includes(q));
            render();
        });

        document.getElementById('sort-name-asc').addEventListener('click', () => { filtered.sort((a,b) => a.nome.localeCompare(b.nome)); render(); });
        document.getElementById('sort-name-desc').addEventListener('click', () => { filtered.sort((a,b) => b.nome.localeCompare(a.nome)); render(); });
        document.getElementById('sort-age-asc').addEventListener('click', () => { filtered.sort((a,b) => extractAge(a.desc) - extractAge(b.desc)); render(); });
        document.getElementById('sort-age-desc').addEventListener('click', () => { filtered.sort((a,b) => extractAge(b.desc) - extractAge(a.desc)); render(); });
        document.getElementById('reset-btn').addEventListener('click', () => { filtered = [...npcs]; render(); });

        render();
    </script>
</body>
</html>
