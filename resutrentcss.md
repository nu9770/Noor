/* ---------- Tokens ---------- */
:root {
    --bg: #1C1410;
    --bg-raised: #241A14;
    --ember: #D2491D;
    --ember-dim: #7A2E11;
    --turmeric: #E3A83B;
    --cream: #F3E7D3;
    --cream-dim: #C9BBA3;
    --olive: #7A8450;
    --border: rgba(243, 231, 211, 0.14);

    --font-display: "Fraunces", serif;
    --font-body: "Work Sans", sans-serif;

    --max-w: 960px;
}

* {
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    margin: 0;
    background: var(--bg);
    color: var(--cream);
    font-family: var(--font-body);
    line-height: 1.6;
    -webkit-font-smoothing: antialiased;
}

h1,
h2,
h3 {
    font-family: var(--font-display);
    color: var(--cream);
    margin: 0;
    font-weight: 600;
}

p {
    margin: 0;
    color: var(--cream-dim);
}

a {
    color: inherit;
}

ul,
dl {
    margin: 0;
    padding: 0;
    list-style: none;
}

img {
    max-width: 100%;
    display: block;
}

/* focus visibility */
a:focus-visible,
button:focus-visible,
input:focus-visible,
textarea:focus-visible {
    outline: 2px solid var(--turmeric);
    outline-offset: 3px;
}

@media (prefers-reduced-motion: reduce) {
    * {
        animation-duration: 0.01ms !important;
        transition-duration: 0.01ms !important;
    }

    html {
        scroll-behavior: auto;
    }
}

/* ---------- Header ---------- */
.site-header {
    position: sticky;
    top: 0;
    z-index: 50;
    background: rgba(28, 20, 16, 0.92);
    backdrop-filter: blur(6px);
    border-bottom: 1px solid var(--border);
}

.header-inner {
    max-width: var(--max-w);
    margin: 0 auto;
    padding: 18px 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.brand {
    font-family: var(--font-display);
    font-size: 1.5rem;
    font-weight: 700;
    text-decoration: none;
    letter-spacing: 0.01em;
}

.main-nav {
    display: flex;
    gap: 32px;
}

.main-nav a {
    text-decoration: none;
    color: var(--cream-dim);
    font-size: 0.95rem;
    transition: color 0.15s ease;
}

.main-nav a:hover {
    color: var(--turmeric);
}

.nav-toggle {
    display: none;
    flex-direction: column;
    justify-content: center;
    gap: 5px;
    width: 34px;
    height: 34px;
    background: none;
    border: none;
    cursor: pointer;
    padding: 0;
}

.nav-toggle span {
    display: block;
    height: 2px;
    background: var(--cream);
    border-radius: 2px;
    transition: transform 0.2s ease, opacity 0.2s ease;
}

/* ---------- Buttons ---------- */
.btn {
    display: inline-block;
    padding: 13px 26px;
    border-radius: 3px;
    text-decoration: none;
    font-family: var(--font-body);
    font-weight: 600;
    font-size: 0.95rem;
    cursor: pointer;
    border: 1px solid transparent;
    transition: transform 0.15s ease, background 0.15s ease, border-color 0.15s ease;
}

.btn:hover {
    transform: translateY(-1px);
}

.btn-primary {
    background: var(--ember);
    color: var(--cream);
}

.btn-primary:hover {
    background: #E1541F;
}

.btn-ghost {
    background: transparent;
    border-color: var(--border);
    color: var(--cream);
}

.btn-ghost:hover {
    border-color: var(--turmeric);
}

/* ---------- Hero ---------- */
.hero {
    max-width: var(--max-w);
    margin: 0 auto;
    padding: 90px 24px 100px;
    display: grid;
    grid-template-columns: 1.3fr 0.7fr;
    gap: 40px;
    align-items: center;
}

.hero-kicker {
    color: var(--turmeric);
    font-size: 0.95rem;
    margin-bottom: 18px;
}

.hero-title {
    font-size: clamp(2.4rem, 5vw, 3.6rem);
    line-height: 1.12;
    max-width: 14ch;
}

.hero-sub {
    margin-top: 24px;
    max-width: 46ch;
    font-size: 1.05rem;
}

.hero-actions {
    margin-top: 36px;
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
}

.hero-mark {
    display: flex;
    justify-content: center;
}

.ember-svg {
    width: 100%;
    max-width: 220px;
}

.ember-glow {
    fill: var(--ember-dim);
    opacity: 0.55;
}

.ember-flame {
    fill: none;
    stroke: var(--turmeric);
    stroke-width: 4;
    stroke-linecap: round;
}

/* ---------- Section shell ---------- */
section {
    max-width: var(--max-w);
    margin: 0 auto;
    padding: 80px 24px;
}

.section-head {
    margin-bottom: 44px;
    max-width: 56ch;
}

.section-head h2 {
    font-size: clamp(1.8rem, 3.5vw, 2.4rem);
    margin-bottom: 12px;
}

/* ---------- Menu ---------- */
.menu-section {
    border-top: 1px solid var(--border);
}

.menu-tabs {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-bottom: 40px;
}

.tab-btn {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--cream-dim);
    padding: 9px 18px;
    border-radius: 999px;
    font-family: var(--font-body);
    font-size: 0.9rem;
    cursor: pointer;
    transition: border-color 0.15s ease, color 0.15s ease;
}

