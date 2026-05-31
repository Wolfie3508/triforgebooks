<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TriForge Books</title>
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>🔥</text></svg>">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@700&family=Rajdhani:wght@400;600&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --dark-metal: #1a1a1d;
            --deep-red: #950740;
            --bright-red: #c3073f;
            --ember-orange: #ff4d00;
            --text-gray: #c5c6c7;
        }

        body {
            font-family: 'Rajdhani', sans-serif;
            margin: 0;
            background: radial-gradient(circle at 50% -20%, #2c0414, var(--dark-metal) 60%);
            background-attachment: fixed;
            color: var(--text-gray);
            overflow-x: hidden;
        }

        /* --- THE LOADER --- */
        #forge-loader {
            position: fixed;
            top: 0; left: 0; 
            width: 100%; height: 100%;
            background: var(--dark-metal);
            z-index: 10000;
            display: flex;
            justify-content: center;
            align-items: center;
            /* The "Garage Door" Slide transition */
            transition: transform 0.8s cubic-bezier(0.7, 0, 0.3, 1), opacity 0.5s;
        }

        .forge-text {
            font-family: 'Orbitron', sans-serif;
            color: var(--bright-red);
            font-size: 2.5rem;
            letter-spacing: 10px;
            animation: glow-pulse 1.5s infinite alternate;
        }

        @keyframes glow-pulse {
            from {
                text-shadow: 0 0 5px var(--ember-orange);
                transform: scale(0.98);
                opacity: 0.7;
            }
            to {
                text-shadow: 0 0 20px var(--ember-orange), 0 0 40px var(--bright-red);
                transform: scale(1);
                opacity: 1;
            }
        }

        /* Classes added by JavaScript */
        .loader-finished {
            transform: translateY(-100%);
            opacity: 0;
        }

        /* --- REST OF THE SITE --- */
        .firefly-container {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        .firefly {
            position: absolute;
            width: 4px; height: 4px;
            background: var(--ember-orange);
            border-radius: 50%;
            box-shadow: 0 0 10px var(--ember-orange), 0 0 20px var(--bright-red);
            opacity: 0;
            bottom: -10px;
            animation: rise 10s infinite ease-in;
        }

        @keyframes rise {
            0% { transform: translateY(0); opacity: 0; }
            20% { opacity: 0.8; }
            100% { transform: translateY(-110vh); opacity: 0; }
        }

        header {
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(10px);
            border-bottom: 2px solid var(--bright-red);
            padding: 5rem 1rem;
            text-align: center;
        }

        header h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 3rem;
            color: white;
            text-transform: uppercase;
            letter-spacing: 4px;
            text-shadow: 0 0 15px var(--bright-red);
            margin: 0;
        }

        .container {
            max-width: 900px; 
            margin: 2rem auto;
            padding: 2rem 1rem;
        }

        .series-title {
            font-family: 'Orbitron', sans-serif;
            color: var(--ember-orange);
            border-left: 5px solid var(--bright-red);
            padding-left: 15px;
            margin-bottom: 2rem;
            text-transform: uppercase;
        }

        .bookshelf {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2.5rem;
            margin-bottom: 5rem;
        }

        .book-card {
            background: rgba(36, 37, 38, 0.6);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1); 
            border-radius: 12px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            transition: transform 0.3s ease;
        }

        .book-card:hover {
            transform: translateY(-5px);
            border-color: var(--ember-orange);
        }

        .book-image {
            width: 100%;
            aspect-ratio: 2 / 3;
            object-fit: contain;
            background-color: #000;
            border-bottom: 3px solid var(--bright-red);
        }

        .book-info {
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .book-title {
            font-family: 'Orbitron', sans-serif;
            color: white;
            margin: 0 0 1rem 0;
        }

        .book-blurb {
            color: #999;
            flex-grow: 1;
            margin-bottom: 1.5rem;
        }

        .buy-button {
            display: block;
            text-align: center;
            background: var(--bright-red);
            color: white;
            text-decoration: none;
            padding: 0.8rem;
            font-weight: bold;
            text-transform: uppercase;
            transition: 0.3s;
        }

        .buy-button:hover {
            background: var(--ember-orange);
            box-shadow: 0 0 15px var(--ember-orange);
        }

        .coming-soon {
            background: #333;
            color: #777;
            cursor: not-allowed;
        }

        footer {
            text-align: center;
            padding: 4rem 1rem;
            border-top: 1px solid #333;
            color: white;
            background: rgba(0,0,0,0.5);
        }
    </style>
</head>
<body>

    <div id="forge-loader">
        <h1 class="forge-text">FORGING...</h1>
    </div>

    <div class="firefly-container">
        <div class="firefly" style="left: 10%; animation-duration: 8s;"></div>
        <div class="firefly" style="left: 30%; animation-duration: 12s; animation-delay: 2s;"></div>
        <div class="firefly" style="left: 50%; animation-duration: 9s; animation-delay: 4s;"></div>
        <div class="firefly" style="left: 70%; animation-duration: 11s; animation-delay: 1s;"></div>
        <div class="firefly" style="left: 90%; animation-duration: 13s; animation-delay: 3s;"></div>
    </div>

    <header>
        <h1>TriForge Books</h1>
        <p style="color: var(--bright-red); font-weight: bold; letter-spacing: 2px;">LOGIC & IMAGINATION FORGED</p>
    </header>

    <div class="container">
        <section class="series-section">
            <h2 class="series-title">The Adventures of Luke</h2>
            <div class="bookshelf">
                <div class="book-card">
                    <img src="luke_vol1 - Copy.jpg" alt="Luke Book 1" class="book-image">
                    <div class="book-info">
                        <h3 class="book-title">Friends and Foes</h3>
                        <p class="book-blurb">The first installment in the saga. Experience the adventure that started it all.</p>
                        <a href="https://www.amazon.com/Adventures-Luke-Friends-Foes/dp/B0F88G7R8Q" class="buy-button" target="_blank">Acquire on Amazon</a>
                    </div>
                </div>

                <div class="book-card">
                    <img src="luke_vol2 - Copy.jpg" alt="Luke Book 2" class="book-image">
                    <div class="book-info">
                        <h3 class="book-title">The Undead Rise</h3>
                        <p class="book-blurb">The next chapter in Luke's journey is currently being forged in the heat of imagination.</p>
                        <span class="buy-button coming-soon">Currently Forging</span>
                    </div>
                </div>
            </div>
        </section>

        <h2 class="series-title" style="opacity: 0.5;">More Coming Soon</h2>
    </div>

    <footer>
        <p>&copy; 2026 TriForge Books | Built for the Craft</p>
    </footer>

    <script>
        window.addEventListener('load', () => {
            const loader = document.getElementById('forge-loader');
            
            // Wait 1.5 seconds so they can see the glow effect
            setTimeout(() => {
                if(loader) {
                    // Add the class that slides it UP
                    loader.classList.add('loader-finished');
                    
                    // Remove from view completely after slide is done
                    setTimeout(() => {
                        loader.style.display = 'none';
                    }, 800);
                }
            }, 1500);
        });
    </script>
</body>
</html>
