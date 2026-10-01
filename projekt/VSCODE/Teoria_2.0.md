# Weekend 1 — Start + fundamenty Pythona

Materiał teoretyczno-praktyczny dla uczestników kursu **AI Python Engineer**.

Ten plik prowadzi krok po kroku przez pierwszy blok kursu. Teoria jest przeplatana zadaniami, a rozwiązania znajdują się bezpośrednio pod zadaniami w rozwijanych sekcjach.

> Najważniejszy cel tego bloku: uruchomić własny kod, zrozumieć podstawowy błąd i zrobić pierwszy mały program samodzielnie.

---

## Jak pracować z tym materiałem?

1. Czytaj krótki fragment teorii.
2. Przepisuj przykłady samodzielnie, nie tylko kopiuj.
3. Uruchamiaj kod po każdej małej zmianie.
4. Przy zadaniu najpierw spróbuj rozwiązać je samodzielnie.
5. Rozwiń rozwiązanie dopiero wtedy, gdy utkniesz albo chcesz porównać swoje podejście.
6. Jeżeli pojawi się błąd, nie traktuj go jako porażki. Błąd jest informacją diagnostyczną.

---

## Tematy bloku

W tym bloku przejdziesz przez następujące tematy:

- mapa kursu i rola Pythona w projekcie,
- instalacja i sprawdzenie środowiska,
- podstawy Gita w projekcie,
- terminal i praca w katalogu projektu,
- pierwszy plik `.py`,
- środowisko wirtualne `.venv`,
- podstawy `uv` oraz klasycznego `venv`,
- czytanie błędów i tracebacków,
- bezpieczna praca z AI,
- zmienne, typy danych i operatory,
- instrukcje warunkowe `if`, `elif`, `else`,
- listy i pętle `for`,
- pętla `while`,
- proste funkcje,
- mini-projekt: prosty analizator zamówień.

---

# 1. Po co zaczynamy od Pythona?

Python jest językiem programowania, którego będziemy używać do budowania logiki aplikacji. W kolejnych blokach będzie potrzebny do pracy z backendem, API, bazami danych, testami i elementami AI.

Na tym etapie nie chodzi o pisanie idealnego kodu. Chodzi o opanowanie podstawowego rytmu pracy:

```text
piszę mały fragment kodu → uruchamiam → czytam wynik albo błąd → poprawiam → uruchamiam ponownie
```

To jest normalny sposób pracy programisty. Kod bardzo często nie działa za pierwszym razem.

---

## Zadanie 1 — Mój cel na pierwszy blok

Napisz w pliku `notes/start.md` trzy krótkie odpowiedzi:

1. Co chcę umieć po tym bloku?
2. Co najbardziej mnie stresuje w pracy z kodem?
3. Jak sprawdzę, że zrobiłem/zrobiłam postęp?

<details>
<summary>Rozwiązanie przykładowe</summary>

```markdown
# Mój cel na pierwszy blok

1. Chcę umieć uruchomić prosty plik Pythona z terminala.
2. Najbardziej stresuje mnie to, że nie będę rozumieć błędów.
3. Sprawdzę postęp po tym, czy samodzielnie uruchomię program i poprawię przynajmniej jeden błąd.
```

To zadanie nie ma jednej poprawnej odpowiedzi. Ważne, żeby odpowiedzi były konkretne.

</details>

---

# 2. Instalacja i sprawdzenie środowiska

Do pracy potrzebujesz kilku elementów:

- **Python** — interpreter, czyli program uruchamiający kod Pythona,
- **VS Code** — edytor kodu,
- **terminal** — miejsce wpisywania komend,
- **Git** — narzędzie do zapisywania historii zmian w projekcie,
- **folder projektu** — jedno miejsce, w którym trzymasz pliki związane z zadaniem,
- **środowisko wirtualne `.venv`** — osobne miejsce na biblioteki dla konkretnego projektu.

W praktyce wygląda to tak:

```text
folder projektu
├── pliki .py
├── pliki .md
├── .venv
├── .git
└── .gitignore
```

## Sprawdzenie Pythona

W terminalu sprawdź wersję Pythona.

Na Windows często działa:

```powershell
py --version
```

Czasem działa również:

```powershell
python --version
```

Na macOS/Linux często działa:

```bash
python3 --version
```

Poprawny wynik wygląda podobnie do:

```text
Python 3.12.5
```

Nie musi być dokładnie taka sama końcówka wersji. Ważne, żeby był to Python 3.x, najlepiej 3.12.

## Sprawdzenie VS Code

W terminalu możesz sprawdzić, czy działa komenda:

```bash
code --version
```

Jeżeli nie działa, nadal możesz otworzyć VS Code ręcznie z menu systemu. Komenda `code .` jest wygodna, ale nie jest obowiązkowa na starcie.

## Sprawdzenie Gita

Git pozwala zapisywać historię zmian w projekcie. Dzięki temu można wrócić do poprzedniej wersji kodu, sprawdzić, co się zmieniło, i pracować z repozytorium.

Sprawdź wersję Gita:

```bash
git --version
```

Poprawny wynik wygląda podobnie do:

```text
git version 2.45.0
```

Jeżeli Git nie jest skonfigurowany, ustaw podstawowe dane użytkownika:

```bash
git config --global user.name "Imię Nazwisko"
git config --global user.email "twoj-email@example.com"
```

Te dane będą podpisywać Twoje commity. Na potrzeby kursu wystarczy podstawowa konfiguracja.

---

## Zadanie 2 — Sprawdzenie narzędzi

W terminalu sprawdź:

1. wersję Pythona,
2. wersję Gita,
3. czy działa komenda `code --version`.

W pliku `notes/environment_check.md` zapisz, które komendy zadziałały na Twoim komputerze.

<details>
<summary>Rozwiązanie przykładowe</summary>

Przykładowa zawartość pliku `notes/environment_check.md`:

