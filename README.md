# WiseGroup — WSS Blueprint, demo strony zapisu

Statyczny prototyp landing page promującego materiał do samodzielnej diagnozy procesu sprzedaży B2B. Projekt pokazuje układ oferty, formularz kwalifikujący zainteresowane osoby oraz ekran podziękowania.

**Status:** demonstracja interfejsu. Formularz sprawdza dane w przeglądarce i zmienia widok; nie zapisuje kontaktów ani nie wysyła wiadomości e-mail. Repozytorium nie zawiera pliku Blueprint.

## Co jest zaimplementowane

- Responsywny układ z opisem materiału, korzyściami, przykładem zastosowania i kolejnymi krokami.
- Formularz z adresem e-mail, wielkością zespołu sprzedaży i zgodą na przetwarzanie danych.
- Prosta walidacja pól i komunikaty błędów.
- Przełączenie strony zapisu na ekran podziękowania bez przeładowania dokumentu.
- Animacje sekcji przy przewijaniu, wykorzystujące `IntersectionObserver`.

## Stos i architektura

HTML, CSS i JavaScript bez frameworka, bundlera ani zależności npm. Cały kod znajduje się w [index.html](index.html): style w `<style>`, treść obu widoków w HTML, a obsługa formularza i animacji w końcowym `<script>`.

Przepływ: formularz → lokalna walidacja → ukrycie `#lp` → pokazanie `#typ`. Nie ma warstwy serwerowej, bazy danych ani konfiguracji środowiska.

Jedyną zewnętrzną zależnością podczas wyświetlania są fonty Poppins z Google Fonts. Przy braku dostępu do tej usługi przeglądarka użyje fontu zastępczego.

## Uruchomienie lokalne

Wymagania: Git, Python 3 i współczesna przeglądarka.

```sh
git clone https://github.com/dzwoniar/wisegroup-demo.git
cd wisegroup-demo
python -m http.server 8000 --bind 127.0.0.1
```

Otwórz [http://127.0.0.1:8000](http://127.0.0.1:8000). Serwer zatrzymasz przez `Ctrl+C`. Nie ma kroku instalacji ani budowania.

## Struktura i miejsca zmian

```text
.
├── index.html   # treść, style, formularz, ekran podziękowania
└── README.md    # dokumentacja projektu
```

Kolory i typografię zmienisz w CSS, treści oferty w sekcjach HTML, a reguły formularza w obsłudze zdarzenia `submit` dla `#leadForm`.

## Granice demo

Przyciski pobrania materiału i rezerwacji sesji na ekranie podziękowania nie mają podłączonych akcji. Odnośnik polityki prywatności jest placeholderem. Treści, przykłady i deklaracje skuteczności stanowią zawartość prototypu, a nie wyniki pomiarów tego repozytorium.

Udostępnienie działającego zapisu wymaga osobnej integracji z systemem do zbierania kontaktów, dostarczenia materiału i podpięcia docelowych odnośników.

## Sprawdzenie po zmianach

W repozytorium nie ma automatycznego zestawu testów. Lokalnie sprawdź układ na wąskim i szerokim ekranie, komunikaty przy brakujących polach oraz widoczność sekcji po przewinięciu. Przepływ podziękowania można sprawdzić na fikcyjnych danych — obecny kod nie wykonuje wysyłki sieciowej.
