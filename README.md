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

## Trening solo (liczenie odbić po dźwięku)
- Zakładka Trening: aplikacja słucha mikrofonu i liczy uderzenia piłeczki o rakietkę (kalibracja, suwak czułości, ręczne +1/−1). Tryby: swobodnie oraz runda 1, 3 lub 5 minut. Serię kończy przerwa 1,5–4 s.
- Rekord serii i najlepsze rundy są w profilu gracza i w tabeli w zakładce Trening; monety za trening (do 30 + 20 za rekord) oraz 10 medali.

- **Filtr odbić o podłogę** (Trening): jeśli kolejne uderzenia przyspieszają i cichną (piłeczka spadła), aplikacja ich nie liczy i kończy serię. Można wyłączyć w ustawieniach treningu.
- **Trening w parze**: w zakładce Trening przełącz tryb na „W parze”, wybierz dwóch graczy. Liczona jest wspólna wymiana, opcjonalnie z pomijaniem cichszego odbicia od stołu. Rekordy par są w tabeli i w profilach obu graczy, a monety dostają oboje.
- **Nowe ćwiczenia w zakładce Trening** (wybór „Ćwiczenie”):
  - **Serwis na cel** – aplikacja losuje strefę stołu (6 stref), Ty serwujesz i zaznaczasz „Trafiony” albo „Pudło”. Bez mikrofonu. Celność i mapa stref w profilu.
  - **Plan** – gotowe zestawy etapów (krótki 3 min, rozgrzewka 5 min, mocny 8 min) z głosowym prowadzeniem, odpoczynkami i liczeniem odbić w każdym etapie.
  - **Refleks** – podczas odbijania aplikacja co kilka sekund podaje komendę (forhend, bekhend, na przemian, szybciej, spokojniej).
  - Nowe medale: Pierwszy serwis na cel, Snajper serwisu, Plan wykonany, Refleks.
- **Głos: wynik zamiast imienia** – można powiedzieć np. „5 do 5” (najpierw wynik serwującego, potem odbierającego). Aplikacja sama ustala, kto zdobył punkt, uwzględniając zmianę serwisu, złotą piłkę, świnkę i koniec seta.
- **Dogrywka do 30** – w ustawieniach meczu i turnieju przełącznik „Dogrywka: Do 30 pkt / Bez limitu”. Przy „do 30” punkt przy 29:29 kończy seta (30:29). Aplikacja zapowiada to głosem.
- **Trening w parze: „Co drugi dźwięk”** – uderzenie rakietką i odbicie od stołu to dwa dźwięki, liczone jako jedno odbicie (domyślnie).
- **Tabela miesięczna i roczna** (Ranking): bilans meczów (wygrane:przegrane), punkty (zdobyte:stracone) i liczba meczów, z przełączaniem miesiąca lub roku strzałkami.

## Dart (rzutki)
Po wejściu do aplikacji pojawia się pytanie „W co dzisiaj gramy?” z wyborem **Dart** albo **Ping Pong**. Gracze i awatary są wspólne dla obu gier.
- Ustawienia meczu: 2 do 4 graczy, gra od **301 / 501 / 701**, do ilu wygranych **setów**, ile **legów** w secie, zakończenie **double out** albo dowolne, kto zaczyna.
- Wpisywanie rzutów przyciskami 1–20, 25, 50 i Pudło oraz **Double** i **Triple** (np. Triple, potem 20 = 60). Kolejka to 3 rzuty, potem rzuca następny gracz. Przebicie (poniżej zera, zostaje 1 albo zero nie dublem) unieważnia kolejkę.
- Podpowiedź wykończenia przy double out, średnia z trzech rzutów, kolejki 100+ i 180, cofanie rzutów, opcjonalny głos.
- Zakładki: Mecz, Historia (ze statystykami meczu), Statystyki (bilans, legi, średnia, 180, najwyższe wykończenie, najlepszy leg), Gracze.
- **Mały czerwony znaczek z liczbą rzutów** (9 przy 501, 6 przy 301, 12 przy 701) przy nicku gracza, który nadal może zamknąć leg w minimalnej liczbie rzutów.
- **Tryb z botem**: poziomy Bardzo łatwy, Łatwy, Średni, Trudny, Bardzo trudny oraz „Dopasuj do mnie” (bot startuje od Twojej dotychczasowej średniej i w trakcie meczu dostosowuje się do tego, jak rzucasz). Bot rzuca po jednym rzucie, cofnięcie usuwa jego kolejkę. Poziomy skalibrowano symulacją rozrzutu rzutów na tarczy.
- W trakcie meczu przy każdym graczu widać **średnią w tym meczu**.
- Statystyki: tabela **miesięczna i roczna** (bilans meczów W:L, legi W:L, punkty, mecze) oraz karta gracza: rzucone rzutki, wygrane sety i legi, % wygranych, średnia na leg i na mecz, najmniej rzutów w legu, 100+/140+/180, triple według pola (T20…T1), double, pudła.
- **Monety wspólne** dla Ping Ponga i darta: w darcie leg 3, set 10, mecz 40, 180 po 10, leg w minimum rzutów 150. Sklep jest dostępny też z poziomu darta.
- **Gadżety awatara za punkty rzucone w darcie**: 11 nowych elementów (czapki, okulary, efekty) odblokowywanych od 5 tys. do 200 tys. punktów (5 tys., 10 tys., 20 tys., 30 tys., 50 tys., 75 tys., 100 tys., 125 tys., 150 tys., 175 tys., 200 tys.).
- Profil i lista graczy w trybie darta pokazują tylko statystyki darta (bez ping ponga).
- **Around the Clock**: tryb wybierany na górze ustawień meczu. Trafiasz po kolei pola od 1 do 20, na końcu bull (25 albo 50). Każde trafienie w dane pole (pojedyncze, double, triple) to jeden krok, w kolejce są 3 rzuty, wygrywa pierwszy, kto trafi bull. Działa z botem, cofaniem, historią i tabelą Around the Clock (bilans, rekord w rzutach, celność). Mecze Around the Clock nie wchodzą do punktów darta, monet ani statystyk 301/501/701.
- **Gadżety za punkty rzucone w darcie**: 37 odblokowań od 2 500 do 200 000 punktów (kolory ciała, czapki i hełmy związane z rzutkami, dodatki, oczy, buzia, efekty). Kolejny gadżet i postęp widać w profilu gracza i w edytorze awatara.
- Mecze darta synchronizują się tak samo jak Ping Pong (nowa kolekcja `darts`).