````markdown
# Sprawdzenie środowiska

## Python

Na moim komputerze działa komenda:

```bash
py --version
```

Wynik:

```text
Python 3.12.5
```

## Git

Działa komenda:

```bash
git --version
```

Wynik:

```text
git version 2.45.0
```

## VS Code

Komenda `code --version` działa / nie działa.

Jeżeli nie działa, otwieram VS Code ręcznie.
````

Jeżeli u Ciebie działa `python3 --version` zamiast `py --version`, zapisz właśnie tę komendę. Celem jest rozpoznanie własnego środowiska, a nie używanie identycznych komend na każdym systemie.

</details>

---

# 3. Folder projektu i podstawy Gita

Projekt powinien mieć własny folder. Nie warto pracować w folderze `Downloads`, na pulpicie pełnym przypadkowych plików albo w katalogu, którego później nie znajdziesz.

Utwórz folder projektu:

```bash
mkdir ai-python-weekend-01
cd ai-python-weekend-01
```

Jeżeli działa u Ciebie komenda `code`, otwórz folder w VS Code:

```bash
code .
```

## Podstawowe komendy terminala

| Komenda | Windows / macOS / Linux | Co robi? |
|---|---|---|
| `pwd` | głównie macOS/Linux/Git Bash | pokazuje aktualny katalog |
| `cd nazwa_folderu` | wszystkie systemy | wchodzi do folderu |
| `cd ..` | wszystkie systemy | wraca katalog wyżej |
| `mkdir nazwa_folderu` | wszystkie systemy | tworzy folder |
| `ls` | macOS/Linux/Git Bash | pokazuje pliki i foldery |
| `dir` | Windows CMD/PowerShell | pokazuje pliki i foldery |

## Czym jest repozytorium Git?

Repozytorium Git to folder, w którym Git śledzi historię zmian. Repozytorium lokalne działa na Twoim komputerze.

Aby rozpocząć śledzenie zmian w folderze projektu, użyj:

```bash
git init
```

Po tej komendzie w projekcie powstaje ukryty folder `.git`. Nie trzeba go edytować ręcznie.

## Podstawowy cykl pracy z Gitem

Najprostszy cykl wygląda tak:

```text
zmieniam pliki → sprawdzam status → dodaję pliki → tworzę commit
```

Komendy:

```bash
git status
git add nazwa_pliku
git commit -m "Krótki opis zmiany"
```

Można dodać wszystkie zmienione pliki:

```bash
git add .
```

Na początku kursu wystarczy znać ten minimalny zestaw:

```bash
git init
git status
git add .
git commit -m "Initial commit"
git log --oneline
```

## Czego nie commitować?

Nie wszystko powinno trafić do repozytorium. Nie commitujemy przede wszystkim:

- folderu `.venv`,
- plików `.env`,
- haseł,
- tokenów API,
- prywatnych danych,
- folderów cache, np. `__pycache__`.

Do ignorowania takich plików służy `.gitignore`.

Przykładowy plik `.gitignore`:

```gitignore
.venv/
__pycache__/
*.pyc
.env
.DS_Store
```

---

## Zadanie 3 — Utworzenie projektu i repozytorium

Wykonaj następujące kroki:

1. Utwórz folder `ai-python-weekend-01`.
2. Wejdź do folderu.
3. Otwórz go w VS Code.
4. Utwórz plik `.gitignore`.
5. Wpisz do niego reguły ignorowania `.venv`, `__pycache__`, `.env`.
6. Zainicjalizuj repozytorium Git.
7. Sprawdź status repozytorium.

<details>
<summary>Rozwiązanie</summary>

Komendy:

```bash
mkdir ai-python-weekend-01
cd ai-python-weekend-01
code .
```

Plik `.gitignore`:

```gitignore
.venv/
__pycache__/
*.pyc
.env
.DS_Store
```

Inicjalizacja repozytorium:

```bash
git init
git status
```

Po `git status` powinien pojawić się komunikat, że plik `.gitignore` jest nowy i nieśledzony, np. `Untracked files`.

</details>

---

## Zadanie 4 — Pierwszy commit

Dodaj `.gitignore` do historii projektu i utwórz pierwszy commit.

<details>
<summary>Rozwiązanie</summary>

```bash
git add .gitignore
git commit -m "Add gitignore"
git log --oneline
```

`git log --oneline` powinien pokazać krótki identyfikator commita i jego opis, np.:

```text
a1b2c3d Add gitignore
```

Jeżeli Git prosi o konfigurację `user.name` i `user.email`, ustaw je:

```bash
git config --global user.name "Imię Nazwisko"
git config --global user.email "twoj-email@example.com"
```

Potem ponów commit.

</details>

---

# 4. Pierwszy plik `.py`

Pliki z kodem Pythona mają rozszerzenie `.py`, np.:

```text
hello.py
orders.py
main.py
```

Na początku trzymaj się prostych nazw:

- małe litery,
- słowa oddzielone podkreślnikiem,
- bez spacji,
- bez polskich znaków,
- bez zaczynania nazwy od cyfry.

Dobre nazwy:

```text
hello.py
order_report.py
calculate_discount.py
```

Złe nazwy:

```text
1_plik.py
mój plik.py
Raport Zamówień.py
plik-testowy!!.py
```

W pliku `hello.py` wpisz:

```python
print("Hello, Python!")
```

Uruchomienie pliku:

```bash
python hello.py
```

Na części komputerów będzie potrzebne:

```bash
py hello.py
```

albo:

```bash
python3 hello.py
```

To zależy od systemu i konfiguracji.

---

## Zadanie 5 — Pierwszy program

Utwórz plik `hello.py`, który wypisuje trzy linie:

1. Twoje imię,
2. nazwę kursu,
3. zdanie: `Mój pierwszy plik Python działa.`

Następnie uruchom plik z terminala.

<details>
<summary>Rozwiązanie</summary>

