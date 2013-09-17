******************************************
Stałe i funkcje do obsługi mikrokontrolera
******************************************

Constants
=========

HIGH
----

Podczas odczytu lub zapisu pinu cyfrowego, możliwe jest przyjęcie przez niego tylko dwóch wartości: ``HIGH`` i ``LOW``.

Znaczenie ``HIGH`` różni się nieco w zależności od tego, czy pin jest ustawiony na wejście czy na wyjście. Gdy pin jest skonfigurowany jako wejście z użyciem funkcji ``pinMode()`` i odczytywany poprzez ``digitalRead()``, mikrokontroler będzie zwracać wartość ``HIGH``, gdy na pinie obecne będzie napięcie :math:`3 V` lub więcej.

Pin może być również skonfigurowany jako wejście poprzez ``pinMode()``, a następnie ustawiony na wartość ``HIGH`` poprzez ``digitalWrite()``. To ustawi wewnętrzny :math:`20 kΩ` rezystor podwyższający i ustabilizuje wejście pinu na odczytywanie wartości ``HIGH``, chyba że zewnętrzny obwód wymusi na nim przyjęcie wartości ``LOW``. Ten sam efekt można szybciej uzyskać poprzez użycie argumentu ``INPUT_PULLUP`` (wejście podwyższające) w funkcji ``pinMode()``.

Gdy pin jest skonfigurowany jako wyjście poprzez ``pinMode()`` i ustawiony na wartość ``HIGH`` z ``digitalWrite()``, to ustala się na nim napięcie :math:`5 V`. W tym stanie może służyć jako źródło prądu i np. zasilać diodę LED podłączoną szeregowo poprzez rezystor do masy, lub do innego pinu skonfigurowanego jako wyjście i ustawionego na wartość ``LOW``.

LOW
---

Podczas odczytu lub zapisu pinu cyfrowego, możliwe jest przyjęcie przez niego tylko dwóch wartości: ``HIGH`` i ``LOW``.

Znaczenie ``LOW`` także różni się nieco w zależności od tego, czy pin jest ustawiony na wejście czy na wyjście. Gdy pin jest skonfigurowany jako wejście poprzez ``pinMode()`` i odczytywany poprzez ``digitalRead()``, mikrokontroler zwracać będzie wartość ``LOW``, jeśli na pinie obecne jest napięcie :math:`2 V` lub mniej.

Gdy pin jest skonfigurowany jako wyjście poprzez ``pinMode()`` i ustawiony na wartość ``LOW`` poprzez ``digitalWrite()``, na pinie ustala się napięcie :math:`0 V`. W tym stanie może służyć jako masa i zamykać obwód np. diody LED połączonej szeregowo z poprzez rezystor do :math:`5 V`, albo innego pinu skonfigurowanego jako wyjście i ustawionego na watrtość ``HIGH``.

INPUT
-----

**Piny skonfigurowane jako wejście**


Cyfrowe piny mogą być używane jako wejścia, wejścia podwyższające i wyjścia. Zmiana przeznaczenia pinu poprzez funkcję ``pinMode()`` zmienia właściwości elektryczne pinu.

O pinach Arduino (Atmega) skonfigurowanych jako wejście poprzez ``pinMode()`` mówi się, że są w stanie wysokiej impedancji, ponieważ powodują one ekstremalnie mały spadek napięcia w obwodzie, który próbkują, porównywalny z :math:`100 MΩ` rezystorem połączonym szeregowo do pinu. To sprawia, że są one przydatne do odczytu czujnika, ale nie nadają się do zasilania diody LED.

Jeśli twój pin będzie skonfigurowany jako wejście, to będziesz chciał, by był on uziemiony. Jest to często realizowane poprzez rezystor obniżający.

INPUT_PULLUP
------------

**Piny skonfigurowane jako wejścia podwyższające**


Cyfrowe piny mogą być używane jako wejścia, wejścia podwyższające i wyjścia. Zmiana przeznaczenia pinu poprzez funkcję ``pinMode()``, zmienia właściwości elektryczne pinu.

Chip Atmega na Arduino posiada wewnętrzne rezystory podwyższające, które można wykorzystać. Jeśli wolisz je od zewnętrznych rezystorów obniżających, możesz użyć argumentu ``INPUT_PULLUP`` w ``pinMode()``. To skutecznie odwraca zachowanie - ``HIGH`` oznacza wyłączony sensor, a ``LOW`` włączony.

