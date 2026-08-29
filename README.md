<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>For My Love ❤️</title>
    <style>
        /* ----- RESET & BASE ----- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html, body {
            min-height: 100vh;
        }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            background: #6b0a3a;
            font-family: 'Segoe UI', 'Poppins', system-ui, sans-serif;
            /* FIX: allow vertical scrolling, hide horizontal overflow */
            overflow-y: auto;
            overflow-x: hidden;
            position: relative;
            padding: 20px 0;
        }

        body::before {
            content: '';
            position: fixed;
            inset: 0;
            background: radial-gradient(ellipse at 50% 80%, #9b1b5e 0%, #4d0628 100%);
            z-index: 0;
            animation: bgPulse 8s ease-in-out infinite alternate;
            pointer-events: none;
        }

        @keyframes bgPulse {
            0% {
                opacity: 0.7;
                transform: scale(1);
            }
            100% {
                opacity: 1;
                transform: scale(1.05);
            }
        }

        /* ----- FLOATING HEARTS ----- */
        .floating-hearts {
            position: fixed;
            inset: 0;
            z-index: 1;
            pointer-events: none;
            overflow: hidden;
        }

        .float-heart {
            position: absolute;
            font-size: 1.4rem;
            opacity: 0.2;
            animation: floatUp linear infinite;
            user-select: none;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(110vh) rotate(0deg) scale(0.6);
                opacity: 0.1;
            }
            20% {
                opacity: 0.25;
            }
            100% {
                transform: translateY(-10vh) rotate(720deg) scale(1.2);
                opacity: 0;
            }
        }

        /* ----- CARD WRAPPER (handles disappear transition) ----- */
        .card-wrapper {
            position: relative;
            z-index: 10;
            padding: 20px;
            margin: 20px auto; /* FIX: added margin for scroll breathing room */
            transition: all 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
            transform-origin: center;
            opacity: 1;
            transform: scale(1) translateY(0) rotate(0deg);
            pointer-events: auto;
            max-width: 560px;
            width: 100%;
        }

        .card-wrapper.hidden {
            opacity: 0;
            transform: scale(0.5) translateY(-80px) rotate(-6deg);
            pointer-events: none;
        }

        .card {
            width: 100%;
            padding: 40px 35px 35px;
            background: #ffe2ec;
            border-radius: 32px;
            border: 4px solid #ffb0c8;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5), 0 0 0 1px rgba(255, 200, 220, 0.3) inset,
                0 0 40px rgba(255, 150, 200, 0.15);
            text-align: center;
            position: relative;
            backdrop-filter: blur(2px);
        }

        /* ----- MAIN MESSAGE ----- */
        .message {
            font-size: 1.55rem;
            font-weight: 700;
            line-height: 1.4;
            color: #7a1a44;
            letter-spacing: -0.2px;
            margin-bottom: 8px;
            font-family: 'Poppins', 'Segoe UI', sans-serif;
        }

        .message .highlight {
            color: #c41e5a;
            display: inline-block;
            animation: textGlow 2s ease-in-out infinite alternate;
        }

        @keyframes textGlow {
            0% {
                text-shadow: 0 0 4px rgba(196, 30, 90, 0.2);
            }
            100% {
                text-shadow: 0 0 20px rgba(196, 30, 90, 0.35), 0 0 40px rgba(196, 30, 90, 0.1);
            }
        }

        /* ----- MINI CARD (second message) ----- */
        .mini-card {
            background: rgba(255, 255, 255, 0.35);
            backdrop-filter: blur(4px);
            border: 2.5px solid #e8709a;
            border-radius: 24px;
            padding: 14px 18px;
            margin: 16px 0 18px;
            display: inline-block;
            box-shadow: 0 4px 20px rgba(196, 30, 90, 0.15);
            transition: transform 0.3s ease;
        }

        .mini-card:hover {
            transform: scale(1.02);
        }

        .mini-card p {
            font-size: 1.4rem;
            font-weight: 700;
            color: #7a1a44;
            letter-spacing: -0.2px;
            margin: 0;
        }

        .mini-card p span {
            display: inline-block;
            animation: heartBeat 1.6s ease-in-out infinite;
        }

        .sub-message {
            font-size: 1rem;
            color: #a0466a;
            margin-top: 2px;
            margin-bottom: 14px;
            font-weight: 400;
            letter-spacing: 1px;
            opacity: 0.8;
        }

        .sub-message span {
            display: inline-block;
            animation: heartBeat 1.6s ease-in-out infinite;
        }

        @keyframes heartBeat {
            0%,
            100% {
                transform: scale(1);
            }
            15% {
                transform: scale(1.3);
            }
            30% {
                transform: scale(1);
            }
            45% {
                transform: scale(1.2);
            }
            60% {
                transform: scale(1);
            }
        }

        /* ----- STATIC PHOTO ----- */
        .photo-section {
            margin: 10px 0 14px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
        }

        .photo-preview {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            border: 4px solid #ffb0c8;
            overflow: hidden;
            background: #f5d0de;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2.8rem;
            color: #b05a7a;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
            object-fit: cover;
            transition: border-color 0.4s ease, box-shadow 0.4s ease;
        }

        .photo-preview img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
        }

        .photo-preview .placeholder-icon {
            opacity: 0.4;
        }

        .photo-label {
            font-size: 0.85rem;
            color: #a0466a;
            font-weight: 500;
            padding: 6px 18px;
            border-radius: 30px;
            background: rgba(255, 176, 200, 0.15);
            border: 1.5px dashed #d48aaa;
            display: inline-block;
            margin-top: 2px;
        }

        /* ----- HEART BUTTON ----- */
        .heart-btn-wrap {
            margin: 10px 0 2px;
            display: flex;
            justify-content: center;
        }

        .heart-btn {
            background: none;
            border: none;
            cursor: pointer;
            font-size: 3.4rem;
            padding: 6px 18px;
            transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), filter 0.4s ease;
            filter: drop-shadow(0 4px 12px rgba(196, 30, 90, 0.25));
            display: inline-flex;
            align-items: center;
            justify-content: center;
            position: relative;
            user-select: none;
            z-index: 20;
        }

        .heart-btn:hover {
            transform: scale(1.18);
            filter: drop-shadow(0 6px 24px rgba(196, 30, 90, 0.45));
        }

        .heart-btn:active {
            transform: scale(0.92);
        }

        .heart-btn .heart-text {
            position: absolute;
            bottom: -22px;
            font-size: 0.7rem;
            color: #b05a7a;
            font-weight: 500;
            letter-spacing: 0.5px;
            opacity: 0;
            transition: opacity 0.4s ease;
            white-space: nowrap;
        }

        .heart-btn:hover .heart-text {
            opacity: 0.8;
        }

        .heart-btn .pulse-ring {
            position: absolute;
            inset: -12px;
            border-radius: 50%;
            border: 2px solid rgba(255, 100, 150, 0.15);
            animation: ringPulse 2s ease-out infinite;
            pointer-events: none;
        }

        @keyframes ringPulse {
            0% {
                transform: scale(0.8);
                opacity: 1;
            }
            100% {
                transform: scale(1.8);
                opacity: 0;
            }
        }

        /* ----- ROSES CANVAS ----- */
        #rosesCanvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 5;
            pointer-events: none;
        }

        /* ----- RESPONSIVE ----- */
        @media (max-width: 600px) {
            .card {
                padding: 28px 20px 24px;
                border-radius: 24px;
            }
            .message {
                font-size: 1.25rem;
            }
            .mini-card p {
                font-size: 1.15rem;
            }
            .sub-message {
                font-size: 0.85rem;
            }
            .photo-preview {
                width: 96px;
                height: 96px;
                font-size: 2.2rem;
            }
            .heart-btn {
                font-size: 2.8rem;
            }
            .float-heart {
                font-size: 1rem;
            }
        }

        @media (max-width: 400px) {
            .card {
                padding: 18px 12px 16px;
            }
            .message {
                font-size: 1.05rem;
            }
            .mini-card p {
                font-size: 1rem;
            }
            .photo-preview {
                width: 80px;
                height: 80px;
                font-size: 1.8rem;
            }
            .heart-btn {
                font-size: 2.4rem;
            }
        }

        .sparkle-container {
            position: fixed;
            inset: 0;
            z-index: 2;
            pointer-events: none;
            overflow: hidden;
        }

        .sparkle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: #ffd0e0;
            border-radius: 50%;
            box-shadow: 0 0 6px #ffa0c0;
            animation: sparkleAnim linear infinite;
            opacity: 0;
        }

        @keyframes sparkleAnim {
            0% {
                opacity: 0;
                transform: scale(0) rotate(0deg);
            }
            30% {
                opacity: 0.8;
                transform: scale(1.2) rotate(60deg);
            }
            70% {
                opacity: 0.5;
                transform: scale(0.8) rotate(120deg);
            }
            100% {
                opacity: 0;
                transform: scale(0) rotate(180deg);
            }
        }

        .footer-note {
            position: fixed;
            bottom: 16px;
            left: 0;
            right: 0;
            text-align: center;
            color: rgba(255, 200, 220, 0.25);
            font-size: 0.7rem;
            letter-spacing: 2px;
            z-index: 3;
            pointer-events: none;
            font-weight: 300;
        }
    </style>
