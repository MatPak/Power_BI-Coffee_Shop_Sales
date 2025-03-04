Link do projektu 👉 https://app.powerbi.com/view?r=eyJrIjoiMDJlNDM1NzAtNWZlMC00ZmQwLWI5OTMtMmU4YmMzYmRiM2FlIiwidCI6IjNkZmU5YWI2LTgxYmYtNDkxYy1iNjcwLTAxYzgyNGEwOWUxOSJ9
1. Opis projektu
Cel biznesowy
	Projekt miał na celu stworzenie interaktywnego raportu analitycznego dla sieci trzech kawiarni, który umożliwiłby kierownictwu monitorowanie wyników sprzedażowych, 						 
	identyfikację trendów oraz podejmowanie świadomych decyzji biznesowych. Raport został zaprojektowany, aby dostarczyć kompleksową analizę pod względem lokalizacji, czasu oraz 		struktury sprzedaży produktów.
Problem biznesowy
	Sieć kawiarni potrzebowała narzędzia do efektywnego śledzenia i porównywania wyników sprzedażowych w trzech lokalizacjach (Hell's Kitchen, Astoria, Lower Manhattan), ze 					szczególnym uwzględnieniem sezonowości sprzedaży, popularności produktów i wzorców zachowań klientów w różnych porach dnia i tygodnia.
Główne pytania analityczne
	1.	Jak kształtuje się sprzedaż w poszczególnych lokalizacjach i która z nich generuje najwyższe przychody?
	2.	Jakie produkty cieszą się największą popularnością i przynoszą najwyższe zyski?
	3.	Jakie są wzorce czasowe w sprzedaży (pory dnia, dni tygodnia, miesiące)?
	4.	Jakie trendy sprzedażowe można zaobserwować w ciągu analizowanego okresu?
	5.	Jakie są kluczowe wskaźniki efektywności dla poszczególnych lokalizacji?
2. Źródła danych
Opis danych
	Głównym źródłem danych był plik Excel "Coffee Shop Sales.xlsx", zawierający szczegółowe informacje o transakcjach sprzedażowych w trzech kawiarniach. Dane obejmowały sześć 			miesięcy operacji z informacjami o:
		•	transaction_id
		•	transaction_date
		•	transaction_time
		•	transaction_qty
		•	store_id
		•	store_location
		•	product_id
		•	unit_price
		•	product_category
		•	product_type
		•	product_detail
Sposób pozyskania danych
	Dane zostały zaimportowane z pliku Excel przy użyciu Power Query w celu odpowiedniego przygotowania danych przed modelowaniem.
3. Proces przygotowania danych
	Transformacje w Power Query
		1.	Czyszczenie danych:
			o	Standaryzacja nazw lokalizacji i produktów
			o	Usunięcie duplikatów rekordów
			o	Obsługa brakujących wartości w danych liczbowych
			o	Konwersja typów danych do odpowiednich formatów (daty, liczby, tekst)
		2.	Tworzenie dodatkowych kolumn:
			o	Wyodrębnienie atrybutów czasu z dat transakcji (godzina, dzień tygodnia, miesiąc, kwartał)
	Model danych
	Model danych zawiera następujące tabele:
		•	Calendar - tabela wymiarów zawierająca:
			o	Date 
			o	Day 
			o	Day_name 
			o	Month 
			o	month_name 
			o	Number_day_of_the_week 
			o	Quarter 
			o	Week Segment
			o	Year 
		•	Transactions - tabela faktów zawierająca:
			o	Date 
			o	Full hours 
			o	Month 
			o	Location 
			o	Product_Category 
			o	Product_Category [group] 
			o	Product_Detail 
			o	Product_ID 
			o	Product_Type
			o	Quantity_of_Items 
			o	Store_ID 
			o	Time 
			o	Transaction_ID 
			o	Unit_Price 
		•	Store  - tabela wymiarów zawierająca:
			o	Location 
			o	Store_ID 
		•	Hours  - tabela wymiarów zawierająca:
			o	Hour 
			o	Time Interval 
	Relacje między tabelami zostały ustanowione w oparciu o klucze obce, tworząc schemat gwiazdy dla optymalnej wydajności zapytań i łatwości tworzenia miar:
			•	Tabela Calendar połączona z tabelą Transactions przez pole Date
			•	Tabela Store połączona z tabelą Transactions przez pole Store_ID
			•	Tabela Hours połączona z tabelą Transactions przez pole Hour
4. Wizualizacje i analizy
	Struktura raportu
	Raport składa się z 5 głównych stron:
		1.	Landing Page - strona nawigacyjna z logo i przyciskami do innych sekcji
		2.	Overview - kluczowe wskaźniki, trendy sprzedaży miesięcznej i podział sprzedaży
		3.	Sales by Location - szczegółowa analiza każdej z trzech kawiarni
		4.	Product Analysis - popularność kategorii i typów produktów, rozmiary porcji
		5.	Time Analysis - wzorce sprzedaży w różnych porach dnia i dniach tygodnia
	Kluczowe wizualizacje
		1.	Karty z miernikami KPI:
			o	Całkowita sprzedaż: $699 tys.
			o	Średnia miesięczna liczba transakcji: 25 tys.
			o	Średnia dzienna liczba transakcji: 824
			o	Średnia wartość transakcji na klienta: $4,69
		2.	Wykresy:
			o	Wykres liniowy trendów sprzedaży miesięcznej
			o	Wykresy słupkowe do porównania sprzedaży między lokalizacjami
			o	Wykres kołowy podziału sprzedaży według lokalizacji
			o	Mapa drzewa kategorii produktów
			o	Wykres słupkowy dynamiki sprzedaży miesiąc do miesiąca
			o	Wykresy godzinowe i dzienne rozkładu sprzedaży
		3.	Tabele:
			o	Tabela sprzedaży według kategorii produktów i lokalizacji
			o	Tabela typów produktów z ilościami, średnimi cenami i całkowitą sprzedażą
	Interaktywność
	Raport zawiera szereg elementów interaktywnych:
		•	Filtry na wszystkich stronach umożliwiające filtrowanie według kwartału i miesiąca
		•	Filtry na wybranych stronach umożliwiające filtrowanie według lokalizacji
		•	Przycisk "Clear All Slicers" do szybkiego resetowania filtrów
		•	Cross-filtering między wizualizacjami
		•	Dynamiczne wyświetlanie danych w zależności od wybranych filtrów
5. Wnioski i rekomendacje biznesowe
	Kluczowe obserwacje
		1.	Lokalizacje: Sprzedaż jest dość równomiernie rozłożona między trzema lokalizacjami, z Hell's Kitchen prowadzącym nieznacznie ($237 tys., 33,84%), następnie Astoria ($232 		tys., 33,23%) i Lower Manhattan ($230 tys., 32,92%).
		2.	Produkty:
			o	Kategoria kawy dominuje w sprzedaży (38,63%, $270 tys.), następnie herbata (28,11%, $196 tys.)
			o	Najpopularniejsze typy produktów to Barista Espresso ($91,4 tys.) i Brewed Chai tea ($77 tys.)
		3.	Dynamika czasowa:
			o	Zaobserwowano wyraźny trend wzrostowy sprzedaży miesięcznej
			o	Średnia sprzedaż w dni robocze jest nieznacznie wyższa niż w dni weekendowe
			o	Poranne godziny (przed 11:00) są niemal równie dochodowe ($342 tys.) co popołudniowe i wieczorne ($357 tys.)
		4.	Zachowania klientów:
			o	Średnia wartość transakcji jest najwyższa w Lower Manhattan ($4,81)
			o	Lower Manhattan ma najniższą średnią liczbę transakcji dziennie (264) w porównaniu do pozostałych lokalizacji (280)
	Rekomendacje
		1.	Optymalizacja oferty produktowej:
			o	Rozszerzenie oferty najpopularniejszych produktów (Barista Espresso i Brewed Chai tea)
			o	Wprowadzenie promocji na mniej popularne kategorie w celu zwiększenia ich sprzedaży
		2.	Strategia dla lokalizacji:
			o	W Hell's Kitchen warto skoncentrować się na sprzedaży ziaren kawy (najwyższa sprzedaż w tej kategorii)
			o	W Lower Manhattan można rozważyć strategię zwiększenia liczby klientów, utrzymując wysoką średnią wartość transakcji
		3.	Optymalizacja według czasu:
			o	Wprowadzenie specjalnych ofert weekendowych w celu zwiększenia ruchu w te dni
			o	Zwiększenie liczby personelu do godziny 11, przy jednoczesnym ograniczeniu obsady w późniejszych godzinach
		4.	Rozwój biznesu:
			o	Kontynuacja trendu wzrostowego sprzedaży poprzez rozszerzenie oferty produktów o najwyższej marży
			o	Rozważenie programu lojalnościowego w celu zwiększenia częstotliwości wizyt klientów
6. Aspekty techniczne
	Zastosowane funkcje DAX
	W raporcie wykorzystano liczne miary DAX, w tym:
		•	Total Sales = CALCULATE(SUMX(Transactions, Transactions[Quantity_of_items]*Transactions[Unit_Price]))
		•	Average Transaction per Customer = DIVIDE([Total sales], COUNT(Transactions[Transaction_ID]),0)
		•	Average Daily Number of Transactions = 
		VAR NR_of_transaction = COUNTROWS(Transactions)
		       VAR Day_count = DATEDIFF(MIN(Transactions[Date]),MAX(Transactions[Date]),DAY)+1
		       VAR Final =  COALESCE(DIVIDE(Nr_of_transaction, Day_count,0),0)
		        RETURN Final
		•	Month-over-Month Growth % = 
	Optymalizacja wydajności
		1.	Filtrowanie na poziomie zapytania: wykorzystanie parametrów do ograniczenia ilości pobieranych danych
		2.	Modelowanie danych: implementacja schematu gwiazdy dla optymalnej wydajności
		3.	Optymalizacja miar: tworzenie miar pomocniczych do wielokrotnego wykorzystania
		4.	Efektywne wykorzystanie kontekstu filtra: unikanie zbyt złożonych wyrażeń DAX
8. Podsumowanie
	Projekt dostarcza kompleksowej analizy działalności sieci trzech kawiarni, umożliwiając podejmowanie decyzji biznesowych opartych na danych. Dzięki interaktywnym wizualizacjom 	i możliwości drążenia danych, raport stanowi skuteczne narzędzie do monitorowania kluczowych wskaźników efektywności i identyfikacji obszarów wymagających optymalizacji.
	Analiza ujawnia równomierne rozłożenie sprzedaży między lokalizacjami z niewielką przewagą Hell's Kitchen, dominację kategorii kawy w strukturze sprzedaży oraz wyraźne wzorce 		czasowe z różnicami między dniami roboczymi a weekendami. Rekomendacje dotyczące optymalizacji oferty produktowej, strategii dla poszczególnych lokalizacji oraz działań 					marketingowych mogą przyczynić się do dalszego wzrostu sprzedaży i poprawy efektywności operacyjnej.