OUTPUT
------

**Piny skonfigurowane jako wyjścia**


Cyfrowe piny mogą być używane jako wejścia, wejścia podwyższające i wyjścia. Zmiana przeznaczenia pinu poprzez funkcję ``pinMode()``, zmienia właściwości elektryczne pinu.

O pinach Arduino skonfigurowanych jako wyjścia przy użyciu funkcji ``pinMode()`` mówi się, że są w stanie niskiej impedancji. Oznacza to, że mogą one zapewnić znaczną ilość prądu do innych układów. Piny Atmega mogą zasilać (prąd dodatni) lub uziemiać (prąd ujemy) aż do :math:`40 mA` do innych urządzeń / obwodów. To sprawia, że ​​są one przydatne do zasilania diod LED, ale bezużyteczne do odczytu sensorów. 
	
**Uwaga:**

Piny skonfigurowane jako wyjscia mogą zostać uszkodzone lub zniszczone, jeśli zostaną zwarte. Ilość prądu dostarczana prze Atmega nie wystarcza także na zasilanie większości przekaźników i silników elektrycznych. Wymagany więc będzie jakiś układ sprzęgający.

Digital I/O
===========

pinMode()
---------

**Opis:**

Konfiguruje określony pin jako wejście, wejście podwyższające lub wyjście.


**Uwaga:**

Piny analogowe mogą być używane jako piny cyfrowe, odnosząc się do nich jako A0, A1...


**Składnia:**

pinMode(<pin>, <tryb>)


**Parametry:**

<pin>: numer pinu, którego tryb chcesz ustawić

<tryb>: ``INPUT``, ``OUTPUT`` lub ``INPUT_PULLUP``


digitalWrite()
--------------

**Opis:**

Przypisz wartość ``HIGH`` lub ``LOW`` do pinu cyfrowego.

Jeśli pin jest skonfigurowany jako wyjście poprzez ``pinMode()``, jego napięcie będzie ustawione na odpowiednią wartość: :math:`5 V` lub :math:`3.3` V dla ``HIGH`` oraz :math:`0 V` (masa) dla ``LOW``.

Jeśli pin jest skonfigurowany jako wejście, przypisanie wartości ``HIGH`` poprzez ``digitalWrite()`` włączy wewnętrzny :math:`20 kΩ` rezystor podwyższający. Przypisanie wartości ``LOW`` - wyłączy. Rezystor podwyższający wciąż zapewnia napięcie wystarczające, aby dioda LED lekko świeciła, więc jeśli diody wydają się działać, ale bardzo słabo, to jest to prawdopodobnie przyczyną ich zachowania. Rozwiązaniem jest ustawienie pinu na wyjście poprzez ``pinMode()``. 


**Ostrzeżenie:**

Pin :math:`13` jest trudniejszy w użyciu jako wejście cyfrowe od pozostałych pinów cyfrowych, ponieważ na większości płytek posiada on fabrycznie przymocowaną do niego diodę LED i rezystor. Jeśli włączysz swój wewnętrzny :math:`20 kΩ` rezystor podwyższający, to napięcie wyniesie około :math:`1.7 V` zamiast oczekiwanych :math:`5 V`, w związku ze spadkiem napięcia na diodzie LED i szeregowym rezystorze, co spowoduje, że pin :math:`13` zawsze zwróci wartość ``LOW``. Jeśli musisz użyć pinu :math:`13` jako wejścia cyfrowego, użyj zewnętrznego rezystora obniżającego.


**Uwaga:**

Piny analogowe mogą być używane jako piny cyfrowe, odnosząc się do nich jako A0, A1...


**Składnia:**

digitalWrite(<pin>,<wartość>)


**Parametry:**

<pin>: numer pinu, którego wartość chcesz ustawić

<wartość>: ``HIGH`` lub ``LOW``


digitalRead()
-------------

**Opis:**

Odczytuje wartość z określonego pinu cyfrowego: ``LOW`` lub ``HIGH``.


**Składnia:**

digitalRead (<pin>)


**Parametry:**

<pin>: numer cyfrowego pinu, który chcesz odczytać (int)

