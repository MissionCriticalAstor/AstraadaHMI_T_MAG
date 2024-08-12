Program Astraada HMI do wizualizacji na modelu AS46TFT1207 (1024x768), danych z czujników firmy ELA Innovatio (Blue PUCK T, Blue PUCK MAG) odbiera wiadomości za pośrednictwem protokołu MQTT z gatewaya Cassia X2000. Program:
  - odbiera dane wysyłane protokołem MQTT
  - wyświetla dane pomiarowe czujników w zależności od nazwy
  - wyświetla stan połączenia MQTT
  - możliwość przesłania danych innymi protokołami, np. Modbus TCP/IP

Po pobraniu, należy w ustawieniach "MQTT Client" zmienić adres IP brokera oraz port,
a także określić temat subskrypcji w sekcji „Text Format Table”.

![zmiana_brokera_i_tematu](https://github.com/user-attachments/assets/114be716-f898-4425-abe8-692d7816eca2)

LODÓWKA LUB ZASTAW SKŁAD SIĘ Z:
1X BLE PUCK T + 1x BLE PUCK MAG
CZUJNIKI W JEDNYM ZESTAWIE POWINNY MIEĆ TAKĄ SAMĄ NAZWE '0x',
GDZIE 'x' TO NR. ZESTAWU/LODÓWKI

DOMYŚLNIE PROGRAM JEST DLA DWÓCH ZASTAWÓW
Z MOŻLIWOŚCIĄ DODANIA WIĘKSZEJ ILOŚCI ZESTAWÓW

ABY DODAĆ NASTĘPNE ZESTAWY NALEŻY:
	- W ZAKŁADCE 'Tags -> Data Types -> Array Dimensions and Ranges -> High Bound -> Dim. 1' ZWIĘKSZYĆ TABLICE DLA ZMIENNYCH:
		> lodowka
		> wynik_n
		> wynik_t
		> wynik_s
		> wynik_c
		> porownanie
		> count
		> oraz dodac zmienną/zmienne 'stan3', ..., 'stanX'; Data Type: STRING

- DODAĆ DO 'Macros -> Native Scripts -> STALE' NASTĘPNY ZESTAW: 0\lodowka[x] = "0x",
	GDZIE '0x' TO NAZWA OBU CZUJNIKÓW W DANYM ZESTAWIE
	
	- DODAĆ DO 'Macros -> Native Scripts -> main' NASTĘPNĄ PĘTLE 'IF' I 'porownani',
	ODPOWIEDNIO WSTAWIAJĄC NR. NASTĘPNEJ LODÓWKI W MIEJSCE '[x]'
	
	- DODAĆ DO 'Screen 1 (#1)' MIEJSCA DO WYŚIETLANIA DANYCH Z NOWEGO ZESTAWU
