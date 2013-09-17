********
Programy
********

Blink
=====

Opis
----

Do układu podłącz diodę led – dłuższa noga do pinu, krótsza przez opornik (może być jakakolwiek wartość od :math:`100 Ω` do :math:`100 kΩ` – zwróć uwagę, jaki ma to wpływ na jasność diody).

Po zaprogramowaniu mikrokontrolera dioda powinna migać z częstotliowością określaną przez wartości opóźnienia zawarte w funkcji ``delay()``.

W kodzie funkcja ``delay()`` wywołana jest dwa razy – za pierwszym razem określa jak długo dioda ma świecić, za drugim razem określa jak długo ma być zgaszona.

*Po co jest ten opornik?* – Jesli masz zapas diod spróbuj podłączyć jedną bez opornika, chwile poświeci i się przepali, przy odrobinie szczęścia puści również trochę dymu – diody nie lubią dużego natężenia prądu.


*Dlaczego w przykładzie Blink nie ma opornika?* – Pin 13 jako jedyny posiada opornik wbudowany w płytkę Arduino dlatego można do niego podłączyć diodę bezpośrednio i nie ulegnie ona przepaleniu.


.. figure:: Blink_bb.jpg
   :align: center

.. figure:: Blink_schem.jpg
   :align: center

Kod
---

.. code-block:: c++

	// inicjalizacja zmiennych globalnych:
	int led = 13;			// Pin 13 ma podłączony LED na płycie.


	// procedura setup() wykonuje się po resecie:
	void setup() 
	{
	  pinMode(led, OUTPUT);		// zainicjalizuj pin cyfrowy jako wyjście
	}

	// procedura loop() - nieskończona pętla:
	void loop()
	{ 
	  digitalWrite(led, HIGH);	// zapal LED 
	  delay(1000);			// czekaj sekundę 
	  digitalWrite(led, LOW);	// zgaś LED 
	  delay(1000); 			// czekaj sekundę
	}

Fade
====

Opis
----

Program ilustruje zastosowanie funkcji ``analogWrite()`` do wytworzenia efektu blaknięcia światła diody LED. ``AnalogWrite()`` wykorzystuje modulację szerokości impulsu (PWM).


*Obwód:*

Anodę diody LED podłącza się do cyfrowego wyjścia na pinie 9 na Arduino poprzez :math:`220 Ω`-owy rezystor, natomiast katodę bezpośrednio do uziemienia.


.. figure:: fade_bb.jpg
   :width: 600px
   :align: center

.. figure:: fade_schem.jpg
   :width: 600px
   :align: center

Kod
---

.. code-block:: c++

	int led = 9;  // pin, do którego podłączona jest dioda
	int brightness = 0;  // jak jasna jest dioda
	iny fadeAmount = 5;  // jak szybko bleknie dioda

	void setup()
	{
	  pinMode(led, OUTPUT);  // zadeklarowanie pinu 9 jako wyjście
	}

	void loop()
	{
	  analogWrite(led, brightness);  // ustawienie jasności pinu 9
	  brightness = brightness + fadeAmount;  // zmiana jasności diody dla kolejnych iteracji pętli  

	  // odwrócenie kierunku blaknięcia na końcach przedziału:
	  if (brightness == 0 || brightness = 255)
	  {
	    fadeAmount = -fadeAmount;
	  }
	  delay(30);  // odczekanie 30 ms  
	}

Pushbutton
==========

Opis
----

Ten przykład ilustruje włączenie lub wyłączenie diody LED przy naciśnięciu przycisku.

Podłączamy trzy przewody do płyty Arduino – dwa, zapewniające dostęp do :math:`5 V` i uziemienia, oraz jeden, łączący cyfrowy pin z jednym z ramion przycisku. Te samo ramię uziemia się poprzez :math:`10 kΩ`-owy rezystor obniżający. Drugie ramię przycisku podłącza się do zasilania :math:`5 V`. 