Analog I/O
==========

analogReference()
-----------------

**Opis:**

Konfiguruje napięcie odniesienia podawane na wejście analogowe (wartość maksymalną wejścia). Możliwe opcje:

- DEFAULT: domyślna, napięcie odniesienia dla przetwornika jest napięciem zasilającym mikrokontroler, czyli :math:`5 V` lub :math:`3.3 V`,

- INTERNAL: wbudowane napięcie odniesienia równe :math:`1.1 V` dla ATmega168 (dla ATmega328 na Arduino Uno również),

- EXTERNAL: zewnętrzne napięcie odniesienia dołączone do linii AREF, mieszczące się w przedziale od :math:`0 V` do :math:`5 V`.


**Ostrzeżenie:**

Nie używaj napięcia niższego niż :math:`0 V` ani wyższego niż :math:`5 V` jako zewnętrznego napięcia odniesienia na pinie AREF. Jeśli używasz pinu AREF jako źródła zewnętrznego napięcia odniesienia, musisz ustawić typ EXTERNAL w funkcji ``analogReference()``, zanim użyjesz funkcji ``analogRead()``. W przeciwnym razie zewrzesz wewnętrznie generowane napięcie odniesienia pinu analogowego z pinem AREF, uszkadzając z dużym prawdopodobieństwem mikrokontroler na twojej płytce Arduino.


**Uwaga:**

Po zmianie analogowego napięcia odniesienia, kilka pierszych odczytów z ``analogRead()`` może nie być dokładne (stan nieustalony w obowodzie).


**Składnia:**

analogReference(<typ>)


**Parametry:**

<typ>: umożliwia wybranie napięcia odniesienia spośród typów DEFAULT, INTERNAL lub EXTERNAL.



analogRead()
------------

**Opis:**

Odczytuje wartość z wybranego pinu analogowego. Płytka Arduino Uno posiada 6-cio kanałowy, 10-cio bitowy konwerter analogowo-cyfrowy (każdy bit może przyjąć wartość 0 lub 1, co daje nam :math:`2^{10} = 1024` możliwych stanów). To powoduje, że napięcia wyjścia zawierające się w przedziale od :math:`0 V` do :math:`5 V`, przekształcane będą odpowiednio na liczby z przedziału od 0 do 1023, dla napięcia :math:`0 V < X < 5 V`, uzyskując wartość :math:`\frac{X}{1023}` na wyjściu. Widzimy także, że rozdzielczość odczytu wyniesie około :math:`4.9 mV`. Wartość oraz rozdzielczość wejścia mogą być zmienione poprzez ``analogReference()``.

Odczyt stanu analogowego wejścia zajmuje około :math:`0.1 ms`, więc maksymalne tempo odczytu wynosi około :math:`10^{3}` razy na sekundę.


**Uwaga:**

Jeśli wejście analogowego pinu nie jest do niczego podłączone, wartość zwrócona przez ``analogRead()`` będzie fluktuowała w zależności od szeregu czynników (np. wartości innych wejść analogowych, bliskości twojej ręki od płytki itd.).


**Składnia:**

analogRead(<pin>)


**Parametry:**

<pin>: numer pinu analogowego (0, 1, ...), z którego odczytywana będzie wartość


**Zwraca:**

Liczbę całkowitą z zakresu od 0 do 1023


analogWrite()
-------------

**Opis:**

Zapisuje wartość analogową (falę modulacji szerokości impulsów PWM, ang. pulse width modulation wave) do pinu. Może być używana do zapalania diody LED ze zmieniającą się jasnością, albo zasilania silnika elektrycznego z różnymi prędkościami. Po odwołaniu się do funkcji ``analogWrite()``, pin będzie generował stabilny sygnał prostokątny o określonym cyklu pracy, aż do ponownego wywołania funkcji ``analogWrite()`` (lub ``digitalRead()``, ``digitalWrite()``) na tym samym pinie. Częstotliwość sygnału PWM wynosi około :math:`490 Hz`.

Na płytce Arduino Uno funkcja ta jest dostępna na pinch 3, 5, 6, 9, 10 lub 11, i oznaczona jako ~<pin>.

Nie musisz używać funkcji ``pinMode()``, aby ustawić pin jako wyjście zanim odwołasz się do funkcji ``analogWrite()``.

