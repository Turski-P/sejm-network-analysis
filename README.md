# sejm-network-analysis

Ilościowa analiza dyscypliny klubowej i głosowań w Sejmie RP. Projekt łączy dane z API Sejmu, analizę sieci społecznych (SNA) oraz, w kolejnych etapach, klasyfikację tematyczną głosowań metodami NLP.

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![NetworkX](https://img.shields.io/badge/Library-NetworkX-orange.svg)](https://networkx.org/)
[![Gephi](https://img.shields.io/badge/Visualization-Gephi-brightgreen.svg)](https://gephi.org/)
[![API](https://img.shields.io/badge/Data-API%20Sejmu-red.svg)](https://api.sejm.gov.pl)

Status: w przebudowie. Etap 1 (notebooki) jest zakończony i oznaczony tagiem `v1-notebooks`. Etap 2 (infrastruktura danych i NLP) jest w toku na gałęzi `refactor/infrastructure`.

## Cel badawczy

Główne pytanie: jak silna jest dyscyplina klubowa w Sejmie i czy zależy od tematu głosowania. Pytania szczegółowe:

1. Jak mierzyć dyscyplinę w sposób, który różnicuje kluby i tematy (a nie osiąga sufitu)?
2. Czy dyscyplina i przekraczanie linii podziału rząd-opozycja różnią się między obszarami polityk publicznych?
3. Jak zmienia się struktura sieci posłów w czasie i między kadencjami?
4. (Plan odległy) Czy treść debaty, widoczna w stenogramach, wyjaśnia odstępstwa od dyscypliny?

## Etapy projektu

### Etap 1: analiza sieciowa (zakończony)

Sieć posłów X kadencji na podstawie posiedzeń 20-35 (991 głosowań, 742 po filtrze kontrowersyjności). Graf: 461 węzłów, 48 358 krawędzi, modularność Louvaina Q = 0.477. Szczegóły i wnioski w [docs/stage1_results.md](docs/stage1_results.md), kod w `notebooks/legacy/`.

Uwaga metodologiczna: gęstość wewnątrzklubowa przy progu zgodności 0.80 osiąga wartość 1.000 dla większości klubów, więc w etapie 2 jest uzupełniana miarami ciągłymi.

### Etap 2: infrastruktura danych (w toku)

Przyrostowe pobieranie pełnych odpowiedzi API do `data/raw/`, znormalizowana baza (SQLite lub DuckDB), konfiguracja przez `config.yaml`. Schemat bazy w [docs/schema.md](docs/schema.md).

### Etap 3: klasyfikacja tematyczna (planowany)

Przypisanie każdemu głosowaniu kategorii tematycznej (kandydat: schemat Comparative Agendas Project), z etykietami zapisywanymi w osobnej tabeli wraz z metodą i wersją modelu. Walidacja na ręcznie oznaczonej próbie (accuracy, kappa Cohena). Opis w [docs/taxonomy.md](docs/taxonomy.md).

### Etap 4: dyscyplina według kategorii (planowany)

Miary ciągłe (indeks Rice'a, średnia zgodność par w klubie) agregowane po kategoriach z przedziałami ufności, sieci tematyczne i porównanie modularności.

### Etap 5: transkrypcje (plan odległy)

Połączenie głosowań ze stenogramami przez numery druków.

## Struktura repozytorium

```text
sejm-network-analysis/
  src/
    collect.py       pobieranie przyrostowe z API do data/raw/
    build_db.py      data/raw/ -> baza znormalizowana
    classify.py      klasyfikacja tematyczna -> tabela labels
    network.py       budowa grafów i metryki
  notebooks/
    legacy/          notebooki z etapu 1
  tests/
    fixtures/        małe próbki danych do testów
  docs/              schemat bazy, taksonomia, metodologia, wyniki etapu 1
  assets/            wizualizacje do README
  results/           wyniki gotowe do publikacji
  config.yaml        kadencja, zakres posiedzeń, progi, schemat kategorii
  requirements.txt
```

Dane (`data/`, pliki baz, CSV, GEXF) nie są wersjonowane w gicie i są odtwarzane skryptami.

## Instalacja i uruchomienie

```bash
git clone https://github.com/<uzytkownik>/sejm-network-analysis.git
cd sejm-network-analysis
python -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Planowany przepływ pracy (po zakończeniu etapu 2):

```bash
python -m src.collect --term 10        # pobiera tylko brakujące głosowania
python -m src.build_db                 # buduje lub aktualizuje bazę
python -m src.classify --scheme cap    # etykiety tematyczne
python -m src.network --config config.yaml
```

Dla klasyfikacji z użyciem LLM klucz API ustaw w pliku `.env` (nie jest śledzony przez git).

## Dane

Źródło: [API Sejmu RP](https://api.sejm.gov.pl). Dane są jawne, ale warto sprawdzić warunki ponownego wykorzystania przed publikacją pochodnych zbiorów. Surowe odpowiedzi API są zapisywane w niezmienionej postaci, a wszystkie przekształcenia dzieją się w kolejnych warstwach (znormalizowana baza, etykiety, wyniki).

## Metodologia

Opis miar, progów, obsługi nieobecnych i wstrzymujących się oraz walidacji klasyfikacji w [docs/methodology.md](docs/methodology.md). Parametry każdej analizy są zapisywane razem z wynikami, aby wykresy dało się odtworzyć.

## Wizualizacje z etapu 1

| Podział według klubów parlamentarnych | Detekcja społeczności (Louvain, Q = 0.477) |
|:---:|:---:|
| ![Graf partii](assets/graf_partii.png) | ![Graf klas modułów](assets/graf_modulow.png) |

## Plan prac

- [ ] Pobieranie przyrostowe pełnych JSON-ów
- [ ] Schemat bazy i budowa bazy
- [ ] Pobranie druków i powiązanie z głosowaniami
- [ ] Taksonomia i klasyfikacja tematyczna
- [ ] Walidacja ręczna (100-150 głosowań)
- [ ] Miary dyscypliny według kategorii
- [ ] Przepisanie analizy sieciowej na zapytania do bazy
- [ ] Rozszerzenie na wcześniejsze kadencje
- [ ] Transkrypcje

## Licencja

Do uzupełnienia (np. MIT dla kodu).

## Autor

Do uzupełnienia
