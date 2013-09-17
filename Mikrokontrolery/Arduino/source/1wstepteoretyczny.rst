*****************
Wstęp teoretyczny
*****************

Podstawowe elementy zestawu Arduino 
===================================

Zestaw ma gniazdo USB, za pomocą którego odbywa się komunikacja komputera PC z mikrokontrolerem zestawu. Zestaw może być zasilany z interfejsu USB lub z wykorzystaniem zewnętrznego zasilania. 

Dostępne są linie DIGITAL (cyfrowe) mikrokontrolera oznaczone od 0 do 13, przy czym linie 0 i 1 są liniami interfejsu RS232. Cyfrowe linie portów mikrokontrolerów mogą być skonfigurowane jako wejścia lub wyjścia.

Dostępna jest również linia AREF, do której można dołączyć zewnętrzne napięcie odniesienia dla przetwornika A/C mikrokontrolera. 

Do gniazda ANALOG IN dołączone zostały linie analogowe mikrokontrolera, oznaczone od A0 do A5, które również mogą pracować jako linie cyfrowe. Analogowe linie portów mikrokontrolerów mogą być skonfigurowane jako wejścia lub wyjścia. 

Część z wejść/wyjść może pełnić funkcje dostarczane przez oprogramowanie Arduino: komunikacja szeregowa (RS), protokół I2C, zewnętrzne przerwania. 

Do gniazda Power doprowadzono linie masy, napięcia zasilające :math:`5 V` i :math:`3.3 V` oraz linię zerującą RESET. Dostępne jest również gniazdo ICSP, do którego można dołączyć zewnętrzny programator. Umożliwia on załadowania do pamięci mikrokontrolera programu Bootloadera lub zaprogramowania go dowolnym innym programem. Ponadto zestaw wyposażono w diodę sygnalizującą zasilanie, diody sygnalizujące transmisję z wykorzystaniem interfejsu RS232 oraz diodę „L” sygnalizującą stan linii 13 mikrokontrolera. 

Obsługa cyfrowych linii 
=======================

Obsługa linii cyfrowych mikrokontrolera w głównej mierze polega na konfiguracji ich, czy mają pracować jako wyjścia lub wejścia z rezystorem podwyższającym. W zestawie Arduino z mikrokontrolerem ATmega domyślnie linie portów są skonfigurowane jako wejścia z wyłączonym rezystorem podwyższającym. Czyli domyślnie są to wejścia, prawie nie pobierające prądu i bardzo często są wykorzystywane do odczytu sygnałów z czujników. 

W mikrokontrolerach ATmega jest możliwość programowego włączenia rezystora podwyższającego, który domyślnie na linii wejściowej będzie ustalał stan wysoki. Rozwiązanie z rezystorem podwyższającym jest bardzo często wykorzystywane podczas odczytu stanu z przycisków. Jego naciśnięcie, na linii wejściowej ustawi stan niski, a domyślnie po jego puszczeniu będzie panował stan wysoki wymuszany przez rezystor podwyższający. 

Cyfrowe linie mogą również być wyjściami, na których stan może się zmieniać na niski lub wysoki, co odpowiada napięciu :math:`0 V` i :math:`5 V`. Wydajność prądowa wyjść mikrokontrolerów Atmega umożliwia zasilanie dołączonych do nich diod LED. W przypadku większych obciążeń wymagane są dodatkowe wzmacniacze, chociażby w postaci tranzystorów. 

Do obsługi cyfrowych linii w Arduino dostępne są trzy funkcje ``pinMode()``, ``digitalWrite()`` i ``digitalRead()``. 

- Za pomocą funkcji ``pinMode(<pin>, <mode>)`` mamy możliwość skonfigurowania typu linii cyfrowej – ma być wejściem czy wyjściem. Pierwszy parametr określa numer pinu mikrokontrolera zgodnie z opisem linii na płytce zestawu Arduino Uno. Drugi parametr, ``mode``, może posiadać stałe parametry ``INPUT`` lub ``OUTPUT``, co wskazuje, czy linia ma być wejściem, czy wyjściem. 

