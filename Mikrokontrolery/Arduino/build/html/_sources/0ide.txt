***********
Arduino IDE
***********

Oprogramowanie Arduino IDE
==========================

Projekty Arduino mogą pracować samodzielnie lub poprzez komunikację z oprogramowaniem zainstalowanym na komputerze (dostępnym na stronie http://arduino.cc/), przy wykorzystaniu zintegrowanego środowiska programistycznego IDE (na przykład zbudowanego na `Processing`_, Flash, MaxMSP), które można dostosować do własnych potrzeb. Głównym założeniem twórców Processinng było stworzenie języka programowania na tyle prostego, aby był on przyjazny dla osób, nie posiadających doświadczenia związanego z programowaniem. Pierwotną grupą docelową byli artyści sztuk wizualnych, jednak z biegiem czasu okazało się, że język ten jest na tyle uniwersalny, że można go wykorzystywać do tworzenia innych aplikacji. 

Oprogramowanie Arduino jest darmowe. Aplikacje pisane w Processing są multiplatformowe - mogą być uruchamiane na każdym systemie operacyjnym (Windows, OSX, Linux). IDE posiada edytor tekstu z takimi funkcjami jak podświetlanie składni czy automatyczne tworzenie wcięć w kodzie, oraz pozwala na kompilację i załadowanie programu do płyty Arduino. Zazwyczaj nie ma potrzeby dodatkowej edycji plików Makefile lub uruchamiania programów z listy poleceń. 

Standardowo IDE Arduino zawiera bibliotekę C/C++ o nazwie `Wiring`_ z projektu o tej samej nazwie, dzięki czemu wykonywanie podstawowych operacji wejścia/wyjścia staje się znacznie łatwiejsze. 

Przygotowany program należy poddać weryfikacji i kompilacji. Po wybraniu ikony *Verify/Compile* kompilator sprawdza składnię programu, a następnie poddaje ją kompilacji. Po jej prawidłowym zakończeniu program jest gotowy do wysłania do mikrokontrolera. W przypadku nieprawidłowości w kodzie, w dolnej części okienka systemu Arduino zostaną wyświetlone znalezione błędy. Przed wysłaniem programu do mikrokontrolera należy skonfigurować typ zestawu Arduino oraz numer portu w komputerze, do którego jest dołączony. 

Ikona przycisku *Stop* zatrzymuje działanie Serial Monitor (monitor komunikacji szeregowej). Jest to pomocne, gdy przesyłane przez interfejs szeregowy RS232 informacje pojawiają się szybciej, niż można je zaobserwować. 

Przycisk *Serial Monitor* uruchamia okno, w którym pojawiają się informacje wysyłane przez interfejs RS232 mikrokontrolera. Umożliwia ono także wysyłanie danych do mikrokontrolera. W oknie monitora dostępne są opcje automatycznego przewijania otrzymanych znaków, możliwość wyboru prędkości transmisji czy opcji związanych ze znakami końca linii. Monitor będzie pomocny podczas sprawdzania pracy programu i wyszukiwania w nim błędów. 

.. figure:: Arduino_IDE.jpg
   :width: 500px
   :align: center

   Arduino IDE

Uruchomienie zestawu
====================

Zestaw może być zasilany z użyciem zewnętrznego zasilacza lub z interfejsu USB. Po połączeniu zestawu Arduino UNO z komputerem za pomocą przewodu USB należy w pierwszej kolejności zainstalować sterowniki USB wirtualnego portu COM. Sterowniki te znajdują się w pakiecie Arduino w katalogu Drivers. Należy jeszcze odpowiednio skonfigurować oprogramowanie Arduino IDE, korzystając z zakładki Tools z menu,a następnie ustawić numer portu, przez który będzie się odbywała komunikacja. Oprogramowanie Arduino IDE może się już komunikować z zestawem Arduino UNO. Prawidłowa komunikacja będzie sygnalizowana za pomocą diod TX oraz RX. Aby przesłać do zestawu przygotowany program, po jego weryfikacji i kompilacji wystarczy przycisnąć przycisk *Upload*. Problemy z komunikacją może powodować sprzęt lub nieprawidłowa konfiguracja portu komunikacyjnego. Zainstalowany numer portu powinien być zgodny z wybranym portem w oprogramowaniu Arduino IDE. 
