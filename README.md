# Moozg — instalatory i kanał aktualizacji

To repozytorium zawiera wyłącznie gotowe pliki instalacyjne Moozg, ich podpisy i sumy kontrolne oraz manifest kanału aktualizacji `pilot.json`. Kod źródłowy aplikacji jest prywatny i nie znajduje się tutaj.

Moozg to edukacyjna aplikacja do eksploracji zależności między strukturami mózgu, funkcjami psychicznymi, zaburzeniami, substancjami i ciałem. Nie jest narzędziem diagnostycznym ani medycznym. Do uruchomienia potrzebny jest indywidualny kod licencyjny od autora; pobranie instalatora go nie zastępuje.

## Wersja 0.1.2 (pilotaż)

- **Mac z procesorem Apple Silicon (M1 i nowsze), macOS 11 lub nowszy:** [Moozg_0.1.2_aarch64.dmg](https://github.com/patrygu/moozg-updates/releases/download/v0.1.2/Moozg_0.1.2_aarch64.dmg)
- **Windows 10 lub 11, 64-bit:** [Moozg_0.1.2_x64-setup.exe](https://github.com/patrygu/moozg-updates/releases/download/v0.1.2/Moozg_0.1.2_x64-setup.exe)
- [Informacje o wydaniu i sumy kontrolne](https://github.com/patrygu/moozg-updates/releases/tag/v0.1.2)

Mac z procesorem Intel, Windows na ARM i Linux nie są objęte tą wersją.

**Stan sprawdzenia (12 listopada 2026):**

- macOS: sprawdzono podpis aplikacji dla Apple Silicon, podpis paczki aktualizacji i sumę obrazu DMG. Instalacja aktualizacji z 0.1.1 na komputerze testera pozostaje do sprawdzenia.
- Windows: instalator zbudowano i zainstalowano automatycznie na czystym Windows Server 2025 x64 (GitHub Actions), a zainstalowana aplikacja uruchomiła się do ekranu aktywacji. Ręczny odbiór na komputerze z Windows 10/11 (aktywacja, model 3D, zapis danych, ostrzeżenia systemu) jeszcze trwa.

## Instalacja

### Mac

1. Pobierz i otwórz `.dmg`.
2. Przeciągnij Moozg do folderu Programy.
3. Wysuń obraz dysku i uruchom Moozg z Programów.

Wersja pilotażowa nie ma notaryzacji Apple (podpis ad hoc). Jeśli macOS zablokuje pierwsze otwarcie, a plik pochodzi z tego wydania i ma zgodną sumę, otwórz Ustawienia systemowe → Prywatność i ochrona i wybierz „Otwórz mimo to” dla Moozg. Nie wyłączaj zabezpieczeń całego systemu. Jeśli tej opcji nie ma albo pojawia się inny komunikat, zgłoś go autorowi.

Przy zgodzie na dostęp Moozg do jego wpisu w pęku kluczy hasło wpisujesz wyłącznie w oknie macOS. Po aktualizacji aplikacja może poprosić o tę zgodę ponownie.

### Windows

1. Pobierz `Moozg_0.1.2_x64-setup.exe` i uruchom instalator.
2. Zainstaluj dla swojego użytkownika (uprawnienia administratora nie są potrzebne) i uruchom Moozg ze skrótu.
3. Jeśli w systemie brakuje Microsoft Edge WebView2, instalator pobierze ten komponent.

Instalator nie ma podpisu wydawcy Windows (Authenticode). SmartScreen może pokazać ostrzeżenie „System Windows ochronił ten komputer”; po sprawdzeniu nazwy pliku i sumy możesz wybrać „Więcej informacji” → „Uruchom mimo to”. Przy włączonym Smart App Control system może całkiem zablokować instalator; wtedy skontaktuj się z autorem. Nie wyłączaj Defendera, Smart App Control ani antywirusa.

### Pierwsze uruchomienie

Wklej kod otrzymany osobno od autora i wybierz „Aktywuj”. Pierwsza aktywacja wymaga internetu. Kod przypisuje dostęp do jednej instalacji, więc nie udostępniaj go innym osobom. Kolejne uruchomienia nie wymagają kodu.

Przejście z Moozg 0.1.1 na 0.1.2 wymaga ręcznej instalacji z linków powyżej. Aktualizator w 0.1.1 zatrzymuje pobieranie na przekierowaniu GitHuba. Zamknij aplikację przed instalacją i zastąp poprzednią kopię w Programach na Macu albo uruchom instalator na Windows. Zgłaszając błąd, podaj wersję Moozg, system, co kliknięto i treść komunikatu; nie przesyłaj kodu licencyjnego, haseł ani prywatnych notatek.

## Sumy i podpisy

`SHA256SUMS` w wydaniu zawiera sumy SHA-256 wszystkich plików. Sprawdzenie:

- macOS: `shasum -a 256 Moozg_0.1.2_aarch64.dmg`
- Windows (PowerShell): `Get-FileHash .\Moozg_0.1.2_x64-setup.exe -Algorithm SHA256`

Pliki `.sig` to podpisy minisign kanału aktualizacji, sprawdzane przez aplikację kluczem wbudowanym w Moozg (identyfikator `0347359288D642DE`). Nie są podpisem systemowym Apple ani Microsoft i nie usuwają ostrzeżeń Gatekeepera lub SmartScreen.

`pilot.json` na gałęzi `main` to manifest, z którego zainstalowane aplikacje odczytują dostępną wersję.

## Licencje

Kod aplikacji: MIT. Treść edukacyjna: CC BY-SA 4.0. Modele i dane zewnętrzne (BodyParts3D, TotalSegmentator, atlas CIT168 i inne) zachowują własne licencje opisane w pliku `licenses/ATTRIBUTION.md` w zainstalowanej aplikacji, razem z licencjami komponentów (`THIRD_PARTY_LICENSES.txt`).

Visible Human Female CT: Courtesy of the U.S. National Library of Medicine. NLM does not endorse Moozg.

**Portrety przypadków klinicznych** (15 ilustracji fikcyjnych postaci w 0.1.2) zostały wygenerowane narzędziem OpenAI image_gen na potrzeby Moozg w 2026 roku. Portrety nie są objęte licencją kodu (MIT) ani treści (CC BY-SA 4.0) i nie otrzymały żadnej innej otwartej licencji. Nie ma gwarancji wyłączności wizerunku ani braku przypadkowego podobieństwa do prawdziwej osoby. Zdanie w dołączonym do aplikacji `ATTRIBUTION.md`, że licencja portretów czeka na decyzję właściciela przed publicznym wydaniem, odzwierciedla stan sprzed publikacji wydania.
