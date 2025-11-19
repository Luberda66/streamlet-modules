# 📖 Návod na vytvoření Streamlet modulu

Tento návod vás provede vytvořením vlastního modulu pro Streamlet aplikaci.

## 🎯 Typy modulů

### 1. Stream Moduly
Poskytují odkazy na video soubory pro přehrávání.

**Požadované endpointy:**
- `stream_search` - vyhledávání souborů
- `link` - získání stream URL

**Mapování dat:**
```json
{
  "id": "unikátní_identifikátor",
  "name": "název_souboru",
  "type": "video",
  "size": "velikost_v_GB_nebo_MB",
  "ratingUp": "počet_pozitivních_hodnocení",
  "link": "url_k_souboru"
}
```

### 2. Metadata Moduly
Poskytují informace o filmech a seriálech.

**Možné endpointy:**
- `catalogue_movies` - populární filmy
- `search_movies` - vyhledávání filmů
- `movie_detail` - detail filmu
- `catalogue_series` - populární seriály
- `search_series` - vyhledávání seriálů
- `series_detail` - detail seriálu
- `series_episodes` - epizody sezóny

## 🔧 Struktura modulu

### Základní metadata
```json
{
  "id": "unikátní-id",
  "media": ["movies", "series"],
  "type": ["stream", "catalogues", "details"],
  "name": "Zobrazovaný název",
  "website": "https://example.com",
  "repository": "https://raw.githubusercontent.com/user/repo/main/module.json",
  "author": "Váš nick",
  "version": "1.0.0",
  "description": "Popis modulu",
  "baseUrl": "https://api.example.com",
  "responseFormat": "json|xml|scraper"
}
```

### API Moduly
```json
{
  "api": [
    {
      "name": "Název endpointu",
      "type": "stream_search",
      "method": "GET",
      "url": "/search?q={title}",
      "response": {
        "itemsKey": "results",
        "mapping": {
          "id": "id",
          "name": "title",
          "size": "filesize"
        }
      }
    }
  ]
}
```

### Scraper Moduly
```json
{
  "scraper": [
    {
      "name": "Název endpointu",
      "type": "stream_search",
      "url": "/search/{title}",
      "mapping": {
        "id": "regex(attribute(a, href), '/file/(\\d+)', 1)",
        "name": "selector(.title)",
        "size": "selector(.filesize)"
      }
    }
  ]
}
```

## 🔍 Selektorové DSL (pro Scraper moduly)

### Základní selektory
- `selector(css_selektor)` - text prvního elementu
- `selectorAll(css_selektor)` - texty všech elementů
- `attribute(css_selektor, atribut)` - hodnota atributu

### Pokročilé funkce
- `regex(baseSelector, pattern, groupIndex)` - regex extrakce
- `regex_replace(baseSelector, pattern, replacement)` - regex nahrazení

### Příklady
```json
{
  "id": "regex(attribute(a, href), '/movie/(\\d+)', 1)",
  "title": "selector(h2.title)",
  "poster": "attribute(img.poster, src)",
  "rating": "regex(selector(.rating), '([0-9.]+)', 1)",
  "genres": "selectorAll(.genre)"
}
```

## 🔐 Autentizace

### API klíč v hlavičce
```json
{
  "headers": {
    "Authorization": "Bearer YOUR_API_KEY"
  },
  "config": {
    "apiKey": {
      "type": "string",
      "label": "{apiKey}",
      "required": true
    }
  }
}
```

### Vícekrokový proces
```json
{
  "auth": {
    "steps": [
      {
        "name": "login",
        "method": "POST",
        "url": "/login",
        "body": {
          "username": "{login}",
          "password": "{password}"
        },
        "response": {
          "tokenPath": "token",
          "storeTokenAs": "authToken"
        }
      }
    ]
  }
}
```

## 🧪 Testování

1. **Validace JSON** - zkontrolujte syntaxi
2. **Test endpointů** - ověřte dostupnost URL
3. **Test selektorů** - otestujte CSS selektory
4. **Test v aplikaci** - importujte modul do Streamlet

## 📝 Best Practices

- ✅ Používejte popisné názvy a ID
- ✅ Přidejte správné hlavičky (User-Agent)
- ✅ Implementujte error handling
- ✅ Podporujte stránkování (`{page}`)
- ✅ Používejte relativní URL pro obrázky
- ✅ Testujte na různých dotazech

## 🚀 Publikování

1. Vytvořte modul podle tohoto návodu
2. Otestujte funkčnost
3. Přidejte do správné kategorie v repository
4. Aktualizujte README.md
5. Vytvořte Pull Request

## 🔗 Užitečné odkazy

- [Oficiální dokumentace](https://streamlet.info/dev.html)
- [Příklady modulů](https://streamlet.info/repo_v3/)
- [CSS Selektory](https://www.w3schools.com/cssref/css_selectors.asp)
- [Regex tester](https://regex101.com/)
