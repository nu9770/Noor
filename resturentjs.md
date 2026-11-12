// ---------- Mobile nav toggle ----------
const navToggle = document.getElementById('navToggle');
const mainNav = document.getElementById('mainNav');

navToggle.addEventListener('click', () => {
    const isOpen = mainNav.classList.toggle('is-open');
    navToggle.setAttribute('aria-expanded', String(isOpen));
});

// Nav band khud band ho jaye jab koi link click ho (mobile par)
mainNav.querySelectorAll('a').forEach(link => {
    link.addEventListener('click', () => {
        mainNav.classList.remove('is-open');
        navToggle.setAttribute('aria-expanded', 'false');
    });
});

// ---------- Menu category tabs ----------
const tabButtons = document.querySelectorAll('.tab-btn');
const menuItems = document.querySelectorAll('.menu-item');

tabButtons.forEach(btn => {
    btn.addEventListener('click', () => {
        const category = btn.dataset.cat;

        tabButtons.forEach(b => b.classList.remove('is-active'));
        btn.classList.add('is-active');

        menuItems.forEach(item => {
            const match = item.dataset.cat === category;
            item.style.display = match ? '' : 'none';
        });
    });
});

// ---------- Order form validation ----------
const orderForm = document.getElementById('orderForm');
const nameInput = document.getElementById('nameInput');
const phoneInput = document.getElementById('phoneInput');
const orderInput = document.getElementById('orderInput');

const nameMsg = document.getElementById('nameMsg');
const phoneMsg = document.getElementById('phoneMsg');
const orderMsg = document.getElementById('orderMsg');
const formStatus = document.getElementById('formStatus');

function validatePhone(value) {
    // Pakistani mobile number jaisa kuch: 03XXXXXXXXX ya 0300-1234567
    const digitsOnly = value.replace(/[\s-]/g, '');
    return /^03\d{9}$/.test(digitsOnly);
}

function setError(input, msgEl, message) {
    msgEl.textContent = message;
    input.style.borderColor = message ? '#D2491D' : '';
}

orderForm.addEventListener('submit', (event) => {
    event.preventDefault();
    let hasError = false;

    if (nameInput.value.trim().length < 2) {
        setError(nameInput, nameMsg, 'Apna poora naam likhein.');
        hasError = true;
    } else {
        setError(nameInput, nameMsg, '');
    }

    if (!validatePhone(phoneInput.value.trim())) {
        setError(phoneInput, phoneMsg, 'Sahi number likhein, jaise 03XX-XXXXXXX.');
        hasError = true;
    } else {
        setError(phoneInput, phoneMsg, '');
    }

    if (orderInput.value.trim().length < 4) {
        setError(orderInput, orderMsg, 'Order ki tafseel likhein.');
        hasError = true;
    } else {
        setError(orderInput, orderMsg, '');
    }

    if (hasError) {
        formStatus.textContent = '';
        return;
    }

    // Yahan asal app mein order backend/API ko bheja jayega.
    formStatus.textContent = `Shukriya, ${nameInput.value.trim()}! Aapka order mil gaya hai, hum jald rabta karenge.`;
    orderForm.reset();
});