- Funkcja ``digitalWrite(<pin>, <value>)`` służy do ustawiania stanu linii mikrokontrolera. Pierwszy parametr pin określa numer pinu, natomiast drugi parametr określa, jaki ma być jej stan (niski czy wysoki – stałe parametry ``LOW`` lub ``HIGH``). Instrukcja ``digitalWrite()`` umożliwia również załączenie rezystora podwyższającego na linii będącej wejściem. Aby do linii wejściowej dołączyć wewnętrzny rezystor podwyższający należy z wykorzystaniem funkcji ``digitalWrite()`` wpisać do linii wejściowej wartość ``HIGH``.

- Instrukcja ``digitalRead(<pin>)`` służy do odczytu stanu linii będącej wejściem. Parametr pin określa numer pinu mikrokontrolera który jest odczytywany. Funkcja zwraca stan odczytywanego stanu pinu zgodnie z przykładem: ``val = digitalRead(12);``. Do zmiennej val zostanie zapisany stan 12 linii portu mikrokontrolera. 

Liczba dostępnych portów będzie zależeć od zastosowanego mikrokontrolera, choć istnieje również możliwość ich zwiększenia poprzez dołączenie do niego odpowiednich ekspanderów. Na płytce Arduino Uno dostępne są cyfrowe linie portów oznaczone numerami od 0 do 13. Dlatego też dla ułatwienia właśnie tymi aliasami można się posługiwać podczas konfigurowania portów I/O.

Funkcje specjalne pinów
=======================

Informacje wstępne
------------------

Wyprowadzenia Arduino, oprócz standardowej roli wejść/wyjść cyfrowych, posiadają także pewne funkcje specjalne. Są to między innymi: wyprowadzenia sprzętowych interfejsów komunikacyjnych, wyjścia analogowe czy wyjścia timerów (liczników). Dla każdego z nich Arduino posiada bibliotekę, która sprawia, że korzystanie z nich staje się niezwykle proste.

- Serial: 0 (RX) i 1 (TX). Używane do odbioru (RX) i nadawania (TX) TTL [Transistor-transistor logic – klasa cyfrowych układów scalonych] danych seryjnych. Te piny są podłączone do odpowiednich styków na ATmega8U2 USB-to-TTL Serial chip.

- External Interrupts: 2 i 3. Te piny mogą być skonfigurowane do wyzwalania przerwania o niskiej wartości, wzrastania i opadania wykresu sygnału cyfrowego, lub zmiany wartości (szczegóły: funkcja ``attachInterrupt()``).

- PWM: 3, 5, 6, 9, 10 i 11. Zapewniają 8-bitowe wyjście PWM z funkcją ``analogWrite ()``.

- SPI: 10 (S), 11 (MOSI), 12 (MISO), 13 (SCK). Te piny obsługują komunikację SPI przy użyciu biblioteki SPI.

- LED: 13. Gdy pin ma wysoką wartość, dioda LED jest włączona, gdy pin jest niski, to jest wyłączona.

- TWI - I2C - Kolejny popularny, szeregowy, synchroniczny interfejs komunikacyjny. Wymaga dwóch linii komunikacyjnych: danych oraz zegarową (CLK). Za pomocą I2C użytkownik może obsługiwać np. czujniki MEMS (MinIMU-9).


Interfejs szeregowy  (UART)
---------------------------

Do transmisji używane są dwie linie: RX (pin 0) – odbiornik (pin 1) oraz TX - nadajnik. Interfejs jest bardzo prosty w konfiguracji, pozwala na wymianę danych z komputerem bądź obsługę urządzeń cyfrowych np. modułu Bluetooth lub sterownika serwomechanizmów. Czasem oznaczany jest jako USART. Literka *S* oznacza, że dane wysyłane są w sposób synchroniczny, czyli do transmisji oprócz TX RX,﻿ potrzebna jest jeszcze jedna linia - linia zegarowa (CLK).

Przerwania zewnętrzne 
---------------------

Mikrokontroler umożliwia wykonywanie procedur obsługi prze­rwań, czyli podprogramów, których wykonanie musi odbyć się na­tychmiast po zaistnieniu określonego zdarzenia. Wtedy wykonywanie programu głównego jest przerywane na czas realizacji podprogramu obsługi przerwania. 

