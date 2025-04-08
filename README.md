# Projekt: Sales analysis - analiza w Power BI

## 1. Opis projektu

Celem projektu było stworzenie interaktywnego raportu w Power BI służącego do analizy danych sprzedażowych firmy. Dane źródłowe obejmują informacje o transakcjach, produktach, klientach, sklepach oraz budżecie. Raport ma wspierać menedżerów w podejmowaniu decyzji poprzez:

- prezentację kluczowych wskaźników (KPI) dotyczących sprzedaży, kosztów i ilości,

- umożliwienie analizy danych z różnych perspektyw (czasowej, geograficznej, demograficznej),

- porównanie wyników rzeczywistych z planowanymi (budżet),

- identyfikację trendów i odchyleń (w tym analiza YoY),

- eksplorację danych przy użyciu drzewa dekompozycji.

Projekt zrealizowano zgodnie z najlepszymi praktykami modelowania danych w Power BI – z podziałem na tabele faktów i wymiarów, zastosowaniem miar w języku DAX oraz logicznym układem stron raportu.


## 2. Struktura raportu

- Sales Overview – zawiera kluczowe KPI takie jak: sprzedaż, koszty i ilość sprzedanych produktów. Dodatkowo umożliwia analizę wartości sprzedaży względem planu, subkategorii oraz trendów w czasie poprzez wykres liniowy.

- Customers – karta poświęcona analizie danych o klientach. Przedstawia ilość oraz wartość sprzedaży z podziałem na miasto pochodzenia oraz grupy wiekowe klientów.

- Decomposition Tree – wykorzystywana do szczegółowej analizy miar takich jak sprzedaż, ilość i koszty w ujęciu hierarchicznym, podobnie jak w szablonie wzorcowym.


## 3. Model danych

### Tabele:

Raport korzysta z danych zawartych w następujących tabelach:

- sales – główna tabela faktów zawierająca informacje o transakcjach (data, ID produktu, klienta, sklepu, ilość, wartość, koszt).

- products – tabela wymiarów z informacjami o produktach (kategoria, subkategoria, cena, koszt).

- customers – dane o klientach (miasto, wiek, segmentacja – Bins).

- budget – dane budżetowe zawierające planowaną sprzedaż per miesiąc.

- stores – informacje o sklepach (miasto, kod miasta).

- Calendar – tabela dat służąca do analizy czasowej.
  

### Struktura tabel:

W modelu zastosowano logiczne relacje:

- Transakcje (sales) są powiązane z tabelami wymiarów (products, customers, stores, Calendar) relacjami wiele do jednego.

  
## 4. Miary DAX

### Podstawowe miary:

W raporcie użyto szeregu miar stworzonych w tabeli _Measures, m.in.:

- Total Sales – suma wartości sprzedaży (SUMX(sales, sales[Quantity]*sales[Value]))

- Total Costs – suma kosztów (SUM(sales[Total_Cost]))

- Total Quantity – suma ilości (SUM(sales[Quantity]))

- Min Sales / Max Sales – odpowiednio minimalna i maksymalna wartość sprzedaży

- YoY – porównanie rok do roku dla sprzedaży, ilości, kosztów
      

## 5. Wizualizacje

Na poszczególnych kartach zastosowano następujące typy wizualizacji:

- KPI (wskaźniki sprzedaży, kosztów, ilości)

- wykresy liniowe (analiza trendu w czasie)

- tabele i macierze (porównanie względem planu, subkategorii)

- wykresy kolumnowe (segmentacja klientów)

- drzewo dekompozycji (Decomposition Tree) – umożliwia szczegółową analizę wybranej miary według wielu wymiarów (np. produkt, kategoria, klient)

  
## 6. Analiza szeregów czasowych

Dzięki połączeniu z tabelą dat (Calendar) możliwa jest analiza danych w różnych przekrojach czasowych:

- miesiąc, kwartał, rok

- analiza YoY (Year-over-Year) 

- filtrowanie i wizualizacja trendów za pomocą wykresów liniowych i wskaźników KPI
  
  
## 7. Segmentacja klientów

- Miasta – analiza geograficzna sprzedaży

- Grupy wiekowe (Age, Bins) – segmenty demograficzne Wizualizacje prezentują, które grupy klientów generują największe przychody oraz w jakich lokalizacjach sprzedaż jest najwyższa.
  

## 8. Instrukcja użytkowania raportu

- Raport jest interaktywny, umożliwiając użytkownikom dostosowanie widoków za pomocą dynamicznych filtrów.
- Użytkownicy mogą eksplorować dane na różne sposoby, aby uzyskać szczegółowe informacje na temat sprzedaży i podejmować świadome decyzje biznesowe.
- Model danych jest zbudowany w taki sposób, aby istniała możliwość dodawania kolejnych tabel wymiarów, w celu rozszerzenia analizy.

### Źródło danych:
Tabele faktów i wymiarów zostały wygenerowane za pomocą kody Python na podstawie zaprojektowanych założeń. Kod Python jest dostępny w repozytorium:
https://github.com/KatarzynaTondas/Python_script-Sample_data.git
