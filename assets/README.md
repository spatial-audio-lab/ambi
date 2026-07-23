# Ambisonic Web Player — Spatial Audio Lab

Odtwarzacz dźwięku ambisonicznego (FOA / B-Format AmbiX, 4 kanały) z dekodowaniem
binauralnym w przeglądarce i sterowaniem rotacją pola dźwiękowego (yaw / pitch / roll,
opcjonalnie żyroskop urządzenia). Część zestawu narzędzi **Spatial Audio Lab**.

**Na żywo:** https://spatial-audio-lab.github.io/ambi/

## Funkcje
- Dekodowanie FOA → binauralne (biblioteka Omnitone, ładowana z CDN z fallbackami).
- Sterowanie rotacją: ręczne suwaki, żyroskop, tryb auto.
- Wizualizacja pozycji słuchacza w polu dźwiękowym.
- Wbudowane demo (`pociag.opus`) + ładowanie własnych plików (WAV/MP3/OGG/Opus/FLAC/M4A).
- **Wymagane słuchawki** — dźwięk przestrzenny (binauralny).

## System wizualny
Zgodny z **SAL Design Manifest v3.0**: baza neutralna (#0A0C08 / #12150F / #F0EBE0),
akcenty semantyczne — **cyan #00E5CC** (kontrolki / fokus / playback), **amber #FFAB00**
(pole 3D / ambisonia / ostrzeżenia), **crimson #FF3355** (błąd / clipping). Kolor marki
Huba (acid #BEFF00) występuje wyłącznie w pasku nawigacji. Typografia: Lexend + Azeret Mono.
Dostępność: kontrast AA, cele dotykowe ≥44px, wartość liczbowa suwaka zawsze widoczna,
widoczny fokus, `prefers-reduced-motion`.

## Technologia
Pojedynczy plik `index.html` (bez kroku budowania). Omnitone + Three.js z CDN.
Zasoby marki i style są wbudowane / lokalne — aplikacja jest samodzielna.

## Deploy (GitHub Pages)
Settings → Pages → Source: **Deploy from a branch** → `main` → `/ (root)`.
Plik `.nojekyll` zapewnia poprawne serwowanie katalogu `assets/`.

## Licencja
MIT — patrz [LICENSE](LICENSE).
