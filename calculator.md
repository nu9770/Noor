<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <style>
        :root {
            --bg-1: #0b0f1a;
            --bg-2: #141a2e;
            --glass: rgba(255, 255, 255, 0.06);
            --glass-border: rgba(255, 255, 255, 0.12);
            --accent: #7dfff0;
            --accent-2: #a78bfa;
            --op: #ff8a65;
            --text: #eef2ff;
            --muted: #8b93b0;
        }

        * {
            box-sizing: border-box;
        }

        html,
        body {
            height: 100%;
            margin: 0;
            font-family: 'Segoe UI', system-ui, sans-serif;
            background:
                radial-gradient(circle at 20% 15%, rgba(167, 139, 250, 0.18), transparent 40%),
                radial-gradient(circle at 85% 80%, rgba(125, 255, 240, 0.14), transparent 45%),
                linear-gradient(160deg, var(--bg-1), var(--bg-2));
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        /* ambient floating orbs */
        .orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(60px);
            opacity: 0.35;
            pointer-events: none;
            animation: float 12s ease-in-out infinite;
        }

        .orb.one {
            width: 260px;
            height: 260px;
            background: var(--accent-2);
            top: -60px;
            left: -60px;
        }

        .orb.two {
            width: 220px;
            height: 220px;
            background: var(--accent);
            bottom: -60px;
            right: -40px;
            animation-delay: 3s;
        }

        @keyframes float {

            0%,
            100% {
                transform: translate(0, 0) scale(1);
            }

            50% {
                transform: translate(20px, -20px) scale(1.08);
            }
        }

        .calculator {
            position: relative;
            width: 340px;
            padding: 22px;
            border-radius: 28px;
            background: var(--glass);
            border: 1px solid var(--glass-border);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            box-shadow:
                0 20px 60px rgba(0, 0, 0, 0.55),
                inset 0 1px 0 rgba(255, 255, 255, 0.08);
            animation: riseIn 0.6s cubic-bezier(.2, .9, .25, 1);
        }

        @keyframes riseIn {
            from {
                opacity: 0;
                transform: translateY(24px) scale(0.97);
            }

            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .display {
            position: relative;
            margin-bottom: 18px;
            padding: 22px 18px 16px;
            border-radius: 18px;
            background: linear-gradient(145deg, rgba(0, 0, 0, 0.35), rgba(255, 255, 255, 0.03));
            border: 1px solid rgba(255, 255, 255, 0.08);
            text-align: right;
            overflow: hidden;
            min-height: 96px;
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
        }

        .display::before {
            content: '';
            position: absolute;
            inset: 0;
            background: linear-gradient(90deg, transparent, rgba(125, 255, 240, 0.06), transparent);
            transform: translateX(-100%);
            animation: sheen 5s ease-in-out infinite;
        }

        @keyframes sheen {
            0% {
                transform: translateX(-100%);
            }

            45%,
            100% {
                transform: translateX(120%);
            }
        }

        .prev-op {
            font-size: 14px;
            color: var(--muted);
            min-height: 18px;
            letter-spacing: 0.5px;
            font-variant-numeric: tabular-nums;
            transition: opacity 0.2s ease;
        }

        .current {
            font-size: 38px;
            font-weight: 600;
            color: var(--text);
            letter-spacing: 1px;
            font-variant-numeric: tabular-nums;
            word-break: break-all;
            text-shadow: 0 0 18px rgba(125, 255, 240, 0.25);
            transition: transform 0.15s ease;
        }

        .current.pulse {
            animation: pulse 0.28s ease;
        }

        @keyframes pulse {
            0% {
                transform: scale(1);
            }

            40% {
                transform: scale(1.08);
            }

            100% {
                transform: scale(1);
            }
        }

        .keys {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        button {
            position: relative;
            overflow: hidden;
            border: none;
            outline: none;
            padding: 18px 0;
            border-radius: 16px;
            font-size: 18px;
            font-weight: 600;
            color: var(--text);
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.08);
            cursor: pointer;
            transition: transform 0.12s ease, background 0.2s ease, box-shadow 0.2s ease;
        }

        button:hover {
            background: rgba(255, 255, 255, 0.09);
            transform: translateY(-2px);
        }

        button:active {
            transform: translateY(0) scale(0.95);
        }

        /* ripple */
        button::after {
            content: '';
            position: absolute;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.5);
            width: 8px;
            height: 8px;
            left: var(--x, 50%);
            top: var(--y, 50%);
            transform: translate(-50%, -50%) scale(0);
            opacity: 0.6;
            pointer-events: none;
        }

        button.rippling::after {
            animation: ripple 0.5s ease-out;
        }

        @keyframes ripple {
            to {
                transform: translate(-50%, -50%) scale(22);
                opacity: 0;
            }
        }

        .op {
            background: linear-gradient(145deg, rgba(255, 138, 101, 0.22), rgba(255, 138, 101, 0.08));
            color: #ffb199;
            border-color: rgba(255, 138, 101, 0.3);
        }

        .op:hover {
            background: linear-gradient(145deg, rgba(255, 138, 101, 0.32), rgba(255, 138, 101, 0.14));
        }

        .op.active {
            box-shadow: 0 0 0 2px rgba(255, 138, 101, 0.55), 0 0 18px rgba(255, 138, 101, 0.35);
        }

        .fn {
            color: var(--accent-2);
            background: rgba(167, 139, 250, 0.12);
            border-color: rgba(167, 139, 250, 0.25);
        }

        .fn:hover {
            background: rgba(167, 139, 250, 0.2);
        }

        .equals {
            grid-column: span 2;
            background: linear-gradient(135deg, #7dfff0, #4fd1c5);
            color: #04211d;
            font-weight: 700;
            border: none;
            box-shadow: 0 8px 22px rgba(79, 209, 197, 0.35);
        }

        .equals:hover {
            box-shadow: 0 10px 26px rgba(79, 209, 197, 0.5);
            background: linear-gradient(135deg, #8bfff2, #5fe0d3);
        }

        .zero {
            grid-column: span 2;
        }

        @media (max-width:380px) {
            .calculator {
                width: 92vw;
                padding: 16px;
            }

            .current {
                font-size: 32px;
            }
        }
    </style>
</head>

<body>

    <div class="orb one"></div>
    <div class="orb two"></div>

    <div class="calculator">
        <div class="display">
            <div class="prev-op" id="prevOp">&nbsp;</div>
            <div class="current" id="current">0</div>
        </div>

        <div class="keys">
            <button class="fn" data-action="clear">AC</button>
            <button class="fn" data-action="negate">+/-</button>
            <button class="fn" data-action="percent">%</button>
            <button class="op" data-action="divide">÷</button>

            <button data-num="7">7</button>
            <button data-num="8">8</button>
            <button data-num="9">9</button>
            <button class="op" data-action="multiply">×</button>

            <button data-num="4">4</button>
            <button data-num="5">5</button>
            <button data-num="6">6</button>
            <button class="op" data-action="subtract">−</button>

            <button data-num="1">1</button>
            <button data-num="2">2</button>
            <button data-num="3">3</button>
            <button class="op" data-action="add">+</button>

            <button class="zero" data-num="0">0</button>
            <button data-action="decimal">.</button>
            <button class="equals" data-action="equals">=</button>
        </div>
    </div>

    <script>
        const currentEl = document.getElementById('current');
        const prevOpEl = document.getElementById('prevOp');

        let current = '0';
        let previous = null;
        let operator = null;
        let justEvaluated = false;

        function formatNumber(numStr) {
            if (numStr === 'Error') return numStr;
            const [intPart, decPart] = numStr.split('.');
            const withCommas = intPart.replace(/\B(?=(\d{3})+(?!\d))/g, ',');
            return decPart !== undefined ? withCommas + '.' + decPart : withCommas;
        }

        function updateDisplay() {
            currentEl.textContent = formatNumber(current);
            if (operator && previous !== null) {
                const opSymbol = { add: '+', subtract: '−', multiply: '×', divide: '÷' }[operator];
                prevOpEl.textContent = `${formatNumber(previous)} ${opSymbol}`;
            } else {
                prevOpEl.textContent = '\u00A0';
            }
            currentEl.classList.remove('pulse');
            void currentEl.offsetWidth; // reflow to restart animation
            currentEl.classList.add('pulse');
        }

        function inputDigit(d) {
            if (justEvaluated) {
                current = d;
                justEvaluated = false;
                return;
            }
            if (current === '0') {
                current = d;
            } else {
                if (current.replace('-', '').replace('.', '').length >= 15) return;
                current += d;
            }
        }

        function inputDecimal() {
            if (justEvaluated) {
                current = '0.';
                justEvaluated = false;
                return;
            }
            if (!current.includes('.')) current += '.';
        }

        function setOperator(op) {
            if (operator && previous !== null && !justEvaluated) {
                evaluate();
            }
            previous = current;
            operator = op;
            justEvaluated = false;
            current = '0';
            highlightOperator(op);
        }

        function highlightOperator(op) {
            document.querySelectorAll('.op').forEach(btn => btn.classList.remove('active'));
            if (op) {
                const btn = document.querySelector(`.op[data-action="${op}"]`);
                if (btn) btn.classList.add('active');
            }
        }

        function evaluate() {
            if (operator === null || previous === null) return;
            const a = parseFloat(previous);
            const b = parseFloat(current);
            let result;
            switch (operator) {
                case 'add': result = a + b; break;
                case 'subtract': result = a - b; break;
                case 'multiply': result = a * b; break;
                case 'divide': result = b === 0 ? NaN : a / b; break;
            }
            current = isNaN(result) ? 'Error' : trimResult(result);
            previous = null;
            operator = null;
            justEvaluated = true;
            highlightOperator(null);
        }

        function trimResult(num) {
            let str = num.toString();
            if (str.includes('e') || str.length > 15) {
                str = num.toPrecision(10).replace(/\.?0+$/, '').replace(/\.?0+e/, 'e');
            }
            return str;
        }

        function clearAll() {
            current = '0';
            previous = null;
            operator = null;
            justEvaluated = false;
            highlightOperator(null);
        }

        function negate() {
            if (current === '0' || current === 'Error') return;
            current = current.startsWith('-') ? current.slice(1) : '-' + current;
        }

        function percent() {
            if (current === 'Error') return;
            current = trimResult(parseFloat(current) / 100);
        }

        function handleAction(action) {
            switch (action) {
                case 'clear': clearAll(); break;
                case 'negate': negate(); break;
                case 'percent': percent(); break;
                case 'decimal': inputDecimal(); break;
                case 'equals': evaluate(); break;
                case 'add':
                case 'subtract':
                case 'multiply':
                case 'divide':
                    setOperator(action);
                    break;
            }
            updateDisplay();
        }

        document.querySelectorAll('button').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const rect = btn.getBoundingClientRect();
                btn.style.setProperty('--x', (e.clientX - rect.left) + 'px');
                btn.style.setProperty('--y', (e.clientY - rect.top) + 'px');
                btn.classList.remove('rippling');
                void btn.offsetWidth;
                btn.classList.add('rippling');

                const num = btn.getAttribute('data-num');
                const action = btn.getAttribute('data-action');
                if (num !== null) {
                    inputDigit(num);
                    updateDisplay();
                } else if (action) {
                    handleAction(action);
                }
            });
        });

        // keyboard support
        window.addEventListener('keydown', (e) => {
            if (e.key >= '0' && e.key <= '9') { inputDigit(e.key); updateDisplay(); }
            else if (e.key === '.') { inputDecimal(); updateDisplay(); }
            else if (e.key === '+') { handleAction('add'); }
            else if (e.key === '-') { handleAction('subtract'); }
            else if (e.key === '*') { handleAction('multiply'); }
            else if (e.key === '/') { e.preventDefault(); handleAction('divide'); }
            else if (e.key === 'Enter' || e.key === '=') { handleAction('equals'); }
            else if (e.key === 'Escape') { handleAction('clear'); }
            else if (e.key === '%') { handleAction('percent'); }
            else if (e.key === 'Backspace') {
                current = current.length > 1 ? current.slice(0, -1) : '0';
                updateDisplay();
            }
        });

        updateDisplay();
    </script>

</body>

</html>