Gdy przycisk nie jest wciśnięty, nie ma połączenia między dwoma ramionami, więc pin jest podłączony do masy (przez rezystor obniżający) i odczytujemy wartość ``LOW``.

Gdy przycisk jest wciśnięty, ramiona są połączone, łącząc pin z zasilaniem :math:`5 V`, tak że odczytujemy wartość ``HIGH``.

Ten sam schemat może również działać w przeciwną stronę: z rezystorem podwyższającym, utrzymującym na wejściu wartość ``HIGH`` i zwracającym wartość ``LOW``, gdy przycisk jest wciśnięty. Zachowanie programu zostaje odwrócone: dioda LED świeci się, gdy przycisk nie jest wciśnięty i wyłącza po jego naciśnięciu.

Po odłączeniu cyfrowego I/O pinu od wszystkiego, LED może migać nieregularnie. To dlatego, że wejście będzie losowo zwracać wartość ``HIGH`` lub ``LOW``. Dlatego potrzebny jest w obwodzie rezystor podwyższający lub obniżający.


.. figure:: Button_bb.jpg
   :width: 600px
   :align: center

.. figure:: Button_schem.jpg
   :align: center


Kod
---

.. code-block:: c++

	//przycisk

	//inicjalizacja zmiennych globalnych:
	const int LED = 13; 
	const int BUTTON = 2;
	int val = 0;

	//procedura setup() wykonuje się po resecie:
	void setup()
	{
	  pinMode(LED, OUTPUT);
	  pinMode(BUTTON, INPUT);
	}

	//procedura loop() - nieskończona pętla:
	void loop()
	{
	  val = digitalRead(BUTTON);
	  digitalWrite(LED, val);
	}


|
|
|
|


.. code-block:: c++

	//przycisk odwrotnie

	//inicjalizacja zmiennych globalnych:
	const int LED = 13;
	const int BUTTON = 2;
	int val = 0;

	//procedura setup wykonuje się po resecie:
	void setup()
	{
	  pinMode(LED, OUTPUT);
	  pinMode(BUTTON, INPUT);
	}

	//procedura loop – nieskończona pętla:
	void loop()
	{
	  val = 1 - digitalRead(BUTTON);
	  digitalWrite(LED, val);
	}


Switch
======

Opis
----
Ten przykład ilustruje włączanie lub wyłączaniu diody LED po naciśnięciu przełącznika.

Podłączamy trzy przewody do płyty Arduino – dwa, zapewniające dostęp do :math:`5 V` i uziemienia, oraz jeden, łączący cyfrowy pin z jednym z ramion przycisku. Te samo ramię uziemia się poprzez :math:`10 kΩ`-owy rezystor obniżający. Drugie ramię przycisku podłącza się do zasilania :math:`5 V`. 


.. figure:: Button_bb.jpg
   :width: 600px
   :align: center

.. figure:: Button_schem.jpg
   :align: center

Kod
^^^

.. code-block:: c++

	//inicjalizacja zmiennych globalnych:
	const int LED = 13;
	const int BUTTON = 7;
	int val = 0;
	int state = 0;
	int old = 0;

	//procedura setup wykonuje się po resecie:
	void setup()
	{
	  pinMode(LED, OUTPUT);
	  pinMode(BUTTON, INPUT);
	}

	//procedura loop – nieskończona pętla:
	void loop()
	{
	  val = digitalRead(BUTTON);
 	  if ((val == HIGH) && (old == LOW))
	  {
	    state = 1-state;
	    delay(20);
	  }
	  old = val;
	  digitalWrite(LED, state);
	}



Six Diodes
==========

Opis
----

Program ilustruje zachowanie sześciu diod, migających losowo.

.. figure:: Loop_bb.jpg
   :width: 600px
   :align: center

.. figure:: Loop_schem.jpg
   :width: 600px
   :align: center


Kod
---