</head>
<body>

    <!-- BACKGROUND FLOATING HEARTS -->
    <div class="floating-hearts" id="floatingHearts"></div>

    <!-- SPARKLE CONTAINER -->
    <div class="sparkle-container" id="sparkleContainer"></div>

    <!-- ROSES CANVAS -->
    <canvas id="rosesCanvas"></canvas>

    <!-- MAIN CARD -->
    <div class="card-wrapper" id="cardWrapper">
        <div class="card" id="mainCard">

            <!-- MAIN MESSAGE (updated) -->
            <div class="message">
                I am here for you sweety<br />
                and you are <span class="highlight">not alone</span> !!!!<br />
                I am <span class="highlight">always</span> and<br />
                <span class="highlight">always will be</span> here !!
            </div>

            <!-- MINI CARD (second message) -->
            <div class="mini-card">
                <p>
                    💖 Love you soo much hunzz !!! 💖
                    <span>❤️</span>
                </p>
            </div>

            <div class="sub-message">
                <span>✨</span> you are my everything <span>✨</span>
            </div>

            <!-- PHOTO SECTION (hardcoded with your file) -->
            <div class="photo-section">
                <div class="photo-preview" id="photoPreview">
                    <img id="ourPhoto" 
                         src="file:///C:/Users/msi/Downloads/WhatsApp%20Image%202026-08-25%20at%2017.41.58.jpeg" 
                         alt="Our photo" 
                         onerror="this.style.display='none'; this.parentElement.innerHTML='<span class=\'placeholder-icon\'>❤️</span>';" 
                    />
                </div>
                <div class="photo-label">📸 our moment</div>
            </div>

            <!-- HEART BUTTON -->
            <div class="heart-btn-wrap">
                <button class="heart-btn" id="heartBtn" aria-label="Click to see roses">
                    <span class="pulse-ring"></span>
                    ❤️
                    <span class="heart-text">tap for roses</span>
                </button>
            </div>

        </div>
    </div>

    <div class="footer-note">made with all my love ❤️</div>

    <script>
        // ============================================================
        //  1. FLOATING HEARTS
        // ============================================================
        (function initFloatingHearts() {
            const container = document.getElementById('floatingHearts');
            const hearts = ['❤️', '💕', '💗', '💖', '💘', '🌹'];
            for (let i = 0; i < 26; i++) {
                const el = document.createElement('span');
                el.className = 'float-heart';
                el.textContent = hearts[i % hearts.length];
                el.style.left = Math.random() * 100 + '%';
                el.style.fontSize = (0.8 + Math.random() * 1.4) + 'rem';
                el.style.animationDuration = (12 + Math.random() * 18) + 's';
                el.style.animationDelay = (Math.random() * 20) + 's';
                el.style.opacity = 0.08 + Math.random() * 0.15;
                container.appendChild(el);
            }
        })();

        // ============================================================
        //  2. SPARKLES
        // ============================================================
        (function initSparkles() {
            const container = document.getElementById('sparkleContainer');
            for (let i = 0; i < 40; i++) {
                const el = document.createElement('div');
                el.className = 'sparkle';
                el.style.left = Math.random() * 100 + '%';
                el.style.top = Math.random() * 100 + '%';
                const size = 2 + Math.random() * 4;
                el.style.width = size + 'px';
                el.style.height = size + 'px';
                el.style.animationDuration = (4 + Math.random() * 8) + 's';
                el.style.animationDelay = (Math.random() * 10) + 's';
                el.style.background = `hsl(${330 + Math.random() * 30}, 80%, 75%)`;
                container.appendChild(el);
            }
        })();

        // ============================================================
        //  3. ROSES CANVAS — now with MORE roses!
        // ============================================================
        const canvas = document.getElementById('rosesCanvas');
        const ctx = canvas.getContext('2d');
        let W, H;

        function resizeCanvas() {
            W = canvas.width = window.innerWidth;
            H = canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        // ---- rose drawing helpers ----
        function drawPetal(ctx, cx, cy, r, angle, color, squash) {
            squash = squash || 0.7;
            ctx.save();
            ctx.translate(cx, cy);
            ctx.rotate(angle);
            ctx.beginPath();
            ctx.moveTo(0, 0);
            ctx.bezierCurveTo(r * 0.5, -r * 0.35 * squash, r * 0.8, -r * 0.7 * squash, 0, -r * squash);
            ctx.bezierCurveTo(-r * 0.8, -r * 0.7 * squash, -r * 0.5, -r * 0.35 * squash, 0, 0);
            ctx.closePath();
            ctx.fillStyle = color;
            ctx.fill();
            ctx.restore();
        }

        function drawRose(ctx, x, y, size, hue, bloom) {
            const b = Math.min(bloom, 1);
            const layers = 4;
            const petalsPerLayer = [5, 7, 9, 11];
            const layerRadii = [0.28, 0.52, 0.78, 1.0];
            const hueShift = hue || 340;

            const colors = [
                `hsl(${hueShift}, 85%, 30%)`,
                `hsl(${hueShift + 5}, 80%, 48%)`,
                `hsl(${hueShift + 10}, 85%, 62%)`,
                `hsl(${hueShift + 15}, 90%, 76%)`
            ];

            const spread = 0.4 + b * 0.6;

            for (let layer = 0; layer < layers; layer++) {
                const n = petalsPerLayer[layer];
                const radius = size * layerRadii[layer] * (0.6 + b * 0.4);
                const color = colors[layer];
                const petalSize = size * (0.25 + 0.35 * (layer / layers)) * (0.7 + b * 0.3);

                for (let i = 0; i < n; i++) {
                    const angleOffset = layer * 0.35 + i * (Math.PI * 2 / n) + (1 - b) * 0.15;
                    const px = x + Math.cos(angleOffset) * radius * spread;
                    const py = y + Math.sin(angleOffset) * radius * spread * 0.9;
                    const petalAngle = angleOffset + (1 - b) * 0.2;
                    const squash = 0.6 + 0.25 * b;
                    drawPetal(ctx, px, py, petalSize * (0.7 + 0.3 * b), petalAngle, color, squash);
                }
            }

            const budSize = size * 0.12 * (1 + 0.2 * (1 - b));
            ctx.beginPath();
            ctx.arc(x, y, budSize, 0, Math.PI * 2);
            ctx.fillStyle = `hsl(${hueShift - 5}, 80%, 25%)`;
            ctx.fill();
            ctx.beginPath();
            ctx.arc(x - budSize * 0.2, y - budSize * 0.2, budSize * 0.25, 0, Math.PI * 2);
            ctx.fillStyle = `hsl(${hueShift + 10}, 70%, 50%)`;
            ctx.fill();
        }

        function drawStem(ctx, x1, y1, x2, y2, width) {
            ctx.beginPath();
            ctx.moveTo(x1, y1);
            const cx = (x1 + x2) / 2 + (Math.random() - 0.5) * 6;
            const cy = (y1 + y2) / 2 + (Math.random() - 0.5) * 4;
            ctx.quadraticCurveTo(cx, cy, x2, y2);
            ctx.strokeStyle = '#2d5a1e';
            ctx.lineWidth = width || 3;
            ctx.lineCap = 'round';
            ctx.stroke();
        }

        function drawLeaf(ctx, x, y, angle, size, color) {
            ctx.save();
            ctx.translate(x, y);
            ctx.rotate(angle);
            ctx.beginPath();
            ctx.moveTo(0, 0);
            ctx.bezierCurveTo(size * 0.6, -size * 0.3, size * 0.9, -size * 0.1, size, 0);
            ctx.bezierCurveTo(size * 0.9, size * 0.1, size * 0.6, size * 0.3, 0, 0);
            ctx.closePath();
            ctx.fillStyle = color || '#3a7a2a';
            ctx.fill();
            ctx.restore();
        }

        // ---- bouquet state ----
        let roses = [];
        let bloomProgress = 0; // 0..1
        let isAnimating = false;
        let bloomDirection = 1; // 1 = opening, -1 = closing
        let animationId = null;
        let cardVisible = true;

        // ---- generate bouquet with MORE roses ----
        function generateBouquet() {
            roses = [];
            // INCREASED rose count for a fuller bouquet
            const count = 40 + Math.floor(Math.random() * 20);
            const cx = W / 2;
            const cy = H / 2 + 20;

            for (let i = 0; i < count; i++) {
                const angle = Math.random() * Math.PI * 2;
                const dist = 70 + Math.random() * Math.min(W, H) * 0.40;
                const x = cx + Math.cos(angle) * dist * (0.6 + 0.4 * Math.sin(angle * 0.7));
                const y = cy + Math.sin(angle) * dist * 0.7 - 30 + Math.cos(angle * 0.5) * 20;
                const size = 22 + Math.random() * 50;
                const hue = 330 + Math.random() * 30;
                const stemLen = 50 + Math.random() * 100;
                const stemAngle = angle + (Math.random() - 0.5) * 0.6;
                const sx = x + Math.cos(stemAngle + Math.PI) * stemLen * 0.3;
                const sy = y + Math.sin(stemAngle + Math.PI) * stemLen * 0.3 + 40;

                roses.push({
                    x,
                    y,
                    size,
                    hue,
                    stemStartX: sx,
                    stemStartY: sy,
                    stemLen,
                    stemAngle,
                    leaf1: { pos: 0.4 + Math.random() * 0.3, angle: (Math.random() - 0.5) * 1.2, size: 8 + Math.random() *
                            12 },
                    leaf2: { pos: 0.6 + Math.random() * 0.3, angle: (Math.random() - 0.5) * 1.2 + 2.0, size: 8 + Math
                            .random() * 12 },
                    delay: Math.random() * 0.4,
                    speed: 0.6 + Math.random() * 0.8,
                });
            }
            roses.sort((a, b) => a.y - b.y);
        }

        // ---- draw bouquet ----
        function drawBouquet(progress) {
            ctx.clearRect(0, 0, W, H);

            if (progress <= 0) return;

            const grad = ctx.createRadialGradient(W / 2, H / 2 + 30, 10, W / 2, H / 2 + 30, Math.min(W, H) * 0.5);
            grad.addColorStop(0, 'rgba(255, 200, 220, 0.12)');
            grad.addColorStop(0.5, 'rgba(255, 150, 200, 0.06)');
            grad.addColorStop(1, 'rgba(255, 150, 200, 0)');
            ctx.fillStyle = grad;
            ctx.fillRect(0, 0, W, H);

            for (const r of roses) {
                const p = Math.min(1, Math.max(0, (progress - r.delay * 0.3) / (1 - r.delay * 0.3)));
                const bloom = Math.min(1, p * 1.2);
                const scale = 0.2 + 0.8 * p;

                const sx = r.x + Math.cos(r.stemAngle + Math.PI) * r.stemLen * 0.3 * scale;
                const sy = r.y + Math.sin(r.stemAngle + Math.PI) * r.stemLen * 0.3 * scale + 40 * scale;
                const stemEndX = r.x + Math.cos(r.stemAngle + Math.PI) * r.stemLen * scale;
                const stemEndY = r.y + Math.sin(r.stemAngle + Math.PI) * r.stemLen * scale + 40 * scale;

                const stemWidth = 2 + r.size * 0.04;
                drawStem(ctx, sx, sy, stemEndX, stemEndY, stemWidth);

                if (bloom > 0.15) {
                    const leafP = Math.min(1, (bloom - 0.15) / 0.6);
                    const l1 = r.leaf1;
                    const l2 = r.leaf2;
                    const lx1 = sx + (stemEndX - sx) * l1.pos;
                    const ly1 = sy + (stemEndY - sy) * l1.pos;
                    const lx2 = sx + (stemEndX - sx) * l2.pos;
                    const ly2 = sy + (stemEndY - sy) * l2.pos;
                    const leafSize1 = l1.size * leafP * (0.4 + 0.6 * p);
                    const leafSize2 = l2.size * leafP * (0.4 + 0.6 * p);
                    const color1 = `hsl(${120 + Math.random() * 20}, 55%, ${30 + 20 * leafP}%)`;
                    const color2 = `hsl(${120 + Math.random() * 20}, 50%, ${30 + 20 * leafP}%)`;
                    drawLeaf(ctx, lx1, ly1, l1.angle, leafSize1, color1);
                    drawLeaf(ctx, lx2, ly2, l2.angle, leafSize2, color2);
                }

                const roseSize = r.size * (0.2 + 0.8 * p);
                const roseX = r.x + (r.x - stemEndX) * 0.05 * (1 - p);
                const roseY = r.y + (r.y - stemEndY) * 0.05 * (1 - p) - 6 * (1 - p);
                drawRose(ctx, roseX, roseY, roseSize, r.hue, bloom);

                if (bloom > 0.3) {
                    const glow = ctx.createRadialGradient(roseX, roseY, 0, roseX, roseY, roseSize * 0.6);
                    glow.addColorStop(0, `hsla(${r.hue}, 80%, 70%, ${0.06 * bloom})`);
                    glow.addColorStop(1, `hsla(${r.hue}, 80%, 70%, 0)`);
                    ctx.fillStyle = glow;
                    ctx.beginPath();
                    ctx.arc(roseX, roseY, roseSize * 0.6, 0, Math.PI * 2);
                    ctx.fill();
                }
            }

            // falling petals
            if (progress > 0.3) {
                const petalCount = Math.floor(12 + progress * 16);
                for (let i = 0; i < petalCount; i++) {
                    const seed = (i * 137.508) % 1;
                    const px = (seed * 0.7 + 0.15) * W;
                    const py = (0.1 + (i * 0.07 + progress * 0.4) % 0.8) * H;
                    const ps = 4 + 8 * (0.3 + 0.7 * Math.sin(i * 2.3));
                    const rot = i * 0.9 + progress * 1.2;
                    const alpha = 0.1 + 0.2 * (0.5 + 0.5 * Math.sin(i * 1.7 + progress));
                    ctx.save();
                    ctx.translate(px, py);
                    ctx.rotate(rot);
                    ctx.beginPath();
                    ctx.ellipse(0, 0, ps * 0.6, ps * 0.35, 0, 0, Math.PI * 2);
                    ctx.fillStyle = `hsla(${330 + i * 7 % 30}, 70%, 70%, ${alpha})`;
                    ctx.fill();
                    ctx.restore();
                }
            }
        }

        // ---- animation loop ----
        function animateRoses() {
            if (isAnimating) {
                bloomProgress += bloomDirection * 0.012;
                if (bloomProgress >= 1) {
                    bloomProgress = 1;
                    isAnimating = false;
                    spawnCelebration();
                }
                if (bloomProgress <= 0) {
                    bloomProgress = 0;
                    isAnimating = false;
                    const wrapper = document.getElementById('cardWrapper');
                    wrapper.classList.remove('hidden');
                    cardVisible = true;
                }
            }
            drawBouquet(bloomProgress);
            animationId = requestAnimationFrame(animateRoses);
        }

        // ---- celebration sparkles ----
        function spawnCelebration() {
            const container = document.getElementById('sparkleContainer');
            for (let i = 0; i < 40; i++) {
                const el = document.createElement('div');
                el.className = 'sparkle';
                el.style.left = (10 + Math.random() * 80) + '%';
                el.style.top = (10 + Math.random() * 80) + '%';
                const size = 3 + Math.random() * 8;
                el.style.width = size + 'px';
                el.style.height = size + 'px';
                el.style.background = `hsl(${320 + Math.random() * 40}, 90%, 75%)`;
                el.style.boxShadow = `0 0 20px hsl(${320 + Math.random() * 40}, 90%, 75%)`;
                el.style.animationDuration = (1.5 + Math.random() * 3) + 's';
                el.style.animationDelay = (Math.random() * 0.8) + 's';
                container.appendChild(el);
                setTimeout(() => el.remove(), 5000);
            }
        }

        // ---- start background loop ----
        generateBouquet();
        bloomProgress = 0;
        isAnimating = false;
        animateRoses();

        // ============================================================
        //  4. HEART BUTTON – toggle card/roses
        // ============================================================
        const heartBtn = document.getElementById('heartBtn');
        const cardWrapper = document.getElementById('cardWrapper');

        heartBtn.addEventListener('click', function(e) {
            e.preventDefault();
            if (navigator.vibrate) navigator.vibrate(10);

            if (cardVisible) {
                cardWrapper.classList.add('hidden');
                cardVisible = false;
                setTimeout(() => {
                    if (!cardVisible) {
                        bloomProgress = 0;
                        bloomDirection = 1;
                        isAnimating = true;
                    }
                }, 800);
            } else {
                if (!isAnimating) {
                    bloomDirection = -1;
                    isAnimating = true;
                }
            }
        });

        // ============================================================
        //  5. HANDLE RESIZE
        // ============================================================
        let resizeTimeout;
        window.addEventListener('resize', function() {
            clearTimeout(resizeTimeout);
            resizeTimeout = setTimeout(() => {
                resizeCanvas();
                if (!isAnimating) {
                    generateBouquet();
                    drawBouquet(bloomProgress);
                }
            }, 400);
        });

        // ============================================================
        //  6. KEYBOARD SHORTCUT: Space or Enter
        // ============================================================
        document.addEventListener('keydown', function(e) {
            if (e.key === ' ' || e.key === 'Enter') {
                if (e.target.tagName === 'INPUT') return;
                e.preventDefault();
                heartBtn.click();
            }
        });

        console.log('❤️  Made with love for your special person  ❤️');
        console.log('💐  Click the heart to see the magic!');
    </script>

</body>
</html>