Funkcja ``analogWrite()`` nie ma nic wspólnego z pinami analogowymi oraz z funkcją ``analogRead()``.


**Uwaga:**

Cykle pracy fal PWM na pinach 5 i 6 będą dłuższe niż ich oczekiwana wartość. Jest to spowodowane interakcją funkcii ``millis()`` oraz ``delay()``, dzielących ten sam wewnętrzny licznik, który służy do generowania tych fal. Będzie to zwłaszcza widoczne przy niskich wartościach cyklów pracy (0 – 10), powodując, że ustalenie wartości 0 niekoniecznie spowoduje całkowite wyłączenie pinów 5 oraz 6. 


**Składnia:**

analogWrite(<pin>, <value>)


**Parametry:**

<pin>: numer pinu, na którym zapisywana będzie wartość: 3, 5, 6, 9, 10 lub 11.

<value>: cykl pracy (iloraz czasu włączenia pinu do jego wyłączenia) z zakresu od 0 do 255 (w związku z 8 bitowością pinu), odpowiadający odpowiednio stałemu wyłączeniu i stałemu włączeniu.

Advanced I/O
============

tone()
------

**Opis:**

Generuje w pinie sygnał prostokątny o ustalonej częstotliwości (i 50% cyklu pracy). Czas trwania sygnału można podać jawnie, w przeciwnym razie sygnał będzie generowany do momentu wywołania funkcji ``noTone()``. Do pinu może być podłączony głośniczek piezoelektryczny (buzzer), aby wydobywać dźwięki.

Tylko jeden dźwięk może być generowany w tym samym momencie. Jeśli dźwięk jest już grany na innym pinie, odwołanie się do funkcji ``tone()`` nie przyniesie żadnego efektu. Natomiast gdy wydobywa się z tego samego pinu, jej wywołanie ponownie ustawi jego częstotliwość.

Używanie funkcji ``tone()`` będzie interferować z wyjściem PWM na pinach 3 i 11.


**Uwaga:**

Jeśli chcesz grać różne wysokości tego samego dźwięku na wielu pinach, musisz wywołać funkcję ``noTone()`` na poprzednim pinie, zanim wywołasz funkcję ``Tone()`` na następnym.


**Składnia:**

tone(<pin>, <częstotliwość>)

tone(<pin>, <częstotliwość>, <czas_trwania_sygnału>)


**Parametry:**

<pin>: pin na którym ma zostać wygenerowany sygnał prostokątny

<częstotliwość>: częstotliwość sygnału w Hz – typ: unsigned int

<czas_trwania_sygnału): opcjonalny, czas trwania sygnału w ms – typ: unsigned long

noTone()
--------

**Opis:**

Zatrzymuje generowanie sygnału prostokątego zainicjowanego przez funkcję ``tone()``. Nie daje żadnego efektu gdy sygnał nie jest generowany.


**Uwaga:**

Jeśli chcesz grać różne wysokości tego samego dźwięku na wielu pinach, musisz wywołać funkcję ``noTone()`` na poprzednim pinie, zanim wywołasz funkcję ``Tone()`` na następnym.


**Składnia:**

noTone(<pin>)


**Parametry:**

<pin>: pin, na którym generowanie sygnału prostokątnego ma zostać zakończone.

shiftln()
---------

**Opis:**

Przesuwa bajt danych po jednym bicie. Zaczyna albo od najbardziej znaczącego bitu (pierwszy po lewej), albo od najmniej znaczącego (pierwszy po prawej). Dla każdego bitu, clock pin ustawia się na wartość ``HIGH``, bit jest odczytywany ze strumienia danych, a potem clock pin wraca z powrotem do wartości ``LOW``.


**Uwaga:**

To jest implementacja software'owa. Arduino dostarcza także bibliotekę SPI, która wykorzystuje implementację hardware'ową, która jest szybsza, ale działa tylko dla określonych pinów.


**Składnia:**

bite incoming = shiftIn(<pin_danych>, <clock_pin>, <porządek_bitów>)


**Parametry:**

<pin_danych>: pin, na którym wchodzić będą kolejne bity – typ: int

<clock_pin>: przełączany pin sygnalizujący odczyt sygnału z pinu danych