Plik `hello.py`:

```python
print("Ania")
print("AI Python Engineer")
print("Mój pierwszy plik Python działa.")
```

Uruchomienie:

```bash
python hello.py
```

Jeżeli `python` nie działa, spróbuj:

```bash
py hello.py
```

albo:

```bash
python3 hello.py
```

</details>

---

## Zadanie 6 — Commit po pierwszym programie

Dodaj plik `hello.py` do repozytorium i utwórz commit z opisem `Add first Python file`.

<details>
<summary>Rozwiązanie</summary>

```bash
git status
git add hello.py
git commit -m "Add first Python file"
git log --oneline
```

Warto przed commitem zawsze użyć `git status`, żeby świadomie zobaczyć, co zostanie zapisane w historii.

</details>

---

# 5. Środowisko wirtualne `.venv`

Środowisko wirtualne to osobna przestrzeń dla bibliotek danego projektu. Dzięki temu każdy projekt może mieć własny zestaw zależności.

Prosta analogia:

```text
projekt A → własna szuflada z narzędziami
projekt B → własna szuflada z narzędziami
```

Nie wrzucamy wszystkich bibliotek globalnie do jednego miejsca, bo z czasem prowadzi to do bałaganu.

## Wariant z `uv`

`uv` to nowoczesne narzędzie do pracy ze środowiskami i zależnościami Pythona.

Podstawowe komendy:

```bash
uv init
uv venv
```

Aktywacja środowiska na Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Aktywacja środowiska na macOS/Linux:

```bash
source .venv/bin/activate
```

## Wariant z klasycznym `venv`

Jeżeli nie używasz `uv`, możesz utworzyć środowisko klasycznie.

Windows:

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Po aktywacji środowiska w terminalu często pojawia się prefiks:

```text
(.venv)
```

To znak, że pracujesz wewnątrz środowiska projektu.

Dezaktywacja środowiska:

```bash
deactivate
```

---

## Zadanie 7 — Utworzenie środowiska wirtualnego

Utwórz środowisko `.venv` w folderze projektu. Możesz użyć `uv` albo klasycznego `venv`.

Następnie:

1. aktywuj środowisko,
2. sprawdź wersję Pythona,
3. dezaktywuj środowisko,
4. aktywuj je ponownie.

<details>
<summary>Rozwiązanie — wariant z `uv`</summary>

```bash
uv init
uv venv
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
python --version
deactivate
.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
source .venv/bin/activate
python --version
deactivate
source .venv/bin/activate
```

</details>

<details>
<summary>Rozwiązanie — wariant z klasycznym `venv`</summary>

