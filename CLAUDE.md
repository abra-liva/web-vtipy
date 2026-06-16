# Generátor vtipů – Claude.md

Víkam do Claude Code. Zde jsou klíčové informace o tomto projektu.

## 📋 Přehled projektu

**Generátor vtipů** je jednoduchá GitHub Pages aplikace, která:
- Vezme od uživatele **téma** a svůj vlastní **Anthropic API klíč**
- Pošle požadavek na Claude API s promptem na vygenerování vtipu
- Vrátí vygenerovaný vtip přímo do prohlížeče

Aplikace běží zcela na straně klienta – bez serveru.

## 🎯 Cíl

- Demonstrovat přímou komunikaci s Anthropic API z prohlížeče
- Poskytnout jednoduché, přátelské rozhraní pro generování vtipů v češtině
- Ukázat bezpečný (bez ukládání) přístup k API klíčům od uživatelů

## 🗂️ Struktura

```
web-vtipy/
├── index.html          # Jediný soubor – kompletní aplikace (HTML + CSS + JS)
└── .claude/
    └── settings.local.json
```

## 🔧 Jak to funguje

1. **index.html** – samoobsažující se soubor s:
   - **HTML formulář**: pole pro téma a API klíč
   - **CSS**: tmavý design s animacemi (Space Grotesk, Lora fonty)
   - **JavaScript**: `generateJoke()` voá Anthropic API endpoint

2. **API volání**:
   - Endpoint: `https://api.anthropic.com/v1/messages`
   - Model: `claude-sonnet-4-6`
   - Max tokens: 1000
   - Prompt požaduje krátký, vtipný vtip v češtině
   - API klíč se posílá v headeru `x-api-key`

3. **UX**:
   - Loading animace (tři páskující se tečky)
   - Validace API klíče (kontroluje `sk-ant-` prefix)
   - Chybové zprávy
   - Enter key support v poli tématu

## ⚠️ Bezpečnost

- **API klíč se NEUKLÁDÁ** – zůstává v paměti prohlížeče uživatele
- Aplikace se spouští na `console.anthropic.com` odkazu
- Toto je bezpečné pro demo/personal use, ale pro produkci byste měli API volání proxy přes backend
- Nedělat `git push` souboru s "testovacím" API klíčem (pokud byste ho vkládali do kódu)

## 🚀 Jak spustit

1. Otevřete `index.html` v prohlížeči (nebo ho pushnete na GitHub Pages)
2. Zadejte téma vtipu (např. "programátoři", "kočky", "pondělky")
3. Vložte svůj Anthropic API klíč (`sk-ant-...`)
4. Klikněte "Vygenerovat vtip ✨"

## 🔄 Úpravy a vývoj

Pokud chcete upravit projekt:

- **Změnit design**: Editujte CSS v `<style>` bloku v `index.html`
- **Změnit prompt**: Upravte zprávu v `messages[0].content` (řetězec s tématem)
- **Změnit model**: Upravte `model: 'claude-sonnet-4-6'` na jiný Claude model
- **Přidat funkce**: Přidejte nové `<input>` pole a zpracujte je v `generateJoke()`

## 📝 Psaní/úpravy kódu

- Projekt je jeden soubor – editujte ho přímo
- Testujte v prohlížeči (F12 DevTools pro chyby)
- Při pushu na GitHub se automaticky nasadí na Pages

## 🤝 Spolupráce

Zde jsou pokyny pro práci s Claude Code:

- **Rychlé otázky**: Ptejte se na část kódu nebo jak něco funguje
- **Přidání funkcí**: Řekněte, co chcete a já to implementuji
- **Ladění**: Sdělte chybu a já ji najdu/opravím
- **Code review**: Zeptejte se na `/code-review` nebo `/simplify`

---

**Poslední aktualizace**: 2026-06-16  
**Jazyk**: Čeština  
**Licenze**: (doplnit dle vašeho přání)
