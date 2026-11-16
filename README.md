# sejm-network-analysis
# Sieciowa analiza dyscypliny klubowej w Sejmie RP (X Kadencja)

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![NetworkX](https://img.shields.io/badge/Library-NetworkX-orange.svg)](https://networkx.org/)
[![Gephi](https://img.shields.io/badge/Visualization-Gephi-brightgreen.svg)](https://gephi.org/)
[![API](https://img.shields.io/badge/Data-API%20Sejmu-red.svg)](https://api.sejm.gov.pl)

Projekt poświęcony ilościowemu badaniu polaryzacji, spójności partyjnej oraz przepływów głosów w Sejmie RP X kadencji (posiedzenia 20–35, okres październik 2024 – maj 2025). 

Wykorzystując **Analizę Sieci Społecznych (SNA)**, algorytmy detekcji społeczności (**Louvain**) oraz miary centralności strukturalnej, projekt weryfikuje hipotezę o niemal bezwzględnej dyscyplinie koalicyjno-partyjnej i marginalnym stopniu przekraczania linii podziału rząd–opozycja.

---

## Główne wnioski badawcze

1. Perfekcyjna spójność wewnątrzklubowa:
   Gęstość wewnętrzna dla niemal wszystkich klubów (KO, PiS, PSL-TD, Polska 2050, Lewica, Razem, Konfederacja) wyniosła **1.000**, co oznacza, że posłowie danego ugrupowania głosowali ze sobą zgodnie w co najmniej 80% wspólnych obecności.
   Jedynym wyjątkiem było koło Kukiz'15 (gęstość **0.833** – brak zaledwie jednej krawędzi na 10 możliwych).
2. Strukturalna izolacja bloków politycznych:
   Na 48 358 zidentyfikowanych powiązań w sieci zaledwie **242 krawędzie (poniżej 0.5%)** łączyły posłów koalicji rządzącej i opozycji.
   Średnia waga połączeń między blokami wynosi **0.991** – oznacza to, że nieliczne ponadpartyjne krawędzie dotyczyły bardzo specyficznych, powtarzalnych głosowań proceduralnych lub konsensualnych.
3. Wysoka modularność podziału:
   Algorytm Louvaina wykrył trzy główne klasy społeczności przy współczynniku modularności **$Q = 0.477$** (wartości > 0.4 wskazują na silną strukturę klastrową):
   **Klasa 1 (Koalicja rządząca):** KO, PSL-TD, Polska 2050-TD, Lewica, Razem.
   **Klasa 2 (Główna opozycja):** PiS oraz część posłów Kukiz'15.
   **Klasa 3 (Opozycja prawicowa):** Konfederacja oraz część posłów Kukiz'15.
4. **Pozycja partii Razem:**
   * Mimo braku wejścia do rządu, posłowie Razem strukturalnie zostali przyporządkowani do klastra koalicji rządzącej, choć zajmują pozycję peryferyjną w obrębie bloku (podobieństwo do pozycji Konfederacji wobec PiS).

---

## 📊 Kluczowe wizualizacje

| Podział według klubów parlamentarnych | Detekcja społeczności (Louvain, Q = 0.477) |
|:---:|:---:|
| ![Graf partii](assets/graf_partii.png) | ![Graf klas modułów](assets/graf_modulow.png) |
| *Węzły barwione wg klubów (KO, PiS, PSL, Polska 2050, Lewica, Razem, Konfederacja, Kukiz'15)* | *Społeczność 1: Koalicja + Razem \| Społeczność 2: PiS + Kukiz'15 \| Społeczność 3: Konfederacja* |

---

## ⚙️ Metodologia i etapy analizy

```text
[API Sejmu RP] 
      │ (991 głosowań, posiedzenia 20–35)
      ▼
[Filtrowanie kontrowersyjności] 
      │ (Odrzucenie głosowań ze zgodnością > 85%; pozostawiono 742 głosowania)
      ▼
[Konstrukcja macierzy podobieństwa] 
      │ (Minimalna liczba wspólnych głosowań = 10; próg podobieństwa Jaccard/Agreement = 0.80)
      ▼
[Graf relacji posłów (NetworkX)] 
      │ (461 węzłów, 48 358 krawędzi, gęstość = 0.458)
      ▼
[Analiza metryk SNA & Eksport GEXF] 
      │ (Louvain Modularity, Betweenness Centrality, Clustering Coefficient)
      ▼
[Wizualizacja przestrzenna w Gephi]
