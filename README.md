<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SWAX | Site Officiel</title>
    <style>
        /* RESET GLOBAL */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
        }

        body {
            background-color: #ffffff;
            color: #111111;
            overflow-x: hidden;
            position: relative;
        }

        /* HEADER PRINCIPAL */
        .main-header {
            height: 60px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 48px;
            background-color: #ffffff;
            position: relative;
            z-index: 10;
        }

        .brand-logo {
            font-size: 26px;
            font-weight: 900;
            letter-spacing: -1px;
            cursor: pointer;
            user-select: none;
            flex: 1;
            display: flex;
            justify-content: flex-start;
        }

        /* NAVIGATION CENTRALE */
        .main-nav {
            display: flex;
            gap: 28px;
            justify-content: center;
            align-items: center;
        }

        .nav-item-new {
            display: flex;
            align-items: center;
            gap: 6px;
            text-decoration: none;
        }

        .main-nav a {
            text-decoration: none;
            color: #111111;
            font-size: 16px;
            font-weight: 500;
            padding: 6px 0;
            border-bottom: 2px solid transparent;
            transition: border-color 0.2s;
        }

        .main-nav a:hover {
            border-bottom: 2px solid #111111;
        }

        /* BADGE AVEC FOND NOIR ET TEXTE NEW EN ROUGE */
        .badge-new {
            background-color: #111111;
            color: #ff3b30; /* Rouge */
            font-size: 10px;
            font-weight: 800;
            padding: 2px 6px;
            border-radius: 4px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            display: inline-block;
        }

        /* ACTIONS DE DROITE */
        .header-actions {
            display: flex;
            align-items: center;
            gap: 20px;
            flex: 1;
            justify-content: flex-end;
        }

        .search-box {
            position: relative;
            display: flex;
            align-items: center;
        }

        .search-box input {
            background-color: #f5f5f5;
            border: none;
            border-radius: 100px;
            padding: 8px 16px 8px 44px;
            font-size: 15px;
            outline: none;
            width: 180px;
            transition: width 0.2s ease, background-color 0.2s ease;
        }

        .search-box input:focus {
            width: 240px;
            background-color: #e5e5e5;
        }

        .icon-search {
            position: absolute;
            left: 14px;
            width: 18px;
            height: 18px;
            color: #111111;
        }

        .icon-btn {
            background: none;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 4px;
            position: relative;
            transition: transform 0.2s ease;
        }

        .icon-btn svg {
            width: 24px;
            height: 24px;
            color: #111111;
            transition: fill 0.2s ease, color 0.2s ease;
        }

        .icon-btn.has-items svg {
            fill: #ff3b30;
            color: #ff3b30;
        }

        .cart-count-badge {
            position: absolute;
            top: -2px;
            right: -2px;
            background-color: #111111;
            color: #ffffff;
            font-size: 11px;
            font-weight: 700;
            width: 18px;
            height: 18px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* ANIMATIONS DU COEUR VOLANT */
        @keyframes heartPop {
            0% { transform: scale(1); }
            50% { transform: scale(1.4); }
            100% { transform: scale(1); }
        }
        .animate-heart-btn {
            animation: heartPop 0.4s ease-out;
        }

        .flying-heart {
            position: fixed;
            z-index: 9999;
            color: #ff3b30;
            font-size: 30px;
            pointer-events: none;
            transition: all 0.8s cubic-bezier(0.25, 1, 0.5, 1);
        }

        /* ACCUEIL HERO */
        .hero-section {
            width: 100%;
            height: calc(100vh - 60px);
            background-color: #000000;
        }

        .hero-wrapper {
            width: 100%;
            height: 100%;
            background-repeat: no-repeat;
            background-position: center center;
            background-size: cover;
            display: flex;
            align-items: flex-end;
            padding: 60px 48px;
        }

        .hero-content {
            color: #ffffff;
            max-width: 600px;
        }

        .hero-content h1 {
            font-size: 3.5rem;
            font-weight: 800;
            letter-spacing: -1px;
            margin-bottom: 10px;
            text-transform: uppercase;
        }

        .hero-content p {
            font-size: 1.2rem;
            margin-bottom: 24px;
        }

        .btn-shop {
            display: inline-block;
            background-color: #ffffff;
            color: #111111;
            padding: 10px 28px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            font-size: 15px;
            cursor: pointer;
        }

        /* PAGE NOUVEAU TOTALEMENT IMMERSIVE */
        .nouveau-full-page {
            width: 100%;
            height: calc(100vh - 60px);
            background-image: url('T-shirt swax.png');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
        }

        /* CONFIGURATION CHRONOMÈTRE */
        .shop-section-timer {
            width: 100%;
            height: calc(100vh - 60px);
            background-color: #000000;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: #ffffff;
            padding: 40px;
        }

        .shop-timer-title {
            font-size: 28px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 40px;
        }

        .timer-giant-container {
            display: flex;
            gap: 32px;
        }

        .timer-giant-segment {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .timer-giant-number {
            font-size: 5.5rem;
            font-weight: 900;
        }

        .timer-giant-label {
            font-size: 14px;
            font-weight: 700;
            color: #ff3b30;
            text-transform: uppercase;
            margin-top: 8px;
        }

        .timer-colon {
            font-size: 4.5rem;
            color: #ff3b30;
        }

        /* COMPOSANTS PAGES SECONDAIRES */
        .cart-page-section {
            padding: 60px 48px;
            max-width: 800px;
            margin: 0 auto;
        }

        .cart-title {
            font-size: 32px;
            font-weight: 800;
            margin-bottom: 30px;
            text-transform: uppercase;
            letter-spacing: -1px;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            border-bottom: 1px solid #e5e5e5;
        }

        .cart-item-details h3 {
            font-size: 18px;
            font-weight: 600;
        }

        .cart-item-price {
            font-size: 18px;
            font-weight: 700;
        }

        .cart-footer {
            margin-top: 40px;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            gap: 16px;
        }

        .cart-total {
            font-size: 22px;
            font-weight: 800;
        }

        .btn-clear-cart {
            background: none;
            border: 1px solid #111111;
            padding: 10px 20px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 500;
        }
    </style>
</head>
<body>

    <header class="main-header">
        <div class="brand-logo" onclick="afficherAccueil()">SWAX</div>
        
        <nav class="main-nav">
            <a href="#" class="nav-item-new" onclick="ouvrirPageNouveau()">
                <span>Nouveau</span><span class="badge-new">New</span>
            </a>
            <a href="#" onclick="ouvrirPageBoutique('Homme')">Homme</a>
            <a href="#" onclick="ouvrirPageBoutique('Femme')">Femme</a>
        </nav>

        <div class="header-actions">
            <div class="search-box">
                <svg class="icon-search" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <circle cx="11" cy="11" r="8"></circle>
                    <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
                </svg>
                <input type="text" placeholder="Rechercher">
            </div>
            
            <button class="icon-btn" id="main-heart-btn" onclick="ouvrirPageFavoris()">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path>
                </svg>
            </button>
            
            <button class="icon-btn" onclick="ouvrirPagePanier()">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M6 2L3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"></path><line x1="3" y1="6" x2="21" y2="6"></line><path d="M16 10a4 4 0 0 1-8 0"></path></svg>
                <div class="cart-count-badge" id="global-cart-badge">0</div>
            </button>
        </div>
    </header>

    <div id="content-area">
        <main class="hero-section">
            <div class="hero-wrapper" style="background-image: url('T-shirt swax.png');">
                <div class="hero-content">
                    <h1>SWAX PERFORMANCE</h1>
                    <p>Repoussez vos limites avec style.</p>
                    <div onclick="ouvrirPageNouveau()" class="btn-shop">Découvrir</div>
                </div>
            </div>
        </main>
    </div>

    <script>
        // --- LOGIQUE DES PRODUITS EN FAVORIS ---
        let favoris = JSON.parse(localStorage.getItem('swax_favoris_items')) || [];

        function rafraichirIconeFavorisMenu() {
            const boutonCoeur = document.getElementById('main-heart-btn');
            if (boutonCoeur) {
                if (favoris.length > 0) {
                    boutonCoeur.classList.add('has-items');
                } else {
                    boutonCoeur.classList.remove('has-items');
                }
            }
        }

        function ouvrirPageFavoris() {
            const conteneur = document.getElementById('content-area');
            if (favoris.length === 0) {
                conteneur.innerHTML = `
                    <section class="cart-page-section">
                        <h2 class="cart-title">Vos Favoris</h2>
                        <p class="cart-empty-message">Aucun article dans vos favoris pour le moment.</p>
                        <div onclick="afficherAccueil()" class="btn-shop" style="background-color:#111111; color:#ffffff; display:inline-block;">Continuer mes visites</div>
                    </section>
                `;
                return;
            }

            let itemsHTML = '';
            favoris.forEach(item => {
                itemsHTML += `
                    <div class="cart-item">
                        <div class="cart-item-details">
                            <h3>${item.nom}</h3>
                            <p>Ajouté à votre liste de souhaits</p>
                        </div>
                        <div class="cart-item-price">${item.prix} €</div>
                    </div>
                `;
            });

            conteneur.innerHTML = `
                <section class="cart-page-section">
                    <h2 class="cart-title">Vos Favoris</h2>
                    <div class="cart-items-list">${itemsHTML}</div>
                </section>
            `;
        }

        // --- PANIER ET COMPTE À REBOURS ---
        let panier = JSON.parse(localStorage.getItem('swax_panier_items')) || [];
        function mettreAJourBadgePanier() {
            const badge = document.getElementById('global-cart-badge');
            if (badge) badge.innerText = panier.length;
        }
        function viderPanier() {
            panier = []; localStorage.removeItem('swax_panier_items');
            mettreAJourBadgePanier(); ouvrirPagePanier();
        }
        function ouvrirPagePanier() {
            const conteneur = document.getElementById('content-area');
            if (panier.length === 0) {
                conteneur.innerHTML = `<section class="cart-page-section"><h2 class="cart-title">Votre Panier</h2><p class="cart-empty-message">Votre panier est actuellement vide.</p></section>`;
                return;
            }
            let total = 0; let itemsHTML = '';
            panier.forEach(item => { total += item.prix; itemsHTML += `<div class="cart-item"><div class="cart-item-details"><h3>${item.nom}</h3></div><div class="cart-item-price">${item.prix} €</div></div>`; });
            conteneur.innerHTML = `<section class="cart-page-section"><h2 class="cart-title">Votre Panier</h2><div>${itemsHTML}</div><div class="cart-footer"><div class="cart-total">Total : ${total} €</div><button class="btn-clear-cart" onclick="viderPanier()">Vider le panier</button></div></section>`;
        }

        let cibleDate = localStorage.getItem('swax_timer_target') || (new Date().getTime() + 30 * 24 * 60 * 60 * 1000);
        localStorage.setItem('swax_timer_target', cibleDate);
        function actualiserVisuelChronometre() {
            const distance = cibleDate - new Date().getTime();
            const elJours = document.getElementById('giant-timer-j');
            if (elJours && distance > 0) {
                document.getElementById('giant-timer-j').innerText = Math.floor(distance / (1000 * 60 * 60 * 24));
                document.getElementById('giant-timer-h').innerText = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                document.getElementById('giant-timer-m').innerText = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
                document.getElementById('giant-timer-s').innerText = Math.floor((distance % (1000 * 60)) / 1000);
            }
        }
        setInterval(actualiserVisuelChronometre, 1000);

        // --- NAVIGATION ET RENDER PAGES ---
        function ouvrirPageNouveau() {
            const conteneur = document.getElementById('content-area');
            conteneur.innerHTML = `
                <div class="nouveau-full-page"></div>
            `;
        }

        function ouvrirPageBoutique(categorie) {
            const conteneur = document.getElementById('content-area');
            conteneur.innerHTML = `
                <section class="shop-section-timer">
                    <div class="shop-timer-title">Lancement Collection ${categorie}</div>
                    <div class="timer-giant-container">
                        <div class="timer-giant-segment"><div class="timer-giant-number" id="giant-timer-j">00</div><div class="timer-giant-label">Jours</div></div>
                        <div class="timer-colon">:</div>
                        <div class="timer-giant-segment"><div class="timer-giant-number" id="giant-timer-h">00</div><div class="timer-giant-label">Heures</div></div>
                        <div class="timer-colon">:</div>
                        <div class="timer-giant-segment"><div class="timer-giant-number" id="giant-timer-m">00</div><div class="timer-giant-label">Min</div></div>
                        <div class="timer-colon">:</div>
                        <div class="timer-giant-segment"><div class="timer-giant-number" id="giant-timer-s">00</div><div class="timer-giant-label">Sec</div></div>
                    </div>
                </section>
            `;
            actualiserVisuelChronometre();
        }

        function afficherAccueil() {
            const conteneur = document.getElementById('content-area');
            conteneur.innerHTML = `
                <main class="hero-section">
                    <div class="hero-wrapper" style="background-image: url('T-shirt swax.png');">
                        <div class="hero-content">
                            <h1>SWAX PERFORMANCE</h1>
                            <p>Repoussez vos limites avec style.</p>
                            <div onclick="ouvrirPageNouveau()" class="btn-shop">Découvrir</div>
                        </div>
                    </div>
                </main>
            `;
        }

        mettreAJourBadgePanier();
        rafraichirIconeFavorisMenu();
    </script>
</body>
</html>