<porządek_bitów>: kolejność w jakiej przesuwane mają być bity: MSBFIRST (ang. most significant bit first – najbardziej znaczący bit jako pierwszy) lub LSBFIRST ( ang. least significant bit first – najmniej znaczący bit jako pierwszy)


**Zwraca:**

Odczytana wartość – bajt.

pulseIn()
---------

**Opis:**

Zwraca długość impulsu (``HIGH`` lub ``LOW``) na pinie. Dla przykładu, jeśli wartość domyślna to ``HIGH``, funkcja ``pulseIn()`` oczekuje, aż dany pin przejdzie w stan ``HIGH`` i zaczyna odliczać czas, a następnie czeka aż pin przejdzie w stan ``LOW`` i zatrzymuje odliczanie. Na koniec zwraca długość impulsu w ms. Jeśli imuls nie pojawi się w określonym w funkcji czasie, zwraca ona wartość 0.

Odczyt czasu tej funkcji został określony empirycznie i prawdopodobnie będzie obarczony błędami dla dłuższych impulsów. Poprawnie działa dla impulsów z przedziału od :math:`10 ms` do :math:`3 min`.


**Składnia:**

pulseIn(<pin>, <wartość>)

pulseIn(<pin>, <wartość>, <czas_oczekiwania>)


**Parametry:**

<pin>: numer pinu, na którym chcesz odczytać długość impulsu

<wartość>: typ impulsu – ``HIGH`` lub ``LOW``

<czas_oczekiwania>: opcjonalny, liczba ms oczekiwania na rozpoczęcie impulsu, domyślnie :math:`1000 ms`.


**Zwraca:**

Długość impulsu w ms lub 0, jeśli impuls nie zaczął się w czasie mniejszym niż czas oczekiwania.

Time
====

milis()
-------

**Opis:**

Zwraca liczbę ms od kiedy płytka Arduino rozpoczęła działanie bierzącego programu. Po przekroczeniu około 50 dni od momentu włączenia i nieprzerwanego działania programu zakres liczby typu unsigned long wyczerpie się i program zacznie naliczać czas od nowa.


**Zwraca:**

liczbę ms od momentu rozpoczęcia programu – typ: unsigned long.

micros()
--------

**Opis:**

Zwraca liczbę μs od kiedy płytka Arduino rozpoczęła działanie bierzącego programu. Po przekroczeniu około :math:`70 min` od momentu włączenia i nieprzerwanego działania programu, zakres liczby typu unsigned long wyczerpie się i program zacznie naliczać czas od nowa.


**Zwraca:**

liczbę μs od momentu rozpoczęcia programu – typ: unsigned long.

delay()
-------

**Opis:**

Zatrzymuje działanie programu na określoną ilość czasu w ms.


**Uwaga:**

Mimo że łatwo jest wykorzystać funkcję ``delay()`` do uzyskania migającej diody LED, a wiele programów używa krótkich opóźnień np. do regulowania przełącznika, używanie funkcji ``delay()`` ma znaczącą wadę. Żaden inny odczyt z sensorów, operacja matematyczna lub operacja na pinie nie może zostać wykonana w trakcie działania funkcji ``delay()``, więc w efekcie przeprowadza ona całą aktywność układu w stan wstrzymania.

Dla alternatywnych sposobów regulowania czasem wykonywania zobacz funkcję ``milis()``. Bardziej doświadczeni programiści z reguły unikają używania funkcji ``delay()`` na czas dłuższy niż :math:`100 ms`, chyba że program jest bardzo prosty.

Niektóre procesy na chipie Arduino wykonują się normalnie podczas działania funkcji ``delay()``. Komunikacja seryjna występująca na pinie RX jest zapisywana, a wartości PWM na pinach są zachowywane.


**Składnia:**

delay(<czas_zatrzymania>)


**Parametry:**

<czas_zatrzymania>: czas zatrzymania programu w ms.


delayMicroseconds()
-------------------

**Opis:**

Zatrzymuje działanie programu na określoną ilość czasu w μs.

Obecnie największą wartością zwracającą dokładne opóźnienie jest 16383, może się zmienić dopiero w przyszłych wersjach Arduino, więc dla dłuższych przedziałów czasu zaleca się użwanie funkcji ``delay()``.


**Uwaga:**