Windows:

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
python --version
deactivate
.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
python --version
deactivate
source .venv/bin/activate
```

</details>

---

## Zadanie 8 — Sprawdzenie, czy `.venv` nie trafi do commita

Sprawdź, czy Git nie chce dodać folderu `.venv` do repozytorium.

<details>
<summary>Rozwiązanie</summary>

Najpierw sprawdź status:

```bash
git status
```

Jeżeli w `.gitignore` jest wpis:

```gitignore
.venv/
```

Git nie powinien pokazywać folderu `.venv` jako pliku do dodania.

Jeżeli `.venv` pojawia się w statusie, sprawdź:

1. czy plik nazywa się dokładnie `.gitignore`,
2. czy wpis `.venv/` jest zapisany poprawnie,
3. czy `.gitignore` znajduje się w głównym folderze projektu.

Po poprawce możesz dodać zmiany:

```bash
git add .gitignore
git commit -m "Update gitignore for virtual environment"
```

</details>

---

# 6. Jak czytać błędy?

Błędy w Pythonie są normalne. Ważne jest nie to, żeby ich nigdy nie mieć, ale żeby umieć je czytać.

Python pokazuje błąd w formie tracebacka. Traceback mówi:

- w którym pliku wystąpił problem,
- w której linii,
- jaki jest typ błędu,
- jaki jest komunikat błędu.

Najprostszy schemat:

```text
1. Sprawdź ostatnią linię błędu.
2. Odczytaj typ błędu.
3. Odczytaj komunikat.
4. Znajdź numer linii w swoim pliku.
5. Popraw jedną małą rzecz.
6. Uruchom program ponownie.
```

## Przykład: `NameError`

Kod:

```python
user_name = "Ania"
print(username)
```

Problem: utworzono zmienną `user_name`, ale później użyto `username`. Dla Pythona to dwie różne nazwy.

## Przykład: `SyntaxError`

Kod:

```python
print("Hello)
```

Problem: brakuje zamykającego cudzysłowu.

## Przykład: `IndentationError`

Kod:

```python
if True:
print("To powinno być wcięte")
```

Problem: po `if` kod w środku bloku powinien mieć wcięcie.

## Przykład: `ZeroDivisionError`

Kod:

```python
result = 10 / 0
print(result)
```

Problem: nie można dzielić przez zero.

---

## Zadanie 9 — Traceback detective

Utwórz plik `broken_examples.py`. Wklej do niego po kolei poniższe fragmenty i uruchom każdy z nich osobno.

Przy każdym błędzie zapisz:

1. typ błędu,
2. numer linii,
3. przyczynę błędu,
4. poprawioną wersję.

Fragment A:

```python
customer_name = "Ola"
print(custmer_name)
```

Fragment B:

```python
order_total = 120
if order_total > 100:
print("Free shipping")
```

Fragment C:

```python
price = "100"
discount = 20
final_price = price - discount
print(final_price)
```

<details>
<summary>Rozwiązanie</summary>

Fragment A — problem:

```python
customer_name = "Ola"
print(custmer_name)
```

Typ błędu: `NameError`.  
Przyczyna: literówka w nazwie zmiennej. Utworzono `customer_name`, a użyto `custmer_name`.

Poprawka:

```python
customer_name = "Ola"
print(customer_name)
```

Fragment B — problem:

```python
order_total = 120
if order_total > 100:
print("Free shipping")
```

Typ błędu: `IndentationError`.  
Przyczyna: po instrukcji `if` kolejna linia powinna mieć wcięcie.

Poprawka:

```python
order_total = 120
if order_total > 100:
    print("Free shipping")
```

Fragment C — problem:

```python
price = "100"
discount = 20
final_price = price - discount
print(final_price)
```

Typ błędu: `TypeError`.  
Przyczyna: `price` jest tekstem, a `discount` jest liczbą. Nie można odjąć liczby od tekstu.

Poprawka:

```python
price = 100
discount = 20
final_price = price - discount
print(final_price)
```

Można też wykonać konwersję:

```python
price = "100"
discount = 20
final_price = int(price) - discount
print(final_price)
```

</details>

---

# 7. Bezpieczna praca z AI

AI może pomagać w nauce programowania, ale nie zastępuje myślenia, testowania i odpowiedzialności za kod.

Dobre zastosowania AI:

- wyjaśnienie błędu prostym językiem,
- wygenerowanie podobnego przykładu,
- podpowiedź, gdzie szukać problemu,
- code review prostego kodu,
- przygotowanie danych testowych.

Złe zastosowania AI:

- wklejenie całego zadania i bezrefleksyjne skopiowanie odpowiedzi,
- używanie kodu, którego nie umiesz wyjaśnić,
- wklejanie haseł, tokenów, plików `.env`, danych klientów,
- traktowanie odpowiedzi AI jako prawdy bez uruchomienia kodu.

## Czego nie wklejamy do AI?

Nie wklejaj:

- haseł,
- tokenów API,
- kluczy dostępowych,
- plików `.env`,
- prywatnych adresów e-mail,
- danych klientów,
- danych finansowych,
- danych firmowych bez zgody.

## Dobry prompt do nauki

```text
Uczę się podstaw Pythona.
Znam tylko zmienne, typy, if/elif/else, pętle, listy i proste funkcje.

Dostaję taki błąd:
[tu wklejam zredagowany traceback bez danych prywatnych]

Wyjaśnij mi:
1. co oznacza ten błąd,
2. w której części kodu prawdopodobnie jest problem,
3. jakie pytania mam sobie zadać.

Nie podawaj od razu pełnego rozwiązania.
```

---

## Zadanie 10 — Redakcja danych przed wysłaniem do AI

Masz taki opis problemu:

```text
Klient jan.kowalski@firma-example.pl zgłosił problem.
W logach mam token: sk-live-1234567890SECRET.
Program wyrzuca błąd TypeError w pliku orders.py przy obliczaniu rabatu dla zamówienia nr 48291.
```

Przeredaguj opis tak, żeby można go było bezpieczniej wkleić do AI.

<details>
<summary>Rozwiązanie przykładowe</summary>

```text
Uczę się podstaw Pythona i mam problem z błędem TypeError.
Błąd pojawia się w pliku orders.py przy obliczaniu rabatu dla przykładowego zamówienia.
Usunąłem/usunęłam dane prywatne, tokeny i identyfikatory.

Kod:
[tu wklejam tylko neutralny fragment kodu bez danych klienta i bez tokenów]

Proszę wyjaśnij, co może oznaczać TypeError w takim kontekście.
Nie podawaj od razu gotowego rozwiązania, tylko naprowadź mnie krok po kroku.
```

Usunięto:

- adres e-mail klienta,
- token,
- konkretny numer zamówienia.

</details>

---

# 8. Zmienne i typy danych

Zmienna to nazwana wartość, którą możesz wykorzystać później w programie.

Przykład:

```python
customer_name = "Ola"
order_total = 149.99
items_count = 3
is_paid = True
```

W tym przykładzie mamy różne typy danych:

| Typ | Przykład | Do czego służy? |
|---|---|---|
| `str` | `"Ola"` | tekst |
| `int` | `3` | liczba całkowita |
| `float` | `149.99` | liczba z częścią dziesiętną |
| `bool` | `True` / `False` | wartość logiczna |
| `list` | `[100, 200, 50]` | lista wielu wartości |

Typ można sprawdzić funkcją `type()`:

```python
order_total = 149.99
print(type(order_total))
```

## Nazwy zmiennych

Dobre nazwy mówią, co przechowuje zmienna.

Dobre przykłady:

```python
order_total = 149.99
customer_email = "user@example.com"
free_shipping_threshold = 100
```

Słabe przykłady:

```python
x = 149.99
a = "user@example.com"
thing = 100
```

## Czego nie robić w nazwach zmiennych?

Nie używaj:

```python
1order = 100        # nazwa nie może zaczynać się od cyfry
order total = 100   # spacja jest niedozwolona
cena_łącznie = 100  # polskie znaki są niewygodne w kodzie
class = "premium"   # class to słowo kluczowe Pythona
```

Lepiej:

```python
order_total = 100
total_price = 100
customer_segment = "premium"
```

---

## Zadanie 11 — Zmienne zamówienia

Utwórz plik `order_variables.py`. Zapisz w nim informacje o zamówieniu:

- imię klienta,
- kwotę zamówienia,
- liczbę produktów,
- informację, czy zamówienie jest opłacone.

Następnie wypisz każdą wartość i jej typ.

<details>
<summary>Rozwiązanie</summary>

```python
customer_name = "Ola"
order_total = 149.99
items_count = 3
is_paid = True

print(customer_name)
print(type(customer_name))

print(order_total)
print(type(order_total))

print(items_count)
print(type(items_count))

print(is_paid)
print(type(is_paid))
```

Przykładowy wynik:

```text
Ola
<class 'str'>
149.99
<class 'float'>
3
<class 'int'>
True
<class 'bool'>
```

</details>

---

# 9. Operatory i proste obliczenia

Operatory pozwalają wykonywać działania na danych.

## Operatory arytmetyczne

```python
price = 100
discount = 20

print(price + discount)
print(price - discount)
print(price * 2)
print(price / 4)
```

## Operatory porównania

Porównania zwracają `True` albo `False`.

```python
order_total = 120

print(order_total > 100)
print(order_total >= 100)
print(order_total == 100)
print(order_total != 100)
```

## Operatory logiczne

```python
is_paid = True
has_address = True

print(is_paid and has_address)
print(is_paid or has_address)
print(not is_paid)
```

---

## Zadanie 12 — Kalkulator koszyka

Utwórz plik `basket_calculator.py`.

Dane:

```python
product_price = 120
quantity = 3
discount_rate = 0.10
```

Oblicz:

1. wartość koszyka przed rabatem,
2. wartość rabatu,
3. wartość koszyka po rabacie.

Wypisz wszystkie trzy wartości.

<details>
<summary>Rozwiązanie</summary>

```python
product_price = 120
quantity = 3
discount_rate = 0.10

basket_total = product_price * quantity
discount_value = basket_total * discount_rate
final_total = basket_total - discount_value

print("Basket total:", basket_total)
print("Discount value:", discount_value)
print("Final total:", final_total)
```

Wynik:

```text
Basket total: 360
Discount value: 36.0
Final total: 324.0
```

Warto zauważyć, że `0.10` oznacza 10%, a nie 10 zł.

</details>

---

# 10. Warunki `if`, `elif`, `else`

Warunek pozwala programowi podjąć decyzję.

```python
order_total = 120

if order_total >= 100:
    print("Free shipping")
else:
    print("Shipping cost: 15")
```

Czytamy to tak:

```text
Jeżeli wartość zamówienia jest większa lub równa 100,
to wypisz Free shipping.
W przeciwnym razie wypisz Shipping cost: 15.
```

## `elif`

`elif` przydaje się, gdy mamy więcej niż dwie możliwości.

```python
order_total = 700

if order_total >= 1000:
    segment = "premium"
elif order_total >= 500:
    segment = "high"
elif order_total >= 100:
    segment = "medium"
else:
    segment = "low"

print(segment)
```

Kolejność warunków ma znaczenie. Python sprawdza je od góry do dołu.

---

## Zadanie 13 — Darmowa dostawa

Utwórz plik `free_shipping.py`.

Dane:

```python
order_total = 99
free_shipping_threshold = 100
```

Jeżeli zamówienie jest większe lub równe progowi darmowej dostawy, wypisz:

```text
Free shipping
```

W przeciwnym razie wypisz:

```text
Shipping cost: 15
```

Przetestuj program dla wartości `99`, `100` i `150`.

<details>
<summary>Rozwiązanie</summary>

```python
order_total = 99
free_shipping_threshold = 100

if order_total >= free_shipping_threshold:
    print("Free shipping")
else:
    print("Shipping cost: 15")
```

Dla `order_total = 99` wynik to:

```text
Shipping cost: 15
```

Dla `order_total = 100` wynik to:

```text
Free shipping
```

Dla `order_total = 150` wynik to:

```text
Free shipping
```

Dlatego w tym zadaniu używamy `>=`, a nie tylko `>`.

</details>

---

## Zadanie 14 — Segment klienta

Utwórz plik `customer_segment.py`.

Na podstawie wartości zamówienia przypisz segment:

- `premium` dla zamówień od 1000 w górę,
- `high` dla zamówień od 500 do 999.99,
- `medium` dla zamówień od 100 do 499.99,
- `low` dla zamówień poniżej 100.

Wypisz segment.

<details>
<summary>Rozwiązanie</summary>

```python
order_total = 750

if order_total >= 1000:
    segment = "premium"
elif order_total >= 500:
    segment = "high"
elif order_total >= 100:
    segment = "medium"
else:
    segment = "low"

print("Customer segment:", segment)
```

Dla `750` wynikiem będzie:

```text
Customer segment: high
```

Ważne: zaczynamy od najwyższego progu. Gdyby pierwszy warunek brzmiał `order_total >= 100`, zamówienie za 750 też spełniłoby ten warunek i program nie doszedłby do segmentu `high`.

</details>

---

# 11. Listy

Lista przechowuje wiele wartości w jednej zmiennej.

```python
orders = [120, 80, 300, 45, 600]
```

Przydatne funkcje:

```python
print(len(orders))  # liczba elementów
print(sum(orders))  # suma
print(min(orders))  # najmniejsza wartość
print(max(orders))  # największa wartość
```

Indeksy w Pythonie zaczynają się od zera:

```python
orders = [120, 80, 300]

print(orders[0])  # 120
print(orders[1])  # 80
print(orders[2])  # 300
```

---

## Zadanie 15 — Lista kwot zamówień

Utwórz plik `orders_list.py`.

Dane:

```python
orders = [120, 80, 300, 45, 600]
```

Oblicz i wypisz:

1. liczbę zamówień,
2. sumę zamówień,
3. najmniejsze zamówienie,
4. największe zamówienie,
5. średnią wartość zamówienia.

<details>
<summary>Rozwiązanie</summary>

```python
orders = [120, 80, 300, 45, 600]

orders_count = len(orders)
total_value = sum(orders)
min_order = min(orders)
max_order = max(orders)
average_order = total_value / orders_count

print("Orders count:", orders_count)
print("Total value:", total_value)
print("Min order:", min_order)
print("Max order:", max_order)
print("Average order:", average_order)
```

Wynik:

```text
Orders count: 5
Total value: 1145
Min order: 45
Max order: 600
Average order: 229.0
```

</details>

---

# 12. Pętla `for`

Pętla `for` służy do przechodzenia po elementach listy.

```python
orders = [120, 80, 300]

for order in orders:
    print(order)
```

Czytamy to tak:

```text
Dla każdego zamówienia z listy zamówień wypisz jego wartość.
```

Dobra praktyka nazewnicza:

```python
orders = [120, 80, 300]

for order in orders:
    print(order)
```

`orders` to lista wielu zamówień.  
`order` to jedno zamówienie z tej listy.

## Licznik

```python
orders = [120, 80, 300, 45, 600]
large_orders_count = 0

for order in orders:
    if order >= 200:
        large_orders_count = large_orders_count + 1

print(large_orders_count)
```

## Budowanie nowej listy

```python
orders = [120, 80, 300, 45, 600]
large_orders = []

for order in orders:
    if order >= 200:
        large_orders.append(order)

print(large_orders)
```

---

## Zadanie 16 — Licznik dużych zamówień

Utwórz plik `large_orders_count.py`.

Dane:

```python
orders = [120, 80, 300, 45, 600, 220]
large_order_threshold = 200
```

Policz, ile zamówień ma wartość większą lub równą `200`.

<details>
<summary>Rozwiązanie</summary>

```python
orders = [120, 80, 300, 45, 600, 220]
large_order_threshold = 200
large_orders_count = 0

for order in orders:
    if order >= large_order_threshold:
        large_orders_count = large_orders_count + 1

print("Large orders count:", large_orders_count)
```

Wynik:

```text
Large orders count: 3
```

Zamówienia spełniające warunek to `300`, `600` i `220`.

</details>

---

## Zadanie 17 — Lista dużych zamówień

Utwórz plik `large_orders_list.py`.

Na podstawie listy:

```python
orders = [120, 80, 300, 45, 600, 220]
```

Utwórz nową listę `large_orders`, która zawiera tylko zamówienia od `200` w górę.

<details>
<summary>Rozwiązanie</summary>

```python
orders = [120, 80, 300, 45, 600, 220]
large_order_threshold = 200
large_orders = []

for order in orders:
    if order >= large_order_threshold:
        large_orders.append(order)

print("Large orders:", large_orders)
```

Wynik:

```text
Large orders: [300, 600, 220]
```

Pusta lista `large_orders = []` musi powstać przed pętlą. W pętli dodajemy do niej tylko te elementy, które spełniają warunek.

</details>

---

# 13. `input()` i konwersja typów

Funkcja `input()` pozwala pobrać tekst wpisany przez użytkownika.

```python
name = input("Podaj imię: ")
print("Cześć", name)
```

Ważna rzecz: `input()` zawsze zwraca tekst, czyli typ `str`.

Jeżeli chcesz wykonać obliczenia, musisz zamienić tekst na liczbę:

```python
order_total_text = input("Podaj wartość zamówienia: ")
order_total = float(order_total_text)

print(order_total * 2)
```

Jeżeli użytkownik wpisze tekst, którego nie da się zamienić na liczbę, program zwróci błąd `ValueError`.

---

## Zadanie 18 — Prosty formularz wejściowy

Utwórz plik `order_input.py`.

Program ma:

1. zapytać użytkownika o wartość zamówienia,
2. zamienić odpowiedź na `float`,
3. sprawdzić, czy zamówienie kwalifikuje się do darmowej dostawy od `100`,
4. wypisać odpowiedni komunikat.

<details>
<summary>Rozwiązanie</summary>

```python
order_total_text = input("Podaj wartość zamówienia: ")
order_total = float(order_total_text)
free_shipping_threshold = 100

if order_total >= free_shipping_threshold:
    print("Free shipping")
else:
    print("Shipping cost: 15")
```

Przykład działania:

```text
Podaj wartość zamówienia: 120
Free shipping
```

Jeżeli wpiszesz `abc`, program zwróci `ValueError`. To normalne na tym etapie. W kolejnym kroku można dodać prostą pętlę walidacyjną.

</details>

---

# 14. Pętla `while`

Pętla `while` powtarza kod tak długo, jak warunek jest prawdziwy.

```python
counter = 1

while counter <= 3:
    print(counter)
    counter = counter + 1
```

Wynik:

```text
1
2
3
```

Uważaj na nieskończone pętle. Jeżeli warunek nigdy nie stanie się fałszywy, program będzie działał bez końca.

Przykład problemu:

```python
counter = 1

while counter <= 3:
    print(counter)
```

Tutaj `counter` nigdy się nie zmienia, więc warunek zawsze jest prawdziwy.

---

## Zadanie 19 — Pytaj do skutku

Utwórz plik `while_order_input.py`.

Program ma pytać użytkownika o wartość zamówienia tak długo, aż użytkownik poda liczbę większą od zera.

Na tym etapie załóż, że użytkownik wpisuje liczby, np. `-10`, `0`, `50`. Nie musisz jeszcze obsługiwać tekstu typu `abc`.

<details>
<summary>Rozwiązanie</summary>

```python
order_total = 0

while order_total <= 0:
    order_total_text = input("Podaj wartość zamówienia większą od zera: ")
    order_total = float(order_total_text)

print("Przyjęto wartość zamówienia:", order_total)
```

Przykład działania:

```text
Podaj wartość zamówienia większą od zera: -10
Podaj wartość zamówienia większą od zera: 0
Podaj wartość zamówienia większą od zera: 50
Przyjęto wartość zamówienia: 50.0
```

</details>

---

# 15. Funkcje

Funkcja to nazwany fragment kodu, który wykonuje konkretne zadanie.

Przykład:

```python
def calculate_discounted_price(price, discount_rate):
    discount_value = price * discount_rate
    final_price = price - discount_value
    return final_price

result = calculate_discounted_price(100, 0.20)
print(result)
```

Funkcje pomagają:

- unikać powtarzania kodu,
- porządkować logikę,
- testować małe fragmenty programu,
- nazywać intencję kodu.

## `print()` a `return`

`print()` pokazuje coś na ekranie.

`return` zwraca wynik z funkcji, żeby można było go dalej wykorzystać.

Przykład z `return`:

```python
def add_tax(price):
    return price * 1.23

price_with_tax = add_tax(100)
print(price_with_tax)
```

Przykład mniej elastyczny:

```python
def add_tax(price):
    print(price * 1.23)

price_with_tax = add_tax(100)
```

Druga funkcja tylko drukuje wynik. Nie oddaje go dalej do programu.

---

## Zadanie 20 — Funkcja licząca rabat

Utwórz plik `discount_function.py`.

Napisz funkcję `calculate_discounted_price(price, discount_rate)`, która:

1. przyjmuje cenę i procent rabatu zapisany jako liczba dziesiętna,
2. zwraca cenę po rabacie,
3. nie używa `print()` wewnątrz funkcji.

Przetestuj funkcję dla ceny `200` i rabatu `0.15`.

<details>
<summary>Rozwiązanie</summary>

```python
def calculate_discounted_price(price, discount_rate):
    discount_value = price * discount_rate
    final_price = price - discount_value
    return final_price

result = calculate_discounted_price(200, 0.15)
print("Final price:", result)
```

Wynik:

```text
Final price: 170.0
```

Funkcja zwraca wynik przez `return`, a wypisanie wyniku dzieje się poza funkcją.

</details>

---

## Zadanie 21 — Funkcja klasyfikująca zamówienie

Utwórz plik `classify_order.py`.

Napisz funkcję `classify_order(order_total)`, która zwraca:

- `premium`, jeśli zamówienie ma wartość od 1000,
- `high`, jeśli ma wartość od 500,
- `medium`, jeśli ma wartość od 100,
- `low`, jeśli ma wartość poniżej 100.

Przetestuj funkcję dla kilku wartości.

<details>
<summary>Rozwiązanie</summary>

```python
def classify_order(order_total):
    if order_total >= 1000:
        return "premium"
    elif order_total >= 500:
        return "high"
    elif order_total >= 100:
        return "medium"
    else:
        return "low"

print(classify_order(50))
print(classify_order(120))
print(classify_order(750))
print(classify_order(1500))
```

Wynik:

```text
low
medium
high
premium
```

Zwróć uwagę, że funkcja nie musi mieć zmiennej `segment`. Może od razu zwracać wynik.

</details>

---

## Zadanie 22 — Funkcja licząca średnią

Utwórz plik `average_order.py`.

Napisz funkcję `calculate_average(numbers)`, która:

1. przyjmuje listę liczb,
2. zwraca średnią,
3. dla pustej listy zwraca `0`.

<details>
<summary>Rozwiązanie</summary>

```python
def calculate_average(numbers):
    if len(numbers) == 0:
        return 0

    return sum(numbers) / len(numbers)

orders = [120, 80, 300, 45, 600]
average_order = calculate_average(orders)

print("Average order:", average_order)
print("Average for empty list:", calculate_average([]))
```

Wynik:

```text
Average order: 229.0
Average for empty list: 0
```

Warunek dla pustej listy chroni przed dzieleniem przez zero.

</details>

---

# 16. Mini-projekt: prosty analizator zamówień

Teraz połączysz kilka elementów:

- listę,
- obliczenia,
- warunki,
- pętlę,
- funkcje,
- tekstowy raport.

Program ma analizować listę zamówień z jednego dnia.

## Wymagania

Program powinien:

1. mieć listę wartości zamówień,
2. obliczać liczbę zamówień,
3. obliczać sumę zamówień,
4. obliczać średnią,
5. znajdować najmniejsze i największe zamówienie,
6. liczyć zamówienia powyżej ustalonego progu,
7. klasyfikować dzień sprzedaży jako `weak`, `normal` albo `strong`,
8. wypisywać prosty raport tekstowy,
9. mieć minimum dwie funkcje.

Przykładowe progi klasyfikacji dnia:

- `strong` — suma zamówień od 1500,
- `normal` — suma zamówień od 500,
- `weak` — suma zamówień poniżej 500.

---

## Zadanie 23 — Mini-raport dzienny

Utwórz plik `daily_orders_report.py`.

Napisz program zgodny z wymaganiami mini-projektu.

<details>
<summary>Rozwiązanie podstawowe</summary>

```python
def calculate_average(numbers):
    if len(numbers) == 0:
        return 0

    return sum(numbers) / len(numbers)


def count_large_orders(orders, threshold):
    large_orders_count = 0

    for order in orders:
        if order >= threshold:
            large_orders_count = large_orders_count + 1

    return large_orders_count


def classify_sales_day(total_value):
    if total_value >= 1500:
        return "strong"
    elif total_value >= 500:
        return "normal"
    else:
        return "weak"


orders = [120, 80, 300, 45, 600, 220]
large_order_threshold = 200

orders_count = len(orders)
total_value = sum(orders)
average_order = calculate_average(orders)
min_order = min(orders)
max_order = max(orders)
large_orders_count = count_large_orders(orders, large_order_threshold)
sales_day_segment = classify_sales_day(total_value)

print("Daily orders report")
print("-------------------")
print("Orders count:", orders_count)
print("Total value:", total_value)
print("Average order:", average_order)
print("Min order:", min_order)
print("Max order:", max_order)
print("Large orders count:", large_orders_count)
print("Sales day segment:", sales_day_segment)
```

Przykładowy wynik:

```text
Daily orders report
-------------------
Orders count: 6
Total value: 1365
Average order: 227.5
Min order: 45
Max order: 600
Large orders count: 3
Sales day segment: normal
```

</details>

<details>
<summary>Rozwiązanie z obsługą pustej listy</summary>

```python
def calculate_average(numbers):
    if len(numbers) == 0:
        return 0

    return sum(numbers) / len(numbers)


def count_large_orders(orders, threshold):
    large_orders_count = 0

    for order in orders:
        if order >= threshold:
            large_orders_count = large_orders_count + 1

    return large_orders_count


def classify_sales_day(total_value):
    if total_value >= 1500:
        return "strong"
    elif total_value >= 500:
        return "normal"
    else:
        return "weak"


def print_daily_report(orders, large_order_threshold):
    orders_count = len(orders)
    total_value = sum(orders)
    average_order = calculate_average(orders)
    large_orders_count = count_large_orders(orders, large_order_threshold)
    sales_day_segment = classify_sales_day(total_value)

    print("Daily orders report")
    print("-------------------")
    print("Orders count:", orders_count)
    print("Total value:", total_value)
    print("Average order:", average_order)
    print("Large orders count:", large_orders_count)
    print("Sales day segment:", sales_day_segment)

    if len(orders) > 0:
        print("Min order:", min(orders))
        print("Max order:", max(orders))
    else:
        print("Min order: no data")
        print("Max order: no data")


orders = [120, 80, 300, 45, 600, 220]
large_order_threshold = 200

print_daily_report(orders, large_order_threshold)
```

Ta wersja nie wywołuje `min()` ani `max()` dla pustej listy, bo to spowodowałoby błąd.

</details>

---

# 17. Refaktoryzacja nazw

Refaktoryzacja to poprawianie kodu bez zmiany jego działania.

Na początku najważniejsza refaktoryzacja to poprawa nazw.

Słabsza wersja:

```python
x = [120, 80, 300]
s = sum(x)
a = s / len(x)
print(a)
```

Lepsza wersja:

```python
orders = [120, 80, 300]
total_value = sum(orders)
average_order = total_value / len(orders)
print(average_order)
```

Dłuższa nazwa jest lepsza, jeśli pomaga zrozumieć intencję kodu.

---

## Zadanie 24 — Popraw nazwy

Popraw nazwy zmiennych w poniższym kodzie. Działanie programu ma pozostać takie samo.

```python
x = [100, 50, 300]
y = 0

for z in x:
    if z > 100:
        y = y + 1

print(y)
```

<details>
<summary>Rozwiązanie przykładowe</summary>

```python
orders = [100, 50, 300]
large_orders_count = 0

for order in orders:
    if order > 100:
        large_orders_count = large_orders_count + 1

print(large_orders_count)
```

Program nadal robi to samo: liczy, ile zamówień jest większych niż `100`. Różnica polega na tym, że teraz łatwiej zrozumieć intencję kodu.

</details>

---

# 18. Bezpieczne pytanie do AI o własny kod

AI może pomóc w code review, ale warto prosić o konkretny rodzaj pomocy.

Zbyt ogólny prompt:

```text
Popraw mój kod.
```

Lepszy prompt:

```text
Uczę się podstaw Pythona.
Znam tylko zmienne, listy, if/elif/else, pętle for/while i proste funkcje.

Przejrzyj mój kod i daj 3 najważniejsze uwagi:
1. czy nazwy są czytelne,
2. czy funkcje są proste,
3. czy są miejsca, które mogą spowodować błąd.

Nie przepisuj całego kodu.
Nie używaj klas, wyjątków, dekoratorów ani zaawansowanych konstrukcji.
```

---

## Zadanie 25 — Prompt do code review

Przygotuj prompt, którym poprosisz AI o review pliku `daily_orders_report.py`.

Prompt ma:

- informować, że jesteś osobą początkującą,
- ograniczać AI do znanych tematów,
- prosić maksymalnie o 3 uwagi,
- zabraniać przepisywania całego kodu,
- przypominać, że kod nie zawiera danych prywatnych.

<details>
<summary>Rozwiązanie przykładowe</summary>

```text
Uczę się podstaw Pythona i przygotowuję prosty raport zamówień.
Znam tylko:
- zmienne,
- typy danych,
- if/elif/else,
- listy,
- pętle for i while,
- proste funkcje z return.

Poniżej wklejam kod bez danych prywatnych, tokenów i haseł.

Proszę przejrzyj kod i podaj maksymalnie 3 najważniejsze uwagi:
1. czy nazwy zmiennych i funkcji są czytelne,
2. czy kod jest zrozumiały dla osoby początkującej,
3. czy widzisz miejsce, które może spowodować błąd.

Nie przepisuj całego kodu.
Nie używaj klas, dekoratorów, zewnętrznych bibliotek ani zaawansowanych konstrukcji.
Najpierw wyjaśnij uwagi prostym językiem.

Kod:
[tu wklejam kod]
```

</details>

---

# 19. Podsumowanie bloku

Po tym bloku warto umieć samodzielnie:

- otworzyć folder projektu w VS Code,
- uruchomić terminal w katalogu projektu,
- sprawdzić wersję Pythona,
- sprawdzić wersję Gita,
- utworzyć repozytorium Git,
- wykonać prosty commit,
- utworzyć plik `.py`,
- uruchomić plik Pythona,
- utworzyć i aktywować `.venv`,
- przeczytać podstawowy traceback,
- napisać program ze zmiennymi i warunkami,
- przejść pętlą po liście,
- napisać prostą funkcję z `return`,
- bezpiecznie zapytać AI o pomoc.

---

## Pytania kontrolne

1. Czym różni się Python od VS Code?
2. Do czego służy terminal?
3. Po co tworzymy folder projektu?
4. Do czego służy Git?
5. Co zapisuje commit?
6. Czego nie powinno się commitować?
7. Po co tworzymy `.venv`?
8. Od której części tracebacka warto zacząć czytanie błędu?
9. Czym różni się `str` od `int`?
10. Co zwraca `input()`?
11. Kiedy użyjesz `if/elif/else`?
12. Kiedy użyjesz pętli `for`?
13. Do czego służy `while`?
14. Czym różni się `print()` od `return`?
15. Czego nie wklejamy do AI?

---

## Ostatnia zasada

Nie musisz pamiętać wszystkiego. Masz umieć zrobić mały krok, uruchomić kod, przeczytać błąd i sprawdzić, czy poprawka działa.

To jest dokładnie ten nawyk, który będzie potrzebny w kolejnych blokach kursu.
