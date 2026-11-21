# Jak aktywować licencję LAN Monitor

Po instalacji aplikacja działa **14 dni w pełnej wersji (FULL)**. Aby korzystać dalej,
wgraj licencję. Są dwa sposoby: przez pulpit w przeglądarce (najprościej) albo z konsoli.

## 1. Przez pulpit (zalecane)
1. Otwórz **`http://localhost:8787/license`**.
2. Skopiuj **„Odcisk tego serwera”** (przycisk *Kopiuj odcisk*) i wyślij go wydawcy,
   jeśli kupujesz licencję przypiętą do komputera. (Dla licencji „na dowolny komputer”
   odcisk nie jest potrzebny.)
3. Gdy dostaniesz plik **`lanmonitor.lic`** na e‑mail:
   - kliknij **„Wczytaj plik .lic…”** i wskaż otrzymany plik (albo wklej jego treść w pole),
   - kliknij **„Aktywuj”**.
4. Status zmieni się na **„Licencja ważna”** gotowe.

![Strona aktywacji licencji](obrazy/licencja.png)

## 2. Podmiana aktywnej licencji
Jeśli masz już aktywną licencję i chcesz ją zmienić (np. na nowszą albo testową):
na stronie `/license` kliknij **„Wczytaj inną licencję”**, wklej nową i **„Aktywuj”** —
zastąpi obecną. Nie trzeba ruszać żadnych plików.

## 3. Z konsoli serwera (opcjonalnie)
Jako administrator:
```
sudo lanmonitor --fingerprint          # pokaże odcisk serwera
sudo lanmonitor --license lanmonitor.lic
```
(na Windows uruchom wiersz poleceń jako administrator; polecenie bez `sudo`)

## 4. Licencja wygasła / minął okres — co zrobić?
Nie trzeba nic odinstalowywać ani kombinować. Po wygaśnięciu aplikacja **blokuje dostęp
do danych, ale strona aktywacji dalej działa** od razu wgrasz nową licencję:

1. Otwórz **`http://localhost:8787/license`** (nawet gdy reszta panelu jest zablokowana,
   program sam Cię tu przekieruje).
2. Jeśli masz już nową licencję, kliknij **„Wczytaj inną licencję”**, wklej plik `.lic`
   i **„Aktywuj”**. Dostęp wraca natychmiast.
3. Jeśli jeszcze jej nie masz, skopiuj **„Odcisk tego serwera”** i napisz po odnowienie
   (kontakt niżej). Odeślemy nowy plik `.lic`.

> **To nie jest nowy trial.** Wgrywasz swoją **płatną** licencję, program przechodzi
> na nią bez utraty danych i bez ponownego okresu próbnego.

## 5. Prawidłowe odinstalowanie
**Chcesz tylko zmienić/odnowić licencję?** Nie odinstalowuj, użyj sekcji 2 lub 4 powyżej.

Pełne odinstalowanie (gdy chcesz usunąć program z komputera):
1. **Ustawienia Windows → Aplikacje → Zainstalowane aplikacje**, znajdź **LAN Monitor**
   → **Odinstaluj** (albo *Panel sterowania → Programy i funkcje*).
2. Deinstalator zatrzyma usługę i usunie program.

Co warto wiedzieć:
- Ponowna instalacja **nie uruchamia nowego okresu próbnego**, to zabezpieczenie celowe.
  Po reinstalacji po prostu aktywuj swoją licencję (sekcja 1).
- Dane i historia w `C:\ProgramData\LANMonitor` pozostają po odinstalowaniu (możesz do nich
  wrócić po reinstalacji). Jeśli chcesz je też usunąć, skasuj ten folder ręcznie jako
  administrator — **ale** nie przywróci to kolejnego trialu.
- Przenosisz licencję na inny komputer albo porządkujesz instalację? Napisz do nas, pomożemy to zrobić poprawnie.

## Najczęstsze pytania

**Skąd wziąć plik `.lic`?**
Dostajesz go e‑mailem po zakupie. Jeśli nie dotarł, sprawdź spam albo napisz.

**„Podpis licencji nieprawidłowy” albo aktywacja się nie udaje.**
Najczęściej licencja została wystawiona dla innego komputera (zły odcisk) lub plik został
uszkodzony przy kopiowaniu. Wgraj plik `.lic` bez zmian (najlepiej „Wczytaj plik .lic…”),
a jeśli nie pomoże, odeślij wydawcy aktualny odcisk serwera ze strony `/license`.

**Czy po reinstalacji trial zacznie się od nowa?**
Nie. Okres próbny jest powiązany z komputerem, więc ponowna instalacja go nie odnawia.

**Czy dane wychodzą do internetu?**
Nie. Monitoring działa lokalnie; dane zostają na Twoim komputerze, serwerze.

---
Potrzebujesz pomocy? 
Kontakt: **Piotr Pęsiek** 
email: podatnosci@wp.pl
