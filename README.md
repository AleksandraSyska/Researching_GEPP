# Complex Linear System Solver (GEPP)

## 📌 Opis projektu
Ten projekt implementuje numeryczne rozwiązanie układów równań liniowych o współczynnikach zespolonych w środowisku MATLAB. Program rozwiązuje układy postaci:
$$Cz = c$$
gdzie $C$ jest macierzą zespoloną $n \times n$, a $z$ i $c$ są wektorami zespolonymi. Algorytm opiera się na **eliminacji Gaussa z częściowym wyborem elementu głównego (GEPP)**.

## 🧮 Model matematyczny
Aby rozwiązać układ zespolony, projekt przekształca go w równoważny układ rzeczywisty o wymiarze $2n \times 2n$. Definiujemy składowe jako:
* $C = A + iB$
* $z = x + iy$
* $c = a + ib$

Równanie zespolone przyjmuje postać rzeczywistej macierzy blokowej:
$$\begin{bmatrix} A & -B \\ B & A \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} a \\ b \end{bmatrix}$$
Takie podejście pozwala na zastosowanie standardowych algorytmów eliminacji przy zachowaniu pełnej informacji o części rzeczywistej i urojonej.

## 🚀 Funkcje algorytmu
* **GEPP (Gaussian Elimination with Partial Pivoting)**: Wybór elementu o największej wartości bezwzględnej w kolumnie minimalizuje błędy zaokrągleń.
* **Podstawianie wsteczne**: Wyznaczanie rozwiązania po sprowadzeniu macierzy do postaci górnotrójkątnej.
* **Detekcja osobliwości**: Program monitoruje wartości na przekątnej i ostrzega w przypadku macierzy osobliwych lub bliskich osobliwości.
* **Analiza błędów**: Porównanie wyników z wbudowaną funkcją MATLAB-a (`\`).

## 📂 Struktura plików
* `solve_block_system.m` – Główna funkcja rozwiązująca układ.
* `create_equations.m` – Funkcja budująca rzeczywisty układ blokowy z danych zespolonych.
* `skrypt_testujacy.m` – Środowisko testowe sprawdzające wydajność i dokładność dla różnych typów macierzy (losowe, rzadkie, źle uwarunkowane)
