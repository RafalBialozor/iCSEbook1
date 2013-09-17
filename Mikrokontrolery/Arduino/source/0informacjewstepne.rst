******************
Informacje wstępne
******************

Co to jest Arduino?
===================

Arduino jest narzędziem do tworzenia systemów mikroprocesorowych w oparciu o mikrokontrolery AVR (`wiki <http://en.wikipedia.org/wiki/Atmel_AVR>`_). Jest to open-source’owa platforma obliczeniowa oparta na prostej konstrukcji sprzętowej i zintegrowanym środowisku programistycznym (IDE - integrated development environment), przeznaczona dla artystów, projektantów, hobbystów i każdego zainteresowanego tworzeniem interaktywnych obiektów i środowisk. Celem projektu jest przygotowywanie narzędzi - ogólnodostępnych, nie wymagających dużych nakładów finansowych, elastycznych i łatwych w użyciu. Częściowo Arduino stanowi również alternatywę dla osób, które nie mają dostępu do bardziej zaawansowanych mikrokontrolerów, wymagających bardziej skomplikowanych narzędzi.

Arduino składa się:

- z mikrokontrolera na płytce z układami pomocniczymi, sensorów i aktuatorów

- oraz zintegrowanego środowiska programistycznego (IDE - integrated development environment).

Arduino może zostać wykorzystane do tworzenia modułowych urządzeń z różnymi układami peryferyjnymi, takimi jak przyciski, czujniki, wyświetlacze, interfejsy komunikacyjne przewodowe oraz bezprzewodowe, sterowniki silników itp. 


Dlaczego Arduino?
=================

System Arduino upraszcza proces przygotowywania oprogramowania dla mikrokontrolera. Ideą przyświecającą twórcom Arduino było maksymalne uproszczenie części sprzętowej systemu, umożliwiające jego rozbudowę za pomocą dodatkowych modułów, które mogą być zaprojektowane własnoręcznie lub przygotowane przez innych użytkowników tego systemu. Do programowania mikrokontrolerów nie są wymagane żadne dodatkowe programatory. Wystarczy podłączyć płytkę sprzętową do portu USB komputera i można już programować mikrokontroler własnym oprogramowaniem. Dodatkowe atuty Arduino:

- Jest niedrogi – podstawowa płytka startowa Arduino Uno jest w cenie poniżej 100 zł. 

- Bezpłatne oprogramowanie Arduino działa w systemach Windows, Macintosh OS X i Linux.

- Środowisko programistyczne jest łatwe w obsłudze dla początkujących i na tyle elastyczne, by mogli z niego korzystać zaawansowani programiści. Przygotowanie programu jest proste i zajmuje bardzo mało czasu.

- System Arduino jest systemem typu open-source, dlatego też może być zmodyfikowany do własnych potrzeb przez doświadczonych programistów,

- Jest niezwykle prosty dzięki modułowej konstrukcji zestawu ewaluacyjnego (Arduino Uno). Przygotowywana jest również bogata liczba modułów rozszerzających dla zestawu Arduino Uno, nazwanych AVT-Duino, dzięki którym można zbudować bardzo wiele niebanalnych urządzeń. 


Otwarty sprzęt i otwarte oprogramowanie
=======================================

Specyfikacja sprzętowa jest ogólnodostępna. Pliki CAD są udostępnione na licencji Creative Commons Attribution Share-Alike 2.5 i jest dostępny na stronie projektu `Arduino`_. Dostępne są również dokładne schematy budowy niektórych wersji układów Arduino. Układ można zbudować samodzielnie lub kupić (nie ma jednego oficjalnego producenta), każdy może produkować i sprzedawać zarówno układy zbudowane z oryginalnych planów, jak i własne modyfikacje. Kod źródłowy IDE Arduino i biblioteki sprzętowe dla Arduino są udostępniane i rozpowszechniane na licencji GPLv2. 

	
Arduino Uno
===========

Podstawowym zestawem dla Arduino jest zestaw Arduino Uno. Ma wyprowadzone wszystkie porty mikrokontrolera i interfejs USB, dzięki któremu można do mikrokontrolera przesyłać programy oraz przesyłać lub odczytywać dane przetworzone przez mikrokontroler. Aby uzyskać dodatkową funkcjonalność zestawu podstawowego, wystarczy włożyć do niego od góry dowolną płytkę rozszerzającą, zawierającą inne podzespoły (GPS, GSM, Ethernet, LCD itp.). 

Mikrokontroler taktowany jest częstotliwością 16 MHz. W zestawie Uno można zastosować mikrokontrolery ATmega8 lub nowsze: Atmega168 i ATmega328. Komunikacja z komputerem odbywa się za pomocą wspomnianego interfejsu USB. Dzięki temu są dostępne sterowniki dla większości systemów operacyjnych. 

.. figure:: ArduinoUno_R3_Front.jpg
   :width: 500px
   :align: center

   Płytka Arduino - widok z przodu

.. figure:: ArduinoUno_R3_Back.jpg
   :width: 500px
   :align: center

   Płytka Arduino - widok z tyłu
