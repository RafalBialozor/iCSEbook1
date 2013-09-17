*******************
Język programowania
*******************

Program główny
==============

Język Arduino IDE jest zbliżony do języka C. W języku Arduino, oprócz standardowych stałych, są dostępne stałe ``LOW``, ``HIGH``, ``INPUT`` oraz ``OUTPUT``, związane z operacjami na liniach portów mikrokontrolera, natomiast typy zmiennych są identyczne jak dla języka C. Nowością w języku Arduino są funkcje związane z mikrokontrolerem. 

Program główny systemu Arduino składa się z dwóch nieodzownych struktur: ``setup()`` oraz ``loop()``. W pierwszej kolejności są inicjowane zmienne. Następnie w strukturze ``setup()`` inicjowane są tryby pracy lini mikrokontrolera, jego peryferia, linie portów mikrokontrolera oraz funkcje. Struktura ta jest wykonywana tylko raz, podczas włączania zasilania lub zerowania mikrokontrolera. 

Po strukturze inicjującej wymagana jest struktura ``loop()``, która tworzy niekończoną pętlę, w której wykonywany jest program sterujący pracą CPU. Działanie instrukcji w pętli będzie zależeć od użytkownika i napływających informacji z otoczenia mikrokontrolera. Oczywiście, jest możliwe wychodzenie z nieskończonej pętli do obsługiwanych funkcji z bibliotek lub własnych. 

Biblioteki
==========

Oprócz dostępnych instrukcji języka Arduino, dostępne są liczne biblioteki funkcji, umożliwiających obsługę różnych układów, dołączanych do mikrokontrolera. Są dostępne dwie grupy bibliotek:

- Biblioteki dostępne z systemem Arduino, czyli biblioteki standardowe (biblioteki funkcji obsługi pamięci EEPROM, komunikacji z komputerem, obsługi wyświetlaczy LCD, transmisji sieciowej ETHERNET, obsługi kart pamięci SD, silników krokowych, programowej wersji interfejsu RS232 czy obsługi interfejsów SPI i I2C/TWI, w które został wyposażony w mikrokontroler). Do niektórych bibliotek standardowych wymagane będą elementy sprzętowe, jak choćby wyświetlacz LCD czy kontroler Ethernet. 

- Niestandardowe biblioteki utworzone przez innych użytkowników systemu Arduino, które można ściągnąć z Internetu. Biblioteki niestandardowe można podzielić na kilka grup:

	- W grupie bibliotek komunikacyjnych można znaleźć biblioteki, umożliwiające obsługę wiadomości tekstowych, obsługi interfejsu 1-Wire, klawiatury z interfejsem PS2, obsługi telefonu komórkowego czy serwera www. Dostępne są również biblioteki, umożliwiające komunikacje zestawów Arduino ze sobą. 

	- W grupie bibliotek obsługujących czujniki są dostępne biblioteki, obsługujące czujniki pojemnościowe oraz przyciski, w jakie jest wyposażona większość urządzeń. 

	- Dostępna jest również grupa bibliotek obsługujących wyświetlacze graficzne oraz wyświetlacze wielosegmentowe LED.

	- Biblioteki w grupie generatory umożliwiają generowanie sygnału na dowolnym pinie mikrokontrolera lub z wykorzystaniem scalonych generatorów PWM. 

	- Dostępna jest również grupa bibliotek dotyczących czasu. Można w niej znaleźć bibliotekę obsługującą zegar oraz kalendarz. Pozostałe biblioteki związane są z odmierzaniem czasu. 

	- Ostatnia grupa dostępnych bibliotek dotyczy bibliotek do obsługi tekstów, przydatnych podczas wyświetlania tekstowych komunikatów na wyświetlaczu LCD lub wysyłanych do komputera. 


Typy pamięci
============

W mikrokontrolerach programowanych przez Arduino istnieją trzy rodzaje pamięci:

- pamięć FLASH (przestrzeń programu). Przechowywany jest w niej program napisany w Arduino. Dane zapisane w tej pamięci nie są tracone po wyłączeniu zasilania.

- pamięć SRAM (Static Random Access Memory) - pamięć na zmienne, czyli dane z obliczeń przeprowadzanych przez mikrokontroler. Dane w tej pamięci są tracone po wyłączeniu zasilania,

- pamięć EEPROM - pamięć do stałego przechowywania danych. Zapisane dane nie są wymazywane po wyłączeniu zasilania. Można jej używać do długoterminowego przechowywania informacji.