.. code-block:: c++

	int time;
	int ledPins[] = {2, 3, 4, 5, 6, 7};
	int ledsNum = 6;
	int raLed;
	int raTime;
	void setup()
	{
	  for(int led = 0; led < ledsNum; led++)
	  {
	    pinMode(ledPins[led], OUTPUT);
	  }
	}

	void loop()
	{
	  time = 110;
	  raTime = rand() % ledsNum;
	  if (raTime == 1)
	  {
	    time += 100;
	  }
	  if (raTime == 2)
	  {
	    time -= 100;
	  }
 	  raLed = rand() % ledsNum;
	  digitalWrite(ledPins[raLed], HIGH);
	  delay(time);
	  digitalWrite(ledPins[raLed], LOW);
	}

Traffic light for vehicles
==========================

Opis
----

Program ilustruje działanie sygnalizacji świetlnej dla pojazdów.


.. figure:: car.jpg
   :width: 600px
   :align: center

.. figure:: car_schem.jpg
   :width: 600px
   :align: center


Kod
---

.. code-block:: c++

	//inicjalizacja zmiennych globalnych:
	int time = 2000;
	int ledPins[] = {10, 11, 12};
	int green = ledPins[0];
	int yellow = ledPins[1];
	int red = ledPins[2];
	int num = 3;

	//procedura setup wykonuje się po resecie:
	void setup()
	{
	  for(int pin = 0; pin < num; pin++)
	  {
	    pinMode(ledPins[pin], OUTPUT);
	  }
	}

	//procedura loop – nieskończona pętla:
	void loop()
	{
	  digitalWrite(green, HIGH);
	  delay(4.5 * time);
	  for(int blink = 0; blink < 2; blink++)
	  {
	    digitalWrite(green, LOW);
	    delay(300);
	    digitalWrite(green, HIGH);
	    delay(300);
	  }
	  digitalWrite(green, LOW);
	  delay(300);
 	  digitalWrite(yellow, HIGH);
	  delay(time);
	  digitalWrite(yellow, LOW);
 	  digitalWrite(red, HIGH);
	  delay(8.25 * time);
	  digitalWrite(yellow, HIGH);
	  delay(0.75 * time);
	  digitalWrite(red, LOW);
	  digitalWrite(yellow, LOW);
	}


Traffic light for vehicles and pedestrians
==========================================

Opis
----

Program ilustruje działanie sygnalizacji świetlnej dla pojazdów oraz pieszych.


.. figure:: carandpedestrians.jpg
   :width: 600px
   :align: center

.. figure:: carandpedestrians_schem.jpg
   :width: 600px
   :align: center

Kod
---

.. code-block:: c++

	//pins:
	int traffic_lights[] = {8, 9, 10, 11, 12};
	int num = 5;
 
	//pedestrians:
	int P_red = traffic_lights[0];
	int P_green = traffic_lights[1];

	//vehicles:
	int V_green = traffic_lights[2];
	int V_yellow = traffic_lights[3];
	int V_red = traffic_lights[4];


	void setup()
	{
	  // pins output activation:
	  for(int i = 0; i < num; i++)
	  {
	    pinMode(traffic_lights[i], OUTPUT);
 	  }
	}

	void loop()
	{
 
	  //vehicle green:
	  digitalWrite(V_green, HIGH);

	  //pedestrian red:
	  digitalWrite(P_red, HIGH);
	  delay(7900);
 
	  //vehicle green blinking:
	  for(int i = 0; i < 3; i++)
	  {
	    digitalWrite(V_green, LOW);
	    delay(300);
	    digitalWrite(V_green, HIGH);
	    delay(300);
	   }
 
	  digitalWrite(V_green, LOW);
	  delay(300);
 
	  //vehicle yellow:
	  digitalWrite(V_yellow, HIGH);
	  delay(2000);
	  digitalWrite(V_yellow, LOW);
 
	  //vehicle red:
	  digitalWrite(V_red, HIGH);
	  delay(2000);

	  //pedestrian red / green:
	  digitalWrite(P_red, LOW);
	  digitalWrite(P_green, HIGH);
	  delay(7900);

	  //pedestrian green blinking:
	  for(int i = 0; i < 3; i++)
	  {
	    digitalWrite(P_green, LOW);
	    delay(300);
	    digitalWrite(P_green, HIGH);
	    delay(300);
	  }
 
	  digitalWrite(P_green, LOW);
	  delay(300);

	  //pedestrian red:
	  digitalWrite(P_red, HIGH);
	  delay(2000);
 
	  //vehicle red with yellow:
	  digitalWrite(V_yellow, HIGH);
	  delay(2000);
	  digitalWrite(V_yellow, LOW);
	  digitalWrite(V_red, LOW);

	  // pedestrian red:
	  digitalWrite(P_red, LOW);

	}

