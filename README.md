# Zadanie 18 - Git Cherry-pick i Stash

## Cel zadania

Praktyczne wykorzystanie zaawansowanych operacji Git:
- git cherry-pick
- git stash
- git stash pop

## 1. Git Cherry-pick

Utworzono trzy galezie:
- main - bazowa wersja projektu
- feature-a - oryginalna implementacja funkcji
- feature-b - galaz docelowa dla cherry-pick

Na galezi feature-a utworzono plik calculations.py
z funkcja calculate_average().

Oryginalny commit:
79dc7bd - feat: dodanie funkcji obliczania sredniej

Nastepnie wykonano:

git switch feature-b
git cherry-pick 79dc7bd

Powstal nowy commit:
a03e124 - feat: dodanie funkcji obliczania sredniej

Wynik uruchomienia calculations.py:
Srednia: 30.0

Wniosek:
Cherry-pick pozwala przeniesc wybrany commit na inna
galaz bez laczenia calej historii galezi.

## 2. Git Stash

Na galezi feature-b zmodyfikowano plik main.py,
dodajac dwie instrukcje print().

Zmiany nie zostaly od razu zapisane w commicie.

Wykonano:

git stash push -m "WIP: niedokonczona funkcjonalnosc"
git status
git stash list

Po wykonaniu git stash:
- katalog roboczy byl czysty
- zmiany znajdowaly sie w schowku
- main.py wrocil do poprzedniej wersji

Nastepnie wykonano:

git stash pop
git status
git stash list
git diff

Rezultat:
- odzyskano obie instrukcje print()
- main.py ponownie byl oznaczony jako zmodyfikowany
- schowek Git zostal oprozniony

Przywrocone zmiany zapisano w commicie:
daded59 - feat: zapisanie zmian przywroconych ze stash

## 3. Wnioski

git cherry-pick:
Pozwala skopiowac zmiany z wybranego commita
na inna galaz bez wykonywania merge.

git stash:
Pozwala tymczasowo odlozyc niezapisane zmiany.

git stash pop:
Przywraca odlozone zmiany i po udanej operacji
usuwa odpowiedni wpis ze schowka.

## 4. Uruchomienie projektu

python main.py
python calculations.py

## 5. Weryfikacja historii

git log --oneline --all --graph --decorate
