# Szablon strony restauracji

Jednostronicowy szablon strony restauracji. Treści można łatwo dostosować w konfiguracji JavaScript.

## Szybki start

1. Otwórz plik `kurczak-z-rozna.html` w edytorze tekstu.
2. Znajdź obiekt konfiguracyjny `RESTAURANT` na początku sekcji `<script>`.
3. Zmień wartości, aby dopasować stronę do swojej restauracji.
4. Otwórz plik HTML w przeglądarce, aby sprawdzić podgląd.

## Personalizacja

### 1. Dane kontaktowe

Zmień poniższe pola w konfiguracji `RESTAURANT`:

```javascript
name: 'Nazwa restauracji',
telephone: {
  display: '123 456 789',    // Numer wyświetlany na stronie
  href: '+48123456789'       // Numer używany w odnośnikach tel:
},
address: {
  street: 'Nazwa ulicy 1',
  postalCode: '00-000',
  locality: 'Nazwa miasta',
  country: 'PL'
},
mapsUrl: 'https://maps.google.com/...',
```

### 2. Godziny otwarcia

Edytuj tablicę `openingHours`:

```javascript
openingHours: [
  { day: 1, label: 'Poniedziałek', schemaDay: 'Monday', open: '09:00', close: '18:00' },
  { day: 2, label: 'Wtorek', schemaDay: 'Tuesday', open: '09:00', close: '18:00' },
  // ... pozostałe dni tygodnia
  { day: 0, label: 'Niedziela', schemaDay: 'Sunday', open: null, close: null }  // Nieczynne
],
```

- `day`: 0 = niedziela, 1 = poniedziałek, ..., 6 = sobota.
- `open` / `close`: godzina w formacie 24-godzinnym `HH:MM` albo `null`, jeśli lokal jest nieczynny.
- `label`: nazwa dnia wyświetlana w tabeli.
- `schemaDay`: angielska nazwa dnia używana w danych strukturalnych Schema.org.

### 3. Menu

Zmień tablicę `menu`:

```javascript
menu: [
  {
    title: '🍕 Pizze',             // Nazwa kategorii
    items: [
      { name: 'Margherita', description: 'Pomidor, mozzarella, bazylia', price: '25 zł', featured: true },
      { name: 'Pepperoni', price: '28 zł' },
      // Kolejne pozycje...
    ]
  },
  // Kolejne kategorie...
],
```

- `featured: true` dodaje do dania etykietę „HIT”.
- `description` jest opcjonalny — można go pominąć.

### 4. Opinie

Edytuj tablicę `reviews`:

```javascript
reviews: [
  {
    quote: 'Treść opinii...',
    tags: ['Jedzenie 5/5', 'Obsługa 5/5'],  // Etykiety opinii
    author: 'Jan K.',
    initials: 'J',                         // Litera w awatarze
    source: 'Źródło opinii · czas temu'
  },
  // Kolejne opinie...
],
```

Zmień również podsumowanie ocen:

```javascript
rating: 4.8,
reviewCount: 42,
```

### 5. Kroki zamawiania

Dostosuj sekcję „Jak zamówić” w tablicy `orderSteps`:

```javascript
orderSteps: [
  { icon: '📞', title: 'Zadzwoń', description: '123 456 789 i złóż zamówienie.' },
  { icon: '🚗', title: 'Przyjedź', description: 'Znajdziesz nas przy ulicy Przykładowej 1.' },
  { icon: '🍽️', title: 'Smacznego', description: 'Odbierz zamówienie i smacznego!' }
],
```

### 6. Kolory motywu

Kolory są zdefiniowane jako zmienne CSS w bloku `:root`. Zmień ich wartości, aby dostosować motyw:

```css
:root {
  --bg: #fff8ee;       /* Tło strony */
  --card: #fff;        /* Tło kart */
  --ink: #2a1a10;      /* Kolor tekstu */
  --accent: #c2410c;   /* Kolor akcentu, np. przycisków i odnośników */
  --accent-d: #9a3412; /* Ciemniejszy wariant akcentu, np. po najechaniu */
  --soft: #ffedd5;     /* Jasne tła sekcji */
  --line: #f0d9bd;     /* Obramowania i separatory */
  /* ...pozostałe zmienne */
}
```

### 7. SEO i metadane

Zmień poniższe pola, aby dostosować tytuł, opis i podgląd strony w mediach społecznościowych:

```javascript
pageTitle: 'Nazwa restauracji | Miasto | Opis',
description: 'Opis strony widoczny w wynikach wyszukiwania...',
ogImage: 'https://example.com/obraz.jpg',  // Pełny, publicznie dostępny adres obrazu
```

Zaktualizuj także statyczne znaczniki `<meta>` w sekcji `<head>`. Roboty indeksujące i komunikatory mogą nie uruchamiać JavaScriptu.

## Informacje techniczne

- Strona jest responsywna i dostosowuje się do telefonów oraz komputerów.
- Treści strony są generowane na podstawie konfiguracji `RESTAURANT`.
- Status „otwarte” / „zamknięte” jest obliczany automatycznie na podstawie bieżącej godziny i strefy czasowej.
- Dane strukturalne JSON-LD (Schema.org/Restaurant) są generowane z konfiguracji.
- Motyw można zmieniać za pomocą zmiennych CSS.
- Tryb ciemny obsługuje ustawienie systemowe `prefers-color-scheme` oraz atrybut `data-theme="dark"`.

## Obsługiwane przeglądarki

Szablon działa w aktualnych przeglądarkach. Do wyświetlania dynamicznych treści wymagany jest włączony JavaScript.
