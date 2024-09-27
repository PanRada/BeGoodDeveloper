## 1) Duża aktualizacja z podbiciem wersji major (aktualizacja przez sklepy)

### Tworzenie nowego tagu
W repozytorium GIT tworzony jest tag z wersją vX.0.0 (gdzie X oznacza nową wersję major).

### Build aplikacji
CI/CD wykrywa nowy tag, uruchamia pipeline do budowania aplikacji na iOS oraz Android. Tworzony jest nowy build dla każdej platformy z podbitą wersją major.

### Testy
Uruchomienie automatycznych testów jednostkowych, integracyjnych oraz testów UI na obu platformach.

### Wysłanie aplikacji do sklepów
Po sukcesie testów aplikacja zostaje automatycznie wypchnięta do App Store (iOS) oraz Google Play (Android) za pomocą odpowiednich narzędzi CI/CD (np. Fastlane). Po zakończeniu procesu oczekuje na review w sklepach.

### Publikacja
Po akceptacji przez sklepy nowa wersja zostaje udostępniona użytkownikom.

## 2) Mniejsze aktualizacje z podbiciem wersji minor (aktualizacja OTA)

### Tworzenie nowego tagu
W repozytorium GIT tworzony jest tag z wersją vX.Y.0 (gdzie Y oznacza nową wersję minor).

### Build kodu JS
CI/CD wykrywa nowy tag i uruchamia proces buildowania kodu JavaScript. Aplikacja nie wymaga pełnej kompilacji, ponieważ aktualizacja dotyczy tylko zmian w kodzie JS.

### Testy
Automatyczne testy jednostkowe oraz integracyjne na kodzie JavaScript.

### Wypuszczenie OTA
Po sukcesie testów kod zostaje wypchnięty za pomocą narzędzi OTA (np. Microsoft CodePush lub Expo OTA). Użytkownicy otrzymują aktualizację bez konieczności aktualizacji przez sklep.

## 3) Wykorzystanie tagów/release z wersją aplikacji w repozytorium GIT na gałęzi main

### Tag Major (vX.0.0)
Wykrycie tagu oznaczonego jako major wywołuje proces buildowania pełnej aplikacji na iOS i Android oraz wysyłania jej do sklepów. Proces budowania i wysyłania aplikacji do sklepów odbywa się automatycznie, z automatycznymi testami i raportowaniem.

### Tag Minor (vX.Y.0)
Wykrycie tagu oznaczonego jako minor uruchamia pipeline OTA. Budowany jest tylko kod JavaScript, który następnie jest wypychany do użytkowników za pomocą OTA.

### Tag Patch (vX.Y.Z)
W przypadku patcha (np. poprawki błędów) ten sam proces co dla minor jest uruchamiany, z tym że aktualizacja dotyczy tylko drobnych poprawek bez podbijania wersji minor.
