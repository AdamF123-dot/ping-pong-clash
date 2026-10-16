# Ping-Pong Clash

Aplikacja do liczenia meczów tenisa stołowego dla domu i przyjaciół. Jeden plik HTML, bez instalacji.

- Awatary w stylu kreskówek z gadżetami: czapki, okulary, wąsy i inne.
- Liczenie punktów i setów (11 lub 21 pkt, 1 set, BO3, BO5, BO7) z wskazaniem serwisu.
- Sterowanie głosem: powiedz imię gracza, a dostanie punkt. „Cofnij” cofa punkt.
- Czytanie wyniku po każdym punkcie.
- Historia meczów z datami, ranking, rekordy i profil każdego gracza.
- Osobny tryb turnieju z drabinką pucharową.

Sterowanie głosem działa w Chrome (Android i komputer) i wymaga internetu oraz zgody na mikrofon.
Dane są zapisywane w przeglądarce. Na dole zakładki „Gracze” jest kopia zapasowa do pobrania i wczytania.

## Synchronizacja między telefonami

Opcjonalna, przez darmową bazę Firebase Realtime Database. W zakładce „Gracze” rozwiń „Jak ją przygotować”,
wklej adres bazy i kliknij „Włącz synchronizację”. Potem użyj „Pokaż link do dołączenia” i otwórz go na pozostałych telefonach.

Reguły bazy (zakładka Rules w Firebase):

```json
{"rules":{".read":false,".write":false,"pp":{"$room":{".read":true,".write":true}}}}
```

Dostęp do danych ma każdy, kto zna link z kodem, więc nie udostępniaj go poza rodziną.
Trwający mecz jest zapisany tylko na urządzeniu, na którym go liczysz. Wspólne są gracze, zapisane mecze i turnieje.
