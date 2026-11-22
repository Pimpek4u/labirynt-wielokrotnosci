# Labirynt Tabliczki Mnożenia — Ustalenia Projektowe

Dokument zbiera kluczowe decyzje funkcjonalne, graficzne i techniczne dotyczące gry oraz wbudowanego generatora kart pracy A4.

---

## 1. Mechanika gry i konfiguracja główna

- **Rozmiary planszy (siatki)**: `4×4`, `5×5`, `6×6`, `8×8`, `10×10`, `12×12`.
- **Tryby rozgrywki**:
  - **1 Gracz**: 1 lub 2 wybrane mnożniki (`2–12`), sterowanie kliknięciem/dotykiem, strzałkami lub `W A S D X`.
  - **2 Graczy**: dokładnie 2 mnożniki na wspólnej planszy (`W A S D X` dla Gracza 1, `Strzałki` dla Gracza 2).
- **Zakres liczb na planszy (`Od – Do`)**:
  - Domyślnie: **`1` – `200`**.
  - Polecane szybkie presety: **`1–30`**, **`30–100`**, **`1–200`**.
  - Wszystkie wielokrotności na trasach oraz liczby rozpraszające mieszczą się w zadanym zakresie (z bezpiecznym fallbackiem matematycznym dla bardzo wąskich przedziałów).
- **Oznaczenia START i META**:
  - Etykiety `START ×N` oraz `META ×N` wyświetlane są bezpośrednio przy odpowiednich strzałkach wejścia/wyjścia, zakotwiczone na zewnątrz siatki tak, aby nigdy nie nachodziły na obramowanie planszy.

---

## 2. Generator kart pracy A4 (`Generuj karty pracy A4`)

- **Dostępność**: przycisk widoczny zarówno na ekranie ustawień początkowych, jak i w dolnym pasku narzędzi w trakcie gry (otwarcie podczas gry wstrzymuje licznik czasu).
- **Sposób wydruku**: wbudowany podgląd A4 w aplikacji oraz wydruk / zapis do PDF przez `window.print()` (`@page { size: A4 portrait; margin: 10mm; }`), bez wyskakujących okienek `window.open()`.
- **Domyślny podgląd**: **widok całej strony** dopasowany automatycznie do wysokości i szerokości okna podglądu (z opcją przełączenia na `Powiększenie 100%`).

### Tryby i opcje kart pracy
1. **Typ kart**:
   - **Z liczbami (labirynt)**: wygenerowane unikalne labirynty dla wybranych mnożników i zakresu.
   - **Puste plansze (bez liczb)**: puste kratki do samodzielnego wpisania liczb, z możliwością wyboru rozmiaru siatki, liczby plansz na stronie i układu strzałek (`1` lub `2` trasy).
2. **Liczba plansz na stronie A4**:
   - **1 plansza**: duża plansza na całą stronę.
   - **2 plansze**: dwa różne losowe labirynty ułożone pionowo z linią cięcia.
   - **4 plansze**: cztery różne losowe labirynty w układzie `2×2` z liniami cięcia.
   - **Wiele małych (`6 małych` w układzie `2×3` lub `8 małych` w układzie `2×4`)**: bez dodatkowych nagłówków, napisów i instrukcji, z bardzo cienką linią podziału (`0.5px`).
3. **Wypełnienie przestrzeni („Wypełnij jak najszerzej”)**:
   - Przełącznik powiększający siatki plansz tak, aby maksymalnie wykorzystać dostępną szerokość i wysokość strony A4.
4. **Dyskretne gwiazdki trudności**:
   - Opcja włączania małych, subtelnych gwiazdek określających poziom trudności na podstawie górnej granicy zakresu liczb:
     - do `30` → **1 gwiazdka** (`★`)
     - do `50` → **2 gwiazdki** (`★★`)
     - do `100` → **3 gwiazdki** (`★★★`)
     - do `200` → **4 gwiazdki** (`★★★★`)
     - do `999` → **5 gwiazdek** (`★★★★★`)
5. **Pole na imię, nazwisko i datę**:
   - Domyślnie **wyłączone** (możliwe do włączenia w układach z nagłówkiem: `1`, `2`, `4` plansze).
6. **Klucz odpowiedzi (2. strona A4)**:
   - Domyślnie **wyłączony**.
   - Po włączeniu udostępnia dwa tryby:
     - **Klucz graficzny**: druga strona A4 z identycznym układem plansz i zaznaczonymi trasami rozwiązań.
     - **Klucz liczbowy**: zwięzła lista wszystkich wielokrotności używanych liczb w zadanym zakresie (np. `7, 14, 21, 28...`) oraz wspólnych wielokrotności dla tras krzyżujących się.

---

## 3. Typografia, wydruk i oszczędność tuszu

- **Czcionka**: **Nunito** (pełna obsługa polskich znaków diakrytycznych `ą, ć, ę, ł, ń, ó, ś, ź, ż`).
- **Oszczędny wydruk**: liczby w komórkach kart pracy renderowane są lżejszą wagą (`500`) i w odcieniu grafitowym (`#475569`) zamiast ciężkiej czerni, z delikatnymi liniami siatki (`0.75px` wewnątrz, `1.5px` na zewnątrz).
