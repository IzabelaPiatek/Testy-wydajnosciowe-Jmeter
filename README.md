# Testy wydajnościowe Jmeter

## Opis projektu
Ten projekt zawiera zestaw automatycznych testów API, przeprowadzonych za pomocą **Apache JMeter**. Celem testów jest weryfikacja poprawności działania interfejsu API, wydajności serwera oraz obsługi różnych scenariuszy autoryzacyjnych. Projekt został skonfigurowany tak, aby umożliwić dynamiczne testowanie wydajności w różnych warunkach i generowanie szczegółowych raportów.

## Wymagania
Aby rozpocząć pracę z tym projektem, potrzebujesz:

- **Apache JMeter** w wersji 5.5 lub nowszej.
- **Java Development Kit (JDK)** w wersji 8 lub wyższej(ważne, aby sprawdzić jaka wersja będzie kompatybilna z pobieranym Apache Jmeter).
- Dostęp do środowiska testowego API (np. HTTPBin).
- Opcjonalnie: narzędzia do przeglądania raportów (np. Excel, narzędzia do analizy plików CSV).

## Zawartość
### 1. Testy autoryzacji Basic Auth
- Weryfikacja odpowiedzi serwera dla:
  - **Poprawnych danych uwierzytelniających**.
  - **Nieprawidłowych danych uwierzytelniających**.
  - **Braku autoryzacji**.
- Oczekiwane kody odpowiedzi: `200 OK`, `401 UNAUTHORIZED`.

### 2. Test wydajności serwera (Throughput Test)
- Testowanie maksymalnej przepustowości serwera.
- Dynamiczne sterowanie liczbą wątków (użytkowników) i czasem ramp-up.
- Generowanie raportów z metrykami:
  - **Throughput (przepustowość)**.
  - **Czas odpowiedzi**.
  - **Liczba błędów (Error%)**.

### 3. Test odpowiedzi serwera
- Walidacja kluczowych elementów odpowiedzi:
  - **Response Code:** Weryfikacja kodów HTTP (`200`, `401`).
  - **Response Message:** Analiza komunikatów (`OK`, `UNAUTHORIZED`).
  - **Nagłówki:** Sprawdzenie obecności kluczowych nagłówków.

## Funkcje projektu
- **Testy funkcjonalne:** Automatyczne sprawdzanie, czy API działa zgodnie z oczekiwaniami w różnych scenariuszach.
- **Testy wydajnościowe:** Symulacja ruchu dla wielu użytkowników, weryfikacja limitów serwera.
- **Testy regresyjne:** Wielokrotne testowanie, aby upewnić się, że nowe zmiany nie wprowadzają błędów.
- **Elastyczna konfiguracja:** Możliwość dostosowania liczby wątków, ramp-up time, liczby żądań i scenariuszy testowych.
- **Przejrzyste raporty:** Automatyczne generowanie wyników w formacie czytelnym dla analityków.

## Jak uruchomić testy?
1. Pobierz plik JMeter `.jmx` i otwórz go w Apache JMeter.
2. Wybierz odpowiedni scenariusz testowy w GUI JMeter:
   - Test autoryzacji Basic Auth.
   - Test wydajności serwera.
3. Dostosuj konfigurację w **Thread Group**, w zależności od potrzeb:
   - Liczba wątków (użytkowników).
   - Ramp-up czas (okres przyrostu użytkowników).
   - Liczba iteracji.
4. Kliknij **Start** (zielona strzałka w JMeter).
5. Analizuj wyniki za pomocą listenerów:
   - **View Results Tree** — szczegóły odpowiedzi serwera.
   - **Summary Report** — ogólne statystyki.
   - **Response Time Graph** — wizualizacja czasów odpowiedzi.

## Analiza wyników
- **Throughput (przepustowość):** Ilość żądań przetworzonych przez serwer na sekundę.
- **Czas odpowiedzi:** Minimalny, średni i maksymalny czas odpowiedzi.
- **Error Rate (Błędy):** Procent nieudanych żądań.

## Uwagi końcowe
- W projekcie wykorzystano API **HTTPBin** do celów testowych.
- Wszystkie scenariusze testowe zostały stworzone w celach edukacyjnych i do nauki obsługi Apache JMeter.
- W razie potrzeby można dostosować scenariusze do innych API, zmieniając ustawienia w JMeter (np. URL, dane autoryzacyjne).