Przerwania zewnętrzne umożliwiają natychmiastową obsługę zdarzeń zewnętrznych, sygnalizowanych sygnałem logicznym. Zdarzenia mogą być wyzwalane za pomocą zbocza opadającego, narastającego lub jakiejkolwiek zmiany logicznej. Gdy zdarzenie wystąpi procesor natychmiast przerwie wszystkie dotychczasowe operacje i zacznie wykonywać fragment kodu związany z obsługą przerwania.﻿

Do obsługi przerwania zewnętrz­nego wykorzystywane są funkcje włączające przerwanie ``attachInter­rupt(<interrupt>, <function>, <mode>)`` oraz wyłączające przerwanie ``detachIn­terrupt(interrupt)``. Parametr ``<interrupt>`` jest numerem portu, od którego jest zgłaszane przerwanie. 

Parametr ``<function>`` to nazwa funkcji, która będzie wykonywana po zaistnieniu przerwania, a mode określa mo­ment zgłoszenia przerwania. Parametr ``<mode>`` ma następujące wartości: 

- ``LOW`` – wywoływane, gdy pin posiada stan niski, 

- ``CHANGE`` – wywoływane, gdy pin zmieni stan, 

- ``RISING`` – wywoływane przy narastającym zboczu sygnału, 

- ``FALLING`` – wywoływane przy opadającym zboczu sygnału. 



Obsługa generatora PWM 
----------------------

6 z 14 pinów Arduino Uno (3, 5, 6, 9, 10 i 11), służących jako wyjście lub wejścia, może działać w trybie PWM output, czyli można sterować mocą przekazywaną (doskonale nadaje się do sterowania jasnością świecenia diody). 

Sygnał PWM (Pulse-width modulation, czyli modulacja szerokości impulsu) jest to sygnał prostokątny o modyfikowanym wypełnieniu. Z wykorzystaniem sygnału PWM i jego późniejszym uśrednieniu z wykorzystaniem prostego filtra, składającego się z rezystora i kondensatora można uzyskać prosty przetwornik cyfrowo-analogowy, na wyjściu którego wartość analogowa (napięcie) będzie zależna od wypełnienia generowanego sygnału PWM. Częstotliwość sygnału PWM w Arduino to około :math:`500 Hz`. 

Do generowania sygnału PWM dostępna jest funkcja ``analogWrite(<pin>, <value>)``, gdzie pierwszym parametrem jest numer linii cyfrowej PWM, a ``<value>`` wartością wypełnienia generowanego sygnału PWM w zakresie od 0 do 255. 

- Wartość 255 daje stałe napięcie :math:`5 V`.

- Wartość 127 daje wypełnienie 50%, czyli napięcie wyjściowe po uśrednieniu :math:`2.5 V`.

- Natomiast wartość 0 daje wypełnienie 0% i napięcie :math:`0 V`. 

Z wykorzystaniem sygnału PWM można modyfikować np. jasność dołączonej diody LED czy prędkości silnika. Sygnał PWM dla mikrokontrolera ATmega168, który zamontowany jest w Arduino Uno może być generowany na pinach 3, 5, 6, 9, 10 i 11. Na przykład funkcja: 

.. code-block:: c++

	analogWrite(5, 127); 
	//Sygnał PWM o wypełnieniu 127 generuje sygnał PWM na pinie 5 o wypełnieniu 50%. 

Nie trzeba również ustawiać linii PWM jako wyjścia przez wywołaniem funkcji ``analogWrite()``, ale dla czytelności programu zalecane jest ustawienie linii PWM jako wyjście z wykorzystaniem funkcji ``pinMode()``. 

.. figure:: pwm.gif
   :width: 450px
   :align: center


Interfejs SPI
-------------

Magistrala szeregowa działająca w sposób synchroniczny﻿. Do komunikacji używane są trzy wyprowadzenia: MOSI(11), MISO (12), SCK(13). Charakteryzuje się wysoką prędkością transmisji, dlatego też jest używana do obsługi szybkich urządzeń (np. pamięci EEPROM, przetworników A/C, C/A). Wykorzystywana jest także do komunikacji z niektórymi wyświetlaczami i czujnikami. 

Pin 13
------

Pin 13 jako jedyny posiada rezystor wbudowany w płytkę Arduino, czego konsekwencją jest zmniejszenie napięcia do :math:`1.7 V`. Dlatego można do niego podłączyć diodę bezpośrednio i nie ulegnie ona przepaleniu.