Funkcja ``delayMicroseconds()`` działa bardzo dokładnie dla przedziałów większych od :math:`3 μs`.


**Składnia:**

delayMircoseconds(<czas_zatrzymania>)


**Parametry:**

<czas_zatrzymania>: czas zatrzymania programu w μs.

Math
====

constrain()
-----------

**Opis:**

Ogranicza liczbę do przedziału domkniętego.


**Składnia:**

constrain(<liczba>, <ograniczenie_dolne>, <ograniczenie_górne>)


**Parametry:**

<liczba>: liczba, którą chcemy ograniczyć

<ograniczenie_dolne>: liczba, bedąca ogr. dolnym przedziału

<ograniczenie_górne>: liczba, będąca ogr. górnym przedziału


**Zwraca:**

x – liczba, a – ogr. dolne, b – ogr. Górne

a: x < a

x: a = < x & x <= b

b: b < x


**Przykład:**

.. code-block:: c++

	sensorValue = constrain(sensorValue, 10, 150);
	// ogranicza zakres wartości sensora do przedziału [10, 150]

map()
-----

**Opis:**

Transformuje liczbę do innej skali liczbowej.

Nie ogranicza liczby do przedziału domkniętego, ponieważ wartości z poza zakresu są zamierzone i przydatne. Aby uzyskać efekt ograniczenie do przedziału domkniętego, należy przed lub po użyciu funkcji ``map()`` zastosować funkcję ``constrain()``.

Warto zauważyć, że “ograniczenia dolne” któregokolwiek z zakresów, mogą być większe niż “ograniczenia górne”. W efekcie funkcja ``map()`` może być używana do odwracania zakresu liczb.

Funkcja ``map()`` używa liczb całkowitych do obliczeń i nie jest w stanie wygenerować ułamków. Wykonywane dzielenie będzie więc dzieleniem całkowitym.


**Składnia:**

map(<liczba>,<ograniczenie_dolne_początkowe>,<ograniczenie_górne_początkowe>,<ograniczenie_dolne_końcowe>,<ograniczenie_górne_końcowe>)


**Parametry:**

<liczba>: liczba, którą chcemy przetransformować

<ograniczenie_dolne_początkowe>: początkowe ograniczenie dolne liczby

<ograniczenie_górne_początkowe>: początkowe ograniczenie górne liczby 

<ograniczenie_dolne_końcowe>: końcowe ograniczenie dolne liczby 

<ograniczenie_górne_końcowe>: końcowe ograniczenie górne liczby


**Zwraca:**

Przetransformowaną wartość.


**Przykład:**

.. code-block:: c++

	x = map(x, 0, 255, 0, 1023);

	// x będzie równy 4x

	x = map(x, 0, 255, 0, -255);

	// x będzie równy -x


Bits and Bytes
==============

lowByte()
---------

**Opis:**

Zwraca najmniej znaczący bajt (leżący najbardziej po prawej) ze zmiennej (np. słowa).


**Składnia:**

lowByte(<zmienna>)


**Parametry:**

<zmienna>: dowolna zmienna


**Zwraca:**

bajt

highByte()
----------

**Opis:**

Zwraca najbardziej znaczący bajt (leżący najbardziej po lewej) ze zmiennej (np. słowa), lub drugi najmniej znaczący bajt (drugi od prawej) większej zmiennej.


**Składnia:**

highByte(<zmienna>)


**Parametry:**

<zmienna>: dowolna zmienna


**Zwraca:**

bajt

bitRead()
---------

**Opis:**

Odczytuje bit z liczby.


**Składnia:**

bitRead(<liczba>, <numer_bitu>)


**Parametry:**

<liczba>: liczba, z której chcemy odczytać bit.

<numer_bitu>: numer bitu, który chcemy odczytać. Numeracja przebiega co 1, zaczynając od 0 dla najmniej znaczącego bitu (leżącego najbardziej po prawej).


**Zwraca:**

Wartość bitu: 1 lub 0.

bitWrite()
----------

**Opis:**

Nadpisuje bit odczytany z liczby.


**Składnia:**

bitWrite(<liczba>, <numer_bitu>, <wartość_logiczna>)


**Parametry:**

<liczba>: liczba, którą bit chemy nadpisać.