.tab-btn.is-active,
.tab-btn:hover {
    border-color: var(--turmeric);
    color: var(--turmeric);
}

.menu-list {
    display: flex;
    flex-direction: column;
}

.menu-item {
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: baseline;
    column-gap: 20px;
    padding: 22px 0;
    border-bottom: 1px solid var(--border);
}

.menu-item:first-child {
    border-top: 1px solid var(--border);
}

.menu-item-name {
    font-family: var(--font-display);
    font-size: 1.2rem;
    grid-column: 1;
}

.menu-item-tag {
    font-family: var(--font-body);
    font-size: 0.72rem;
    color: var(--olive);
    border: 1px solid var(--olive);
    border-radius: 3px;
    padding: 2px 8px;
    margin-left: 10px;
    vertical-align: middle;
}

.menu-item-desc {
    grid-column: 1;
    margin-top: 6px;
    font-size: 0.92rem;
    max-width: 52ch;
}

.menu-item-price {
    grid-column: 2;
    grid-row: 1;
    font-family: var(--font-display);
    font-size: 1.15rem;
    color: var(--turmeric);
    white-space: nowrap;
}

.menu-item-price::before {
    content: "Rs. ";
    font-size: 0.7rem;
    color: var(--cream-dim);
}

/* ---------- Kahani ---------- */
.kahani-section {
    background: var(--bg-raised);
    max-width: none;
    padding: 90px 24px;
}

.kahani-inner {
    max-width: 640px;
    margin: 0 auto;
}

.kahani-inner h2 {
    margin-bottom: 24px;
}

.kahani-inner p {
    font-size: 1.05rem;
    margin-bottom: 18px;
}

.kahani-inner p:last-child {
    margin-bottom: 0;
}

/* ---------- Waqt ---------- */
.waqt-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 30px;
}

.waqt-card {
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 28px;
}

.waqt-card h3 {
    font-size: 1.15rem;
    margin-bottom: 16px;
}

.waqt-times div {
    display: flex;
    justify-content: space-between;
    padding: 8px 0;
    border-bottom: 1px solid var(--border);
}

.waqt-times div:last-child {
    border-bottom: none;
}

.waqt-times dt {
    color: var(--cream-dim);
}

.waqt-times dd {
    margin: 0;
}

.waqt-card p {
    margin-bottom: 8px;
}

.waqt-card p:last-child {
    margin-bottom: 0;
}

/* ---------- Order Form ---------- */
.order-section {
    border-top: 1px solid var(--border);
}

.order-form {
    max-width: 520px;
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.form-row {
    display: flex;
    flex-direction: column;
    gap: 6px;
}

.form-row label {
    font-size: 0.88rem;
    color: var(--cream-dim);
}

.form-row input,
.form-row textarea {
    background: var(--bg-raised);
    border: 1px solid var(--border);
    border-radius: 3px;
    padding: 12px 14px;
    color: var(--cream);
    font-family: var(--font-body);
    font-size: 0.95rem;
    resize: vertical;
}

.form-row input::placeholder,
.form-row textarea::placeholder {
    color: rgba(243, 231, 211, 0.35);
}

.field-msg {
    font-size: 0.8rem;
    color: var(--ember);
    min-height: 1em;
}

.order-form .btn {
    align-self: flex-start;
}

.form-status {
    font-size: 0.92rem;
    color: var(--olive);
    min-height: 1.2em;
}

/* ---------- Footer ---------- */
.site-footer {
    border-top: 1px solid var(--border);
    padding: 30px 24px;
    text-align: center;
}

.site-footer p {
    font-size: 0.85rem;
}

/* ---------- Responsive ---------- */
@media (max-width: 760px) {
    .main-nav {
        position: absolute;
        top: 100%;
        left: 0;
        right: 0;
        flex-direction: column;
        gap: 0;
        background: var(--bg);
        border-bottom: 1px solid var(--border);
        max-height: 0;
        overflow: hidden;
        transition: max-height 0.25s ease;
    }

    .main-nav.is-open {
        max-height: 300px;
    }

    .main-nav a {
        padding: 16px 24px;
        border-top: 1px solid var(--border);
    }

    .nav-toggle {
        display: flex;
    }

    .hero {
        grid-template-columns: 1fr;
        padding-top: 50px;
    }

    .hero-mark {
        order: -1;
        max-width: 140px;
        margin: 0 auto;
    }

    .waqt-grid {
        grid-template-columns: 1fr;
    }

    .menu-item {
        grid-template-columns: 1fr;
    }

    .menu-item-price {
        grid-column: 1;
        grid-row: 2;
        margin-top: 6px;
    }
}
