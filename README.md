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

## Poziomy, postacie i medale
- Co 1000 zdobytych punktów (suma punktów gracza) = nowy poziom i nowe elementy: postacie (Kot, Lis, Sowa, Robot, Dino, Kosmita, Panda, Duszek, Jednorożec), czapki, okulary, fryzury, oczy, buzie i efekty.
- Medale liczone z historii meczów (synchronizują się między telefonami).
- Kosz na karcie gracza usuwa gracza (mecze zostają w historii).

## Monety i sklep
- Monety: 10 za wygrany set, 50 za mecz, 200 za puchar turnieju (liczone z historii meczów, więc wspólne na wszystkich urządzeniach).
- Zakładka Sklep: 4 skrzynki (zwykła 100, rzadka 250, epicka 600, legendarna 1500) z losowymi gadżetami, efektami i kolorami; powtórka zwraca część monet.
- Posiadane przedmioty są w kolekcji gracza i w edytorze awatara.

## Tryb Świnka
- Przy starcie meczu wybierz tryb „Świnka (2 pkt)”. Powiedz „świnka” i imię gracza, a dostanie 2 punkty zamiast 1 (albo dotknij przycisku Świnka i potem pole gracza). Punkty nie wychodzą poza koniec seta.

## Rozszerzenie: 30000 punktów, więcej skrzynek i medali
- Odblokowania za punkty sięgają 30000 (nowe postacie: Smok, Żaba, Pingwin, Wampir, Yeti, Złoty Mistrz oraz style, efekty i kolory). Każdy poziom daje też 50 monet.
- 9 skrzynek w sklepie (od Drobnej za 40 do Skarbca mistrza za 6000), w tym tylko kolory i tylko gadżety.
- 54 medale.

## Tryby: 2 na 2, Złota piłka, Przewaga serwisu
- „Drużyny: 2 na 2” (dowolny tryb): wynik liczy się wszystkim czterem graczom w statystykach, medalach i monetach. Głos rozpoznaje imiona obu graczy drużyny.
- Złota piłka: po losowej wymianie aplikacja ogłasza złotą piłkę, a następny punkt jest wart 3.
- Przewaga serwisu: serwujący dostaje 2 punkty za wymianę, przyjmujący 1; zmiana serwisu liczy wymiany, nie punkty.
- „Cofnij” cofa całą ostatnią wymianę (także świnkę, złotą piłkę i podwójny punkt).


## Tryby: BO9, Sprint, Podwójna stawka, Król stołu
- BO9: wygrywa ten, kto pierwszy zdobędzie 5 setów.
- Sprint 3 lub 5 minut: wygrywa lepszy wynik po czasie, przy remisie złoty punkt; jest pauza i odliczanie (głos ostrzega o minucie i 10 sekundach).
- Podwójna stawka: raz w każdym secie każda drużyna może podbić stawkę, a najbliższy punkt jest wart 2 dla zwycięzcy wymiany (głosem: „podwójna stawka” i imię).
- Król stołu: mecze o koronę z obecnym królem; ranking panowań w zakładce Ranking, bonus monet za koronę (30) i obronę (15) oraz dwa medale.