<numer_bitu>: numer bitu, który chcemy nadpisać. Numeracja przebiega co 1, zaczynając od 0 dla najmniej znaczącego bitu (leżącego najbardziej po prawej).

<wartość_logiczna>: wartość logiczna, jaką chcemy nadpisać na wybranym bicie: 1 lub 0.

bitSet()
--------

**Opis:**

Nadpisuje bit odczytany z liczby wartością logiczną 1.


**Składnia:**

bitSet(<liczba>, <numer_bitu>)


**Paramtery:**

<liczba>: liczba, której bit chemy nadpisać wartością logiczną 1.

<numer_bitu>: numer bitu, który chcemy nadpisać. Numeracja przebiega co 1, zaczynając od 0 dla najmniej znaczącego bitu (leżącego najbardziej po prawej).

bitClear()
----------

**Opis:**

Nadpisuje bit odczytany z liczby wartością logiczną 0.


**Składnia:**

bitClear(<liczba>, <numer_bitu>)


**Paramtery:**

<liczba>: liczba, której bit chemy nadpisać wartością logiczną 0.

<numer_bitu>: numer bitu, który chcemy nadpisać. Numeracja przebiega co 1, zaczynając od 0 dla najmniej znaczącego bitu (leżącego najbardziej po prawej).

bit()
-----

**Opis:**

Oblicza wartość wybranego bitu; n-ty bit ma wartość 2n.


**Składnia:**

bit(<numer_bitu>)


**Parametry:**

<numer_bitu>: numer bitu, który chcemy nadpisać. Numeracja przebiega co 1, zaczynając od 0 dla najmniej znaczącego bitu (leżącego najbardziej po prawej).


**Zwraca:**

Wartość bitu.

Interrupts
==========

interrupts()
------------

**Opis:**

Odblokowuje interrupts (po tym gdy zostały one zablokowane przy pomocy funkcji ``noInterrupts()``). Interrupts umożliwiają funkcjonowanie w tle pewnych istotnych zadań i są domyślnie odblokowane. Pewne funkcje przestaną działać, w momencie gdy interrupts są zablokowane, a przychodząca z programu komunikacja może być ignorowana. Jednakże interrupts mogą nieznacznie zakłócić synchronizację kodu, co sprawia, że ich celowe zablokowanie w krytycznych punktach kodu może być pożądane.


**Składnia:**

interrupts()

noInterrupts()
--------------

**Opis:**

Zablokowuje interrupts (do ich ponownego odblokowania należy użyć funkcji ``interrupts()``). Interrupts umożliwiają funkcjonowanie w tle pewnych istotnych zadań i są domyślnie odblokowane. Pewne funkcje przestaną działać, w momencie gdy interrupts są zablokowane, a przychodząca z programu komunikacja może być ignorowana. Jednakże interrupts mogą nieznacznie zakłócić synchronizację kodu, co sprawia, że ich celowe zablokowanie w krytycznych punktach kodu może być pożądane.


**Składnia:**

noInterrupts()

Communication
=============

Serial
------

**Serial – komunikacja seryjna**

Używana do komunikacji seryjnej płytki Arduino z komputerem lub innym urzadzeniem. Wszystkie płytki Arduino posiadają przynajmniej jeden port komunikacji seryjnej. Do komunikacji wewnętrznej używa pinów 0 (RX) i 1 (TX), natomiast do komunikacji z komputerem – łącza USB. Dlatego podczas jej używania nie mamy możliwości wykorzystywania pinów 0 i 1.

Aby komunikować się z płytką Arduino, możemy używać wbudowanego w jego środowisko monitora seryjnego, którego ikonka widoczna jest w prawym rogu paska narzędzi. Musimy tylko ustalić przepustowość wyrażoną w bit/s.

Stream
-------

**Stream class**

*Stream* jest podstawową klasą dla strumieni znakowych i binarych. Nie jest wywoływany bezpośrednio, lecz wywoływany pośrednio przez funkcje, których działanie się na nim opiera.

*Stream* definiuje funkcje odczytu na Arduino. Podczas używania funkcji, które w swojej nazwie zawierają człon 'read', lub podobny, możemy spokojnie założyć, że odwołuje się on do klasy *Stream*.

Dla funkcji takich jak ``print()``, *Stream* dziedziczy z klasy *Print*.
