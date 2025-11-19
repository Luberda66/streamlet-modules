# 📺 Stream Moduly

Moduly pro vyhledávání a přehrávání video obsahu.

## 📋 Dostupné moduly

### Přehraj.to
- **Typ**: Scraper modul
- **Země**: Česká republika 🇨🇿
- **Popis**: České filmy a seriály s českými titulky/dabingem
- **Autentizace**: Není potřeba
- **GitHub URL**: `https://raw.githubusercontent.com/[username]/streamlet-modules/main/stream/prehraj-to.json`

## 🔧 Instalace do Streamlet

1. Otevřete Streamlet aplikaci
2. Přejděte do nastavení modulů
3. Přidejte nový modul pomocí URL
4. Vložte GitHub raw URL modulu
5. Uložte a aktivujte modul

## 📝 Požadavky na stream moduly

Stream moduly musí obsahovat:
- `stream_search` endpoint pro vyhledávání
- `link` endpoint pro získání stream URL
- Správné mapování: `id`, `name`, `type`, `size`
- Volitelně: `ratingUp`, `ratingDown`

## 🤝 Přispívání

Chcete přidat nový stream modul? Sledujte [návod na vytvoření modulu](../docs/creating-modules.md).
