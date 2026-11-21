# LAN Monitor na Linux

Instalacja jako usługa w tle (systemd). Aplikacja jest w czystym Pythonie, nie wymaga
żadnych pakietów pip.

## Wymagania
- Linux z **systemd** (Debian/Ubuntu/Mint, Fedora/RHEL, openSUSE, Arch…).
- **Python 3.8+**, **iproute2** (`ip`), **iputils-ping** (`ping`).

## Instalacja z pakietu .deb (Debian/Ubuntu i pochodne)
1. Pobierz **[lanmonitor_1.26.0_amd64.deb](../../releases/latest/download/lanmonitor_1.26.0_amd64.deb)** (amd64).
2. Zainstaluj (sam pociągnie zależności):
   ```bash
   sudo apt install ./lanmonitor_1.26.0_amd64.deb
   ```
   (na starszych systemach: `sudo dpkg -i lanmonitor_1.26.0_amd64.deb && sudo apt -f install`)
3. Usługa startuje automatycznie. Otwórz pulpit: **http://127.0.0.1:8787**
   (ustawienia/kreator: http://127.0.0.1:8788/config).

> Pakiet jest **utwardzony**: zawiera zamrożony interpreter i skompilowane moduły —
> kod aplikacji nie jest jawny (tak jak instalator Windows). Nie wymaga Pythona w systemie.

Pełna wersja (FULL) działa 14 dni, potem wymaga licencji — patrz niżej.

## Obsługa usługi
```bash
systemctl status lanmonitor      # stan
systemctl restart lanmonitor     # restart
journalctl -u lanmonitor -f      # logi na żywo
```

## Dostęp do panelu z innego komputera
Domyślnie panel słucha tylko lokalnie (`127.0.0.1`) to bezpieczne. Aby wejść zdalnie:

- **Tunel SSH (zalecane):**
  ```bash
  ssh -L 8787:127.0.0.1:8787 user@serwer
  ```
  i otwórz `http://127.0.0.1:8787` u siebie; albo
- **nasłuch w LAN:** w `/var/lib/lanmonitor/config.json` ustaw `"host": "0.0.0.0"`,
  `sudo systemctl restart lanmonitor`, otwórz port w zaporze (`sudo ufw allow 8787/tcp`)
  i **ustaw hasło logowania** w `/config`.

## Aktywacja licencji
Tak samo jak na Windows, ten sam plik `.lic`:
- w panelu: `http://127.0.0.1:8787/license` → „Wczytaj plik .lic” / „Wczytaj inną licencję”,
- albo z konsoli:
  ```bash
  sudo python3 /opt/lanmonitor/lanmonitor_main.py --fingerprint      # odcisk serwera
  sudo python3 /opt/lanmonitor/lanmonitor_main.py --license plik.lic
  ```

## Deinstalacja
```bash
sudo apt remove lanmonitor            # usuwa program, ZOSTAWIA dane
sudo apt purge  lanmonitor            # usuwa też dane /var/lib/lanmonitor
```

## Uwagi
- Usługa działa jako **root** (skan sieci wymaga pełnych uprawnień — odpowiednik SYSTEM na Windows).
- Dane w `/var/lib/lanmonitor` są dostępne tylko dla roota (`chmod 700`).
- Wykrywanie obejmuje automatycznie **wszystkie aktywne podsieci** serwera.
