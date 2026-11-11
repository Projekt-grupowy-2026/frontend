# Frontend – rola w projekcie

## 1. Kontekst

Projekt to aplikacja logistyczna wspomagająca planowanie i realizację transportu. System monitoruje lokalizację pojazdów i na bieżąco aktualizuje przewidywany czas dotarcia (ETA) do kolejnych punktów trasy.

System składa się z trzech elementów:

| Element | Repozytorium | Użytkownicy |
|---|---|---|
| Aplikacja webowa | **frontend** (to repo) | dyspozytor, klient |
| Back-end / serwer | [backend](https://github.com/Projekt-grupowy-2026/backend) | – |
| Aplikacja mobilna | [mobile-app](https://github.com/Projekt-grupowy-2026/mobile-app) | kierowca |

Frontend nie przechowuje danych ani nie liczy ETA – wszystkie dane pobiera i zapisuje przez API backendu.

## 2. Użytkownicy aplikacji webowej

### Dyspozytor

- Tworzy i modyfikuje plany tras.
- Przydziela trasy kierowcom.
- Monitoruje lokalizację pojazdów na mapie.
- Sprawdza postęp realizacji transportu i przewidywane godziny przyjazdu.

### Klient / odbiorca dostawy

- Sprawdza status swojej dostawy.
- Widzi przewidywany czas przyjazdu pojazdu.
- Otrzymuje informację o opóźnieniach.
- Widzi **wyłącznie** dane dotyczące własnego przejazdu.

## 3. Funkcjonalności

### 3.1. Planowanie transportu (dyspozytor)

- Tworzenie planu trasy jako uporządkowanej sekwencji **odcinków** i **postojów**.
- Dodawanie, usuwanie i edycja odcinków:
  - punkt początkowy i końcowy,
  - przebieg trasy na mapie,
  - dystans [km],
  - planowany czas przejazdu.
- Dodawanie, usuwanie i edycja postojów:
  - lokalizacja,
  - planowana godzina rozpoczęcia i czas trwania,
  - rodzaj: rozładunek, załadunek, przerwa kierowcy, przystanek.
- Przydzielanie gotowego planu kierowcy.

### 3.2. Monitorowanie w czasie rzeczywistym (dyspozytor)

- Mapa pojazdów z aktualną pozycją.
- Lista przejazdów ze statusem i aktualnym etapem.
- Przewidywane godziny przyjazdu (ETA) do kolejnych punktów i sygnalizacja opóźnień.
- Podgląd pozycji konkretnego kierowcy przez uprawnionego użytkownika.

### 3.3. Panel klienta

- Podgląd statusu własnego przejazdu / dostawy.
- Przewidywana godzina przyjazdu.
- Informacja o opóźnieniu.

## 4. Scenariusze użycia

### A. Transport ciężarowy

Dyspozytor planuje trasę: Port (A) → Magazyn 1 (B, postój 30 min, rozładunek) → Magazyn 2 (C, postój 20 min, rozładunek) → Port (A). Pracownicy magazynów (klienci) sprawdzają w aplikacji webowej przewidywany czas dotarcia dostawy.

### B. Transport autobusowy

Dyspozytor tworzy kurs z przystankami i godzinami odjazdów, a następnie śledzi jego realizację. Przy opóźnieniu widzi zaktualizowane ETA dla kolejnych przystanków.

## 5. Poza zakresem tego repozytorium

- Logika biznesowa, przechowywanie danych, obliczanie ETA → `backend`.
- Interfejs kierowcy i pobieranie lokalizacji z telefonu → `mobile-app`.

## 6. Do ustalenia

- Stack technologiczny (framework, biblioteka map).
- Sposób odbierania aktualizacji na żywo (odpytywanie / WebSocket).
- Układ i wygląd ekranów (makiety UI).
