![Zestawienie logotypów KPO, RP i UE](https://raw.githubusercontent.com/spatial-audio-lab/spatial-audio-lab.github.io/main/KPO.jpg)

# Sfera — odsłuch pola ambisonicznego

Odtwarzacz nagrań ambisonicznych z dekodowaniem binauralnym w przeglądarce. Obracasz
polem dźwiękowym wokół nieruchomej głowy, widzisz podpisane punkty źródeł na kuli
i czytasz opis sceny zapisany przez **Scenę**. Część zestawu narzędzi
**Spatial Audio Lab**.

**Na żywo:** https://spatial-audio-lab.github.io/ambi/

> Repozytorium nazywa się `ambi` z powodów historycznych; aplikacja nazywa się **Sfera**.
> Wcześniejsza nazwa („Ambisonic Web Player") wyszła z użycia.

## Co robi

- **Dekodowanie do binauralu** — FOA (4 kan.), HOA 2. rzędu (9 kan.) i 3. rzędu (16 kan.),
  biblioteka Omnitone ładowana z CDN z fallbackami. Pliki binauralne (2 kan.) odtwarza
  wprost, bez dekodera.
- **Rotacja pola** — suwaki yaw / pitch / roll, żyroskop urządzenia, tryb auto.
  Obraca się scena, nie słuchacz: w prawo znaczy w prawo.
- **Nazwane punkty na kuli** — po wczytaniu `_SCENA.json` ze Sceny każde źródło dostaje
  własny punkt pulsujący w rytm swojej głośności, z podpisem jadącym razem z punktem.
  Tryby podpisów: *Z przodu* / *Zawsze* / *Nigdy*.
- **Karta opisu sceny** — tytuł, opis, autor, licencja i data, jeśli zostały wpisane
  przy eksporcie. Pusty opis nie zabiera miejsca w kadrze.
- **Test orientacji** — impulsy szumu zakodowane kolejno na sześć kierunków. Jeśli
  słyszysz je tam, gdzie mówi napis, tor jest w porządku.
- **Miernik i limiter** — kontrola poziomu z sygnalizacją clippingu.
- **Sceny demonstracyjne** — pod przyciskiem *Demo* rozwija się lista gotowych scen
  z `assets/demo` (*Sansula*, *Chodzący zegar*). Każda wczytuje się razem ze swoim
  `_SCENA.json`, więc punkty na kuli zapalają się od razu.
- Ładowanie własnych plików (WAV / MP3 / OGG / Opus / FLAC / M4A / WebM) oraz archiwum
  `.zip` ze Sceny.
- **Wymagane słuchawki** — bez nich dekodowanie binauralne nie ma sensu.

## Wizualizacja

Amplituda pulsowania punktu zależy od rzędu pola: FOA opisuje całą sferę czterema
kanałami, więc kierunek jest najbardziej rozmyty i punkt oddycha najmocniej. Przy HOA
precyzję niesie samo pole, a puls jest spokojniejszy. Obwiednia z pliku (50 Hz) jest
wygładzana po stronie odtwarzacza filtrem z szybkim atakiem i wolnym opadaniem —
promieniowanie punktu płynie, zamiast migotać na transjentach. Format eksportu pozostaje
bez zmian, więc pliki wyeksportowane wcześniej działają tak samo.

## Współpraca ze Sceną

**Scena** (repozytorium `2D_Audio_Explorer`) eksportuje pięć plików: binauralny WAV,
AmbiX WAV, mapę JPG, metadane tekstowe i `_SCENA.json`. Sfera czyta AmbiX razem
z `_SCENA.json` — pierwszy niesie dźwięk, drugi nazwy, pozycje i obwiednie głośności.
AmbiX pierwszego rzędu brzmi nieco bardziej rozmyty kierunkowo niż binaural z tego
samego eksportu i **nie jest to błąd**: cztery kanały opisują całą sferę.

## System wizualny

Zgodny z **SAL Design Manifest v3.0**: baza neutralna (#0A0C08 / #12150F / #F0EBE0),
akcenty semantyczne — **cyan #00E5CC** (sygnał aktywny / fokus / playback),
**amber #FFAB00** (ambisonia / pole 3D / odczyt pozycji), **crimson #FF3355**
(stop / clipping / błąd). Typografia: Lexend + Azeret Mono. Dostępność: kontrast AA,
cele dotykowe ≥ 44 px, wartość liczbowa suwaka zawsze widoczna, widoczny fokus,
`prefers-reduced-motion`.

Górny pasek marki (ikona SAL, `← SAL`, dioda stanu, nazwa, opis) jest wspólny dla
wszystkich narzędzi laboratorium. Ikona ładuje się z `/assets/brand/` repozytorium
portalu — wszystkie aplikacje siedzą pod tym samym originem, więc jest jedno miejsce
aktualizacji i zero duplikatów binariów.

Transport: w ciszy przycisk odtwarzania ma ramkę cyan, w trakcie grania pełne wypełnienie,
a przycisk zatrzymania dostaje ramkę crimson, która po zatrzymaniu gaśnie do neutralnej.

**Świadome odstępstwo od manifestu:** kolor marki Hubu `--acid #BEFF00` występuje
w karcie opisu sceny. Uzasadnienie w komentarzu nad regułą CSS — trzy akcenty semantyczne
są zajęte przez warstwę pomiarową, a opis sceny należy do warstwy opisowej.

## Technologia

Pojedynczy plik `index.html`, bez kroku budowania. Omnitone + Three.js z CDN.
Własny dekoder WAV dla plików wielokanałowych, których `decodeAudioData` nie przyjmuje.

## Deploy (GitHub Pages)

Settings → Pages → Source: **Deploy from a branch** → `main` → `/ (root)`.
Plik `.nojekyll` zapewnia poprawne serwowanie katalogu `assets/`.


---


# O projekcie

[![Baner SAL](https://raw.githubusercontent.com/spatial-audio-lab/spatial-audio-lab.github.io/main/assets/brand/SAL_logo-wordmark.png)](https://spatial-audio-lab.github.io/)

## Spatial Audio Lab: archiwum VR dla edukacji teatralnej
„Spatial Audio Lab” to projekt stypendialny skupiony na tworzeniu profesjonalnego archiwum dźwięku przestrzennego. W ramach działań powstaje baza nagrań w technologii Virtual Reality (VR), która łączy nowoczesną inżynierię dźwięku z edukacją teatralną i technikami uważności (mindfulness).

[https://spatial-audio-lab.github.io/](https://spatial-audio-lab.github.io/)

---

## Finansowanie

![Zestawienie logotypów KPO, RP i UE](https://raw.githubusercontent.com/spatial-audio-lab/spatial-audio-lab.github.io/main/KPO.jpg)

## Informacja o finansowaniu

Projekt jest realizowany w ramach programu stypendialnego Krajowego Planu Odbudowy i Zwiększania Odporności (KPO).

- **Program:** Inwestycja A2.5.1: Program wspierania działalności podmiotów sektora kultury i przemysłów kreatywnych na rzecz stymulowania ich rozwoju.
- **Instytucja Wspierająca:** Narodowy Instytut Muzyki i Tańca (NIMiT).
- **Wartość dofinansowania z Unii Europejskiej (NextGenerationEU):** 36 000,00 zł brutto.
- Umowa nr **143/KPO.STYPENDIA/NIMIT/2025**.

## Licencja

MIT — patrz [LICENSE](LICENSE).