Traffic light - day and night version with pushbutton
=====================================================

Opis
----

Program jest symulacją prostej sygnalizacji świetlnej dla pojazdów oraz pieszych, zmieniającej się na tryb nocny przy wykorzystaniu przycisku.



.. figure:: TrafficLight_bb.jpg
   :width: 600px
   :align: center

.. figure:: TrafficLight_schem.jpg
   :width: 600px
   :align: center

Kod
---

.. code-block:: c++

	/* Program simulates one side of a simple crossroad
	with traffic lights for vehicles and pedestrians. */

	// pins:
	const int traffic_lights[] = {9, 8, 10, 11, 12};
	int num = 5;

	// pedestrians:
	int P_green = traffic_lights[0];
	int P_red = traffic_lights[1];

	// vehicles:
	int V_green = traffic_lights[2];
	int V_yellow = traffic_lights[3];
	int V_red = traffic_lights[4];

	//button
	const int button = 2;
	int current_value = HIGH;
	int previous_value = HIGH;
	int state = 0;

	void setup()
	{
 
	  //pins output activation:
	  for(int i = 0; i < num; i++)
	  {
	    pinMode(traffic_lights[i], OUTPUT);
	  }
 
	  //button
	  pinMode(button, INPUT);
	  digitalWrite(button, HIGH);
	  Serial.begin(9600);

	}

	void loop()
	{
 
	  //button
 	  current_value = digitalRead(button);
	  if(current_value == LOW && previous_value == HIGH)
	  {
	    state = 1 - state;
	    delay(20);
	  }
 	  previous_value = current_value;
 

 	  //day mode
	  if(state == 1)
	  {
	    //vehicle green:
	    digitalWrite(V_green, HIGH);
	    //pedestrian red:
	    digitalWrite(P_red, HIGH);
	    delay(7900);
	    //vehicle green blinking:	
	    for(int i = 0; i < 3; i++)
 	    {
	      digitalWrite(V_green, LOW);
	      delay(300);
	      digitalWrite(V_green, HIGH);
	      delay(300);
	    }
	    digitalWrite(V_green, LOW);
	    delay(300);
	    // vehicle yellow:
	    digitalWrite(V_yellow, HIGH);
	    delay(2000);
	    digitalWrite(V_yellow, LOW);
	    // vehicle red:
	    digitalWrite(V_red, HIGH);
	    delay(2000);
	    // pedestrian red / green:
	    digitalWrite(P_red, LOW);
	    digitalWrite(P_green, HIGH);
	    delay(7900);
	    // pedestrian green blinking:
	    for(int i = 0; i < 3; i++)
	    {
	      digitalWrite(P_green, LOW);
	      delay(300);
	      digitalWrite(P_green, HIGH);
	      delay(300);
	    }
	    digitalWrite(P_green, LOW);
	    delay(300);
	    // pedestrian red:
	    digitalWrite(P_red, HIGH);
	    delay(2000);
	    // vehicle red with yellow:
	    digitalWrite(V_yellow, HIGH);
	    delay(2000);
	    digitalWrite(V_yellow, LOW);
	    digitalWrite(V_red, LOW);
	    // pedestrian red:
	    digitalWrite(P_red, LOW);
	  }

 
 	  // night mode
	  if(state == 0)
	  {
	    digitalWrite(V_yellow, HIGH);
	    delay(500);
	    digitalWrite(V_yellow, LOW);
	    delay(500);
 	  }
	}

