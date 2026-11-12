<!DOCTYPE html>
<html lang="ur">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Angeethi — Peshawari Zaiqa</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="stylesheet"
        href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,500;9..144,600;9..144,700&family=Work+Sans:wght@400;500;600&display=swap">
    <link rel="stylesheet" href="resturent.css">
</head>

<body>

    <header class="site-header" id="siteHeader">
        <div class="header-inner">
            <a href="#top" class="brand">Angeethi</a>
            <nav class="main-nav" id="mainNav">
                <a href="#menu">Menu</a>
                <a href="#kahani">Hamari Kahani</a>
                <a href="#waqt">Waqt &amp; Jaga</a>
                <a href="#order">Order</a>
            </nav>
            <button class="nav-toggle" id="navToggle" aria-label="Menu kholein" aria-expanded="false">
                <span></span><span></span><span></span>
            </button>
        </div>
    </header>

    <main id="top">

        <section class="hero">
            <div class="hero-inner">
                <p class="hero-kicker">Shaam dhalte hi angaar jalte hain</p>
                <h1 class="hero-title">Peshawar ke koyle par<br>pakta asli zaiqa.</h1>
                <p class="hero-sub">Chapli kabab, tikka aur karahi — usi tarah jaise dahaiyon se bante aa rahe hain,
                    seekhon aur tandoor ki garmi mein.</p>
                <div class="hero-actions">
                    <a href="#menu" class="btn btn-primary">Menu dekhein</a>
                    <a href="#waqt" class="btn btn-ghost">Hum kahan hain</a>
                </div>
            </div>
            <div class="hero-mark" aria-hidden="true">
                <svg viewBox="0 0 200 200" class="ember-svg">
                    <circle cx="100" cy="130" r="55" class="ember-glow" />
                    <path d="M100 20 C 130 60, 80 70, 100 100 C 120 120, 90 150, 100 180" class="ember-flame" />
                </svg>
            </div>
        </section>

        <section class="menu-section" id="menu">
            <div class="section-head">
                <h2>Aaj ka Menu</h2>
                <p>Har cheez taaza banai jati hai — order ke baad, order ke mutabiq.</p>
            </div>

            <div class="menu-tabs" id="menuTabs">
                <button class="tab-btn is-active" data-cat="kabab">Kabab &amp; Tikka</button>
                <button class="tab-btn" data-cat="karahi">Karahi</button>
                <button class="tab-btn" data-cat="naan">Naan &amp; Roti</button>
                <button class="tab-btn" data-cat="mashroob">Mashroobat</button>
            </div>

            <ul class="menu-list" id="menuList">

                <li class="menu-item" data-cat="kabab">
                    <div class="menu-item-name">Chapli Kabab <span class="menu-item-tag">Ghar ki Pehchaan</span></div>
                    <div class="menu-item-desc">Desi masalon aur tamatar ke saath, tawe par karari tab tak seenka jata
                        hai jab tak kinaray sunehre na ho jayein.</div>
                    <div class="menu-item-price">450</div>
                </li>
                <li class="menu-item" data-cat="kabab">
                    <div class="menu-item-name">Seekh Kabab</div>
                    <div class="menu-item-desc">Bareek keeme se banaye gaye, koyle ki angeethi par seenke gaye.</div>
                    <div class="menu-item-price">380</div>
                </li>
                <li class="menu-item" data-cat="kabab">
                    <div class="menu-item-name">Malai Boti Tikka</div>
                    <div class="menu-item-desc">Raat bhar dahi aur cream mein maerinate, phir dheemi aanch par bhuna
                        gaya.</div>
                    <div class="menu-item-price">520</div>
                </li>

                <li class="menu-item" data-cat="karahi">
                    <div class="menu-item-name">Chicken Karahi <span class="menu-item-tag">Family Size</span></div>
                    <div class="menu-item-desc">Adrak, lehsan aur hari mirch ke saath, lohay ki karahi mein dam par
                        pakayi gayi.</div>
                    <div class="menu-item-price">1400</div>
                </li>
                <li class="menu-item" data-cat="karahi">
                    <div class="menu-item-name">Mutton Karahi</div>
                    <div class="menu-item-desc">Namkeen aur halka teekha, lambay waqt tak dheemi aanch par pakaya jata
                        hai.</div>
                    <div class="menu-item-price">2100</div>
                </li>

                <li class="menu-item" data-cat="naan">
                    <div class="menu-item-name">Tandoori Naan</div>
                    <div class="menu-item-desc">Angeethi ki deewar par seenka gaya, garam garam table tak.</div>
                    <div class="menu-item-price">60</div>
                </li>
                <li class="menu-item" data-cat="naan">
                    <div class="menu-item-name">Roghni Naan</div>
                    <div class="menu-item-desc">Til aur ghee ke saath, thoda mota aur naram.</div>
                    <div class="menu-item-price">90</div>
                </li>

                <li class="menu-item" data-cat="mashroob">
                    <div class="menu-item-name">Kehwa</div>
                    <div class="menu-item-desc">Elaichi aur zafraan ke saath, khane ke baad ka sukoon.</div>
                    <div class="menu-item-price">120</div>
                </li>
                <li class="menu-item" data-cat="mashroob">
                    <div class="menu-item-name">Lassi</div>
                    <div class="menu-item-desc">Gaadhi, malai wali, thodi si meethi.</div>
                    <div class="menu-item-price">150</div>
                </li>

            </ul>
        </section>

        <section class="kahani-section" id="kahani">
            <div class="kahani-inner">
                <h2>Hamari Kahani</h2>
                <p>Angeethi ki shuruaat ek chhoti si gali ke kone se hui — ek angeethi, kuch kursiyan, aur wo khushbu jo
                    dor door tak bula leti thi. Aaj bhi tareeqa wahi hai: koyla, seekh, aur sabr. Koi shortcut nahi, koi
                    jaldi nahi.</p>
                <p>Har sham hum apna angaar naye sire se jalate hain, taake har plate mein wohi purani garmahat
                    pahunche.</p>
            </div>
        </section>

        <section class="waqt-section" id="waqt">
            <div class="section-head">
                <h2>Waqt &amp; Jaga</h2>
            </div>
            <div class="waqt-grid">
                <div class="waqt-card">
                    <h3>Khulne ka Waqt</h3>
                    <dl class="waqt-times">
                        <div>
                            <dt>Har roz</dt>
                            <dd>Shaam 5:00 — Raat 12:00</dd>
                        </div>
                        <div>
                            <dt>Jumma</dt>
                            <dd>Shaam 6:00 — Raat 1:00</dd>
                        </div>
                    </dl>
                </div>
                <div class="waqt-card">
                    <h3>Jaga</h3>
                    <p>Qissa Khwani Bazar ke qareeb, Peshawar.</p>
                    <p>Parking gali ke peeche dastiyab hai.</p>
                </div>
            </div>
        </section>

        <section class="order-section" id="order">
            <div class="section-head">
                <h2>Order ke liye Rabta Karein</h2>
                <p>Neeche apna order likhein, hum jald rabta karenge.</p>
            </div>

            <form class="order-form" id="orderForm" novalidate>
                <div class="form-row">
                    <label for="nameInput">Naam</label>
                    <input type="text" id="nameInput" name="name" placeholder="Apna naam likhein" required>
                    <span class="field-msg" id="nameMsg"></span>
                </div>
                <div class="form-row">
                    <label for="phoneInput">Phone Number</label>
                    <input type="tel" id="phoneInput" name="phone" placeholder="03XX-XXXXXXX" required>
                    <span class="field-msg" id="phoneMsg"></span>
                </div>
                <div class="form-row">
                    <label for="orderInput">Order ki Tafseel</label>
                    <textarea id="orderInput" name="order" rows="3"
                        placeholder="Jaise: 2x Chapli Kabab, 1x Chicken Karahi" required></textarea>
                    <span class="field-msg" id="orderMsg"></span>
                </div>
                <button type="submit" class="btn btn-primary">Order Bhejein</button>
                <p class="form-status" id="formStatus" role="status"></p>
            </form>
        </section>

    </main>

    <footer class="site-footer">
        <p>Angeethi — Peshawar ka angaar, plate tak.</p>
    </footer>

    <script src="resturent.js"></script>
</body>

</html>
