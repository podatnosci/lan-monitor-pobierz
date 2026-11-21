# Wymagania techniczne i wydajność

LAN Monitor jest lekki, działa w tle jako usługa systemowa i nie wymaga serwera baz
danych ani chmury. Poniższe wartości to praktyczne zalecenia; realne zużycie zależy od
wielkości sieci i włączonych modułów (zwłaszcza bezpieczeństwa w Pro/FULL).

## System operacyjny
- **Windows 10 / 11 (64‑bit)** lub **Windows Server 2016 lub nowszy**.
- Uprawnienia **administratora** do instalacji (usługa działa jako konto SYSTEM).
- Dostęp do monitorowanej sieci LAN (to samo urządzenie/segment, co obserwowane hosty).

## Minimalne wymagania (małe sieci, edycja Standard)
| Zasób | Minimum |
|---|---|
| Procesor (CPU) | 2 rdzenie, 64‑bit |
| Pamięć RAM | 2 GB |
| Dysk | 500 MB wolnego miejsca (program + dane/historia) |
| Sieć | karta w monitorowanej sieci LAN |

Wystarcza dla typowego biura — rzędu **do ~200 urządzeń** w jednej podsieci.

## Zalecane (większe sieci, Pro / FULL)
| Zasób | Zalecane |
|---|---|
| Procesor (CPU) | 4 rdzenie lub więcej |
| Pamięć RAM | 4–8 GB |
| Dysk | 1–2 GB (więcej historii i logów) |
| Sieć | łącze do wszystkich monitorowanych segmentów |

Komfortowo obsługuje **setki urządzeń**; przy **1000+ urządzeń** lub wielu lokalizacjach
(MSP) zaplanuj 8 GB RAM i szybszy dysk (SSD).

## Ile urządzeń obsłuży?
- Technicznie aplikacja skanuje tablicę ARP monitorowanych podsieci — jedna podsieć `/24`
  to maks. 254 hosty; przy wielu podsieciach odpowiednio więcej.
- Praktyczny komfort: **kilkaset urządzeń** na zalecanej konfiguracji, **1000+** przy 8 GB RAM.
- **Rzeczywisty limit wynika z licencji** (pole „liczba urządzeń” w Standard/Pro/MSP).
  Edycja **FULL nie ma limitu** urządzeń ani lokalizacji.

## Moduły bezpieczeństwa (Pro/FULL) — uwaga o zasobach
Funkcje IDS (Suricata, Zeek, CrowdSec) i głęboka analiza ruchu potrafią znacząco zwiększyć
zużycie CPU i RAM, jeśli je włączysz i skierujesz na nie duży ruch. Dla intensywnego IDS
rozważ **4+ rdzenie i 8 GB RAM**. Sam monitoring (bez IDS) jest dużo lżejszy.

## Sieć i porty
- Pulpit w przeglądarce: `http://localhost:8787` (lokalnie na serwerze).
- Dane trzymane lokalnie w `C:\ProgramData\LANMonitor` (dostęp tylko SYSTEM i Administratorzy).
- Działa **offline** — nie wymaga internetu do monitorowania (tryb licencji online jest opcjonalny).

---
Funkcje edycji: **[FUNKCJE.md](FUNKCJE.md)** · Aktywacja i odnawianie: **[JAK_AKTYWOWAC.md](JAK_AKTYWOWAC.md)**
