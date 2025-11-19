# 🎭 Metadata Moduly

Moduly pro katalogy, vyhledávání a detaily filmů/seriálů.

## 📋 Připravované moduly

- **TMDB** - The Movie Database API
- **ČSFD** - Česko-Slovenská filmová databáze
- **OMDb** - Open Movie Database
- **Kinobox** - České premiéry a hodnocení

## 🔧 Typy metadata modulů

### Katalogové endpointy
- `catalogue_movies` - populární filmy
- `catalogue_series` - populární seriály
- `search_movies` - vyhledávání filmů
- `search_series` - vyhledávání seriálů

### Detailní endpointy
- `movie_detail` - detail filmu
- `series_detail` - detail seriálu
- `series_episodes` - epizody sezóny

## 📝 Požadavky na metadata moduly

Metadata moduly musí obsahovat:
- Alespoň jeden katalogový endpoint
- Správné mapování podle typu (film/seriál)
- Podporu pro `{page}` placeholder
- Volitelně: `{catalogueLanguage}` pro lokalizaci

## 🤝 Přispívání

Chcete přidat nový metadata modul? Sledujte [návod na vytvoření modulu](../docs/creating-modules.md).
