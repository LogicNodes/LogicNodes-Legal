---
layout: default
title: LogicNodes Legal
---

<div class="language-selector-page">
    <div class="selector-content">
        <h1>LogicNodes Legal</h1>
        <p class="subtitle">Choose your language / Vælg dit sprog</p>

        <div class="language-options">
            <a href="{{ '/en/' | relative_url }}" class="language-option">
                <span class="flag">🇬🇧</span>
                <span class="language-name">English</span>
                <span class="description">Legal & Security Documentation</span>
            </a>

            <a href="{{ '/da/' | relative_url }}" class="language-option">
                <span class="flag">🇩🇰</span>
                <span class="language-name">Dansk</span>
                <span class="description">Juridisk & Sikkerhedsdokumentation</span>
            </a>
        </div>

        <p class="note">This site will automatically redirect to English in <span id="countdown">5</span> seconds...</p>
    </div>
</div>

<script>
// Auto-redirect to English after 5 seconds
let countdown = 5;
const countdownEl = document.getElementById('countdown');
const timer = setInterval(() => {
    countdown--;
    if (countdownEl) countdownEl.textContent = countdown;
    if (countdown <= 0) {
        clearInterval(timer);
        window.location.href = '{{ "/en/" | relative_url }}';
    }
}, 1000);
</script>

<style>
.language-selector-page {
    min-height: 70vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 2rem;
}

.selector-content {
    text-align: center;
    max-width: 600px;
}

.selector-content h1 {
    font-size: 3rem;
    color: #2c3e50;
    margin-bottom: 1rem;
}

.subtitle {
    font-size: 1.2rem;
    color: #6c757d;
    margin-bottom: 3rem;
}

.language-options {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
    margin-bottom: 3rem;
}

.language-option {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2rem;
    background: white;
    border-radius: 12px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    text-decoration: none;
    transition: all 0.3s ease;
    border: 3px solid transparent;
}

.language-option:hover {
    transform: translateY(-8px);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.15);
    border-color: #667eea;
}

.language-option .flag {
    font-size: 4rem;
    margin-bottom: 1rem;
}

.language-option .language-name {
    font-size: 1.5rem;
    font-weight: 600;
    color: #2c3e50;
    margin-bottom: 0.5rem;
}

.language-option .description {
    font-size: 0.9rem;
    color: #6c757d;
}

.note {
    font-size: 0.9rem;
    color: #6c757d;
    font-style: italic;
}

#countdown {
    font-weight: 600;
    color: #667eea;
}

@media (max-width: 768px) {
    .selector-content h1 {
        font-size: 2rem;
    }

    .language-options {
        grid-template-columns: 1fr;
    }
}
</style>
