# 📑 Projekt analizy sprzedaży sieci kawiarni w Power BI

<div align="center">
  
  ### [📈 Zobacz interaktywny raport 📈](https://app.powerbi.com/view?r=eyJrIjoiMDJlNDM1NzAtNWZlMC00ZmQwLWI5OTMtMmU4YmMzYmRiM2FlIiwidCI6IjNkZmU5YWI2LTgxYmYtNDkxYy1iNjcwLTAxYzgyNGEwOWUxOSJ9)
  
</div>

<div align="center">
  
  ### Raport utworzony: 02.2025
  
</div>

### Problem biznesowy
Sieć kawiarni potrzebowała narzędzia do efektywnego śledzenia i porównywania wyników sprzedażowych w trzech lokalizacjach (Hell's Kitchen, Astoria, Lower Manhattan), ze szczególnym uwzględnieniem:
- Sezonowości sprzedaży
- Popularności produktów
- Wzorców zachowań klientów w różnych porach dnia i tygodnia

### Główne pytania analityczne
1. Jak kształtuje się sprzedaż w poszczególnych lokalizacjach i która z nich generuje najwyższe przychody?
2. Jakie produkty cieszą się największą popularnością i przynoszą najwyższe zyski?
3. Jakie są wzorce czasowe w sprzedaży (pory dnia, dni tygodnia, miesiące)?
4. Jakie trendy sprzedażowe można zaobserwować w ciągu analizowanego okresu?
5. Jakie są kluczowe wskaźniki efektywności dla poszczególnych lokalizacji?

## 💾 Źródła danych

### Opis danych
Głównym źródłem danych był plik Excel "Coffee Shop Sales.xlsx" zawierający szczegółowe informacje o transakcjach sprzedażowych w trzech kawiarniach za okres sześciu miesięcy, zawierający:

- transaction_id
- transaction_date
- transaction_time
- transaction_qty
- store_id
- store_location
- product_id
- unit_price
- product_category
- product_type
- product_detail

### Sposób pozyskania danych
Dane zostały zaimportowane z pliku Excel przy użyciu Power Query w celu odpowiedniego przygotowania danych przed modelowaniem.

## 🔄 Proces przygotowania danych

### Transformacje w Power Query
1. **Czyszczenie danych**:
   - Standaryzacja nazw lokalizacji i produktów
   - Usunięcie duplikatów rekordów
   - Obsługa brakujących wartości
   - Konwersja typów danych

2. **Tworzenie dodatkowych kolumn**:
   - Wyodrębnienie atrybutów czasu z dat transakcji (godzina, dzień tygodnia, miesiąc, kwartał)

### Model danych
Model zawiera następujące tabele:

####  Calendar (tabela wymiarów)
- Date, Day, Day_name
- Month, month_name
- Number_day_of_the_week
- Quarter, Week Segment, Year

####  Transactions (tabela faktów)
- Date, Full hours, Month
- Location
- Product_Category, Product_Category [group], Product_Detail, Product_ID, Product_Type
- Quantity_of_Items
- Store_ID, Time, Transaction_ID, Unit_Price

####  Store (tabela wymiarów)
- Location, Store_ID

####  Hours (tabela wymiarów)
- Hour, Time Interval

Model wykorzystuje schemat gwiazdy dla optymalnej wydajności zapytań i łatwości tworzenia miar.

## 📈 Wizualizacje i analizy

### Struktura raportu
Raport składa się z 5 głównych stron:

1. **Landing Page** - strona nawigacyjna z logo i przyciskami
2. **Overview** - kluczowe wskaźniki, trendy sprzedaży miesięcznej i podział sprzedaży
3. **Sales by Location** - szczegółowa analiza każdej z trzech kawiarni
4. **Product Analysis** - popularność kategorii i typów produktów, rozmiary porcji
5. **Time Analysis** - wzorce sprzedaży w różnych porach dnia i dniach tygodnia

### Kluczowe wizualizacje

####  Karty z miernikami KPI
- Całkowita sprzedaż: $699 tys.
- Średnia miesięczna liczba transakcji: 25 tys.
- Średnia dzienna liczba transakcji: 824
- Średnia wartość transakcji na klienta: $4,69

####  Wykresy
- Wykres liniowy trendów sprzedaży miesięcznej
- Wykresy słupkowe porównujące sprzedaż między lokalizacjami
- Wykres kołowy podziału sprzedaży według lokalizacji
- Mapa drzewa kategorii produktów
- Wykres słupkowy dynamiki sprzedaży miesiąc do miesiąca
- Wykresy godzinowe i dzienne rozkładu sprzedaży

####  Tabele
- Sprzedaż według kategorii produktów i lokalizacji
- Typy produktów z ilościami, średnimi cenami i całkowitą sprzedażą

### Interaktywność
- Filtry na wszystkich stronach (kwartał, miesiąc)
- Filtry na wybranych stronach (lokalizacja)
- Przycisk "Clear All Slicers" 
- Cross-filtering między wizualizacjami
- Dynamiczne wyświetlanie danych zależnie od wybranych filtrów

## 💡 Wnioski i rekomendacje

### Kluczowe obserwacje

####  Lokalizacje
Sprzedaż jest dość równomiernie rozłożona:
- Hell's Kitchen: $237 tys. (33,84%)
- Astoria: $232 tys. (33,23%)
- Lower Manhattan: $230 tys. (32,92%)

####  Produkty
- Kategoria kawy dominuje w sprzedaży (38,63%, $270 tys.)
- Następnie herbata (28,11%, $196 tys.)
- Najpopularniejsze typy: Barista Espresso ($91,4 tys.) i Brewed Chai tea ($77 tys.)

####  Dynamika czasowa
- Wyraźny trend wzrostowy sprzedaży miesięcznej
- Średnia sprzedaż w dni robocze jest nieznacznie wyższa niż w weekendy
- Poranne godziny (przed 11:00) są niemal równie dochodowe ($342 tys.) co popołudniowe i wieczorne ($357 tys.)

####  Zachowania klientów
- Najwyższa średnia wartość transakcji: Lower Manhattan ($4,81)
- Najniższa średnia liczba transakcji dziennie: Lower Manhattan (264 vs 280 w innych lokalizacjach)

### Rekomendacje

####  Optymalizacja oferty produktowej
- Rozszerzenie oferty najpopularniejszych produktów
- Wprowadzenie promocji na mniej popularne kategorie

####  Strategia dla lokalizacji
- Hell's Kitchen: koncentracja na sprzedaży ziaren kawy
- Lower Manhattan: strategia zwiększenia liczby klientów

####  Optymalizacja według czasu
- Wprowadzenie specjalnych ofert weekendowych
- Optymalizacja liczby personelu (więcej do 11:00, mniej później)

####  Rozwój biznesu
- Rozszerzenie oferty produktów o najwyższej marży
- Program lojalnościowy w celu zwiększenia częstotliwości wizyt

## ⚙️ Aspekty techniczne

### Zastosowane funkcje DAX

```dax
Total Sales = CALCULATE(SUMX(Transactions, Transactions[Quantity_of_items]*Transactions[Unit_Price]))

Average Transaction per Customer = DIVIDE([Total sales], COUNT(Transactions[Transaction_ID]),0)

Average Daily Number of Transactions = 
	VAR NR_of_transaction =
    		COUNTROWS ( Transactions )
	VAR Day_count =
    		DATEDIFF ( MIN ( Transactions[Date] ), MAX ( Transactions[Date] ), DAY ) + 1
	VAR Final =
    		COALESCE ( DIVIDE ( Nr_of_transaction, Day_count, 0 ), 0 )
	RETURN
		Final
```

### Optymalizacja wydajności
1. Filtrowanie na poziomie zapytania
2. Implementacja schematu gwiazdy
3. Tworzenie miar pomocniczych
4. Efektywne wykorzystanie kontekstu filtra

## 📝 Podsumowanie

Projekt dostarcza kompleksowej analizy działalności sieci trzech kawiarni, umożliwiając podejmowanie decyzji biznesowych opartych na danych. Dzięki interaktywnym wizualizacjom i możliwości drążenia danych, raport stanowi skuteczne narzędzie do monitorowania KPI i identyfikacji obszarów wymagających optymalizacji.

Analiza ujawnia równomierne rozłożenie sprzedaży między lokalizacjami z niewielką przewagą Hell's Kitchen, dominację kategorii kawy w strukturze sprzedaży oraz wyraźne wzorce czasowe. Rekomendacje dotyczące optymalizacji oferty produktowej, strategii dla poszczególnych lokalizacji oraz działań marketingowych mogą przyczynić się do dalszego wzrostu sprzedaży i poprawy efektywności operacyjnej.
