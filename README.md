# PCB INLET

Dwuwarstwowa płytka wejściowa zasilania sieciowego dla projektu Custom Step-Down PSU 230 V → 100 V.

## Stan projektu

Rewizja PCB: `PCB1-PCB-01R1`

Główny plik płytki:

`pcb-inlet.kicad_pcb`

Układ elektryczny, geometria płytki i trasowanie nie zostały zmienione. Ujednolicono nazwę pliku, strukturę repozytorium oraz automatyczne testy GitHub Actions.

## Parametry PCB

| Parametr | Wartość |
|---|---:|
| Wymiary | 105 × 70 mm |
| Liczba warstw miedzi | 2 |
| Materiał | FR-4 |
| Grubość laminatu | 1,6 mm |
| Grubość miedzi | 70 µm / 2 oz |
| Montaż elementów | THT |
| Liczba footprintów | 10 |
| Liczba przelotek | 0 |
| Otwory montażowe | 4 × 3,2 mm, NPTH, M3 |

## Funkcje płytki

Płytka zawiera:

- wejście i wyjście sieciowe na złączach śrubowych,
- bezpiecznik topikowy w przewodzie fazowym,
- warystor zabezpieczający,
- kondensator klasy X2,
- rezystor rozładowujący,
- sieci `L_IN`, `L_FUSED` i `N_IN`,
- cztery otwory montażowe M3.

## Struktura repozytorium

Najważniejsze pliki:

- `pcb-inlet.kicad_pcb` — projekt płytki KiCad,
- `.github/workflows/kicad-validate.yml` — automatyczna kontrola DRC,
- `.github/workflows/kicad-manufacturing.yml` — generowanie plików produkcyjnych,
- `.gitignore` — wykluczenie plików generowanych automatycznie,
- `README.md` — opis projektu.

## Automatyczna walidacja

Workflow `kicad-validate.yml` uruchamia się przy Pull Requestach oraz zmianach na głównej gałęzi.

Walidacja:

1. uruchamia KiCad CLI 8.0.9,
2. otwiera plik PCB,
3. wykonuje pełny raport DRC,
4. wykonuje kontrolę błędów blokujących,
5. zapisuje raporty jako artifact GitHub Actions.

Aktualny wynik kontroli bramkującej:

- 0 błędów,
- 0 niepołączonych padów.

Pełny raport może zawierać ostrzeżenia i naruszenia informacyjne wymagające ręcznej oceny.

## Pliki produkcyjne

Workflow `kicad-manufacturing.yml` jest przeznaczony do automatycznego generowania:

- warstw Gerber,
- plików wierceń,
- map wierceń,
- pliku IPC-D-356,
- raportów DRC,
- manifestu plików,
- sum kontrolnych SHA-256.

Pliki produkcyjne nie są zapisywane bezpośrednio w repozytorium. Są udostępniane w GitHub Actions jako artifact do pobrania.

## Zalecane parametry zamówienia PCB

- 2 warstwy,
- wymiary 105 × 70 mm,
- materiał FR-4,
- grubość 1,6 mm,
- miedź 2 oz,
- solder mask po obu stronach,
- opis po obu stronach,
- bez panelizacji,
- bez kontrolowanej impedancji,
- bez V-score,
- bez metalizacji krawędzi,
- bez otworów castellated.

## Bezpieczeństwo

Projekt pracuje z napięciem sieciowym.

Przed wykonaniem i uruchomieniem płytki należy sprawdzić:

- wymagane odstępy izolacyjne,
- parametry napięciowe i prądowe elementów,
- klasę bezpieczeństwa kondensatora,
- właściwy dobór bezpiecznika,
- sposób uziemienia urządzenia,
- zgodność konstrukcji z obowiązującymi wymaganiami bezpieczeństwa.

Uruchamianie układu powinno odbywać się wyłącznie przez osobę posiadającą odpowiednie doświadczenie z urządzeniami sieciowymi.