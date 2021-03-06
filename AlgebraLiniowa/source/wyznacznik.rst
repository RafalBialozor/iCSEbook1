﻿Wyznacznik
==========

Definicja
---------


Przyjmujemy aksjomatyczną definicję wyznacznika, sformułowaną w
zapisie kolumnowym macierzy (czyli :math:`C_j` oznacza j-tą kolumnę macierzy):

.. admonition:: **Definicja aksjomatyczna wyznacznika**

   **Def.** Wyznacznik  stopnia  *n*  jest  funkcją  :math:`\det :M_n (K) \to K`  spełniającą  warunki:


   1.) :math:`\det (C_{ 1} , \ldots ,C_j  +  C'_j , \ldots ,C_n ) = \det (C_{ 1} , \ldots ,C_j , \ldots ,C_n ) + \det (C_{ 1} , \ldots ,C'_j , \ldots ,C_n )`.
   
   2.) :math:`\det (C_{ 1} , \ldots ,\lambda C_j , \ldots ,C_n ) = \lambda  \cdot \det (C_{ 1} , \ldots ,C_j , \ldots ,C_n ), \,  \lambda  \in K, \quad  j = 1,2, \ldots ,n`.

   3.) :math:`C_j = C_{j + 1} \Rightarrow \det (C_{ 1} , \ldots ,C_j,C_{j + 1} , \ldots ,C_n ) = 0, \quad j = 1,2, \ldots ,n - 1`.

   4.) :math:`\det {\boldsymbol{I}} = 1`,  gdzie   :math:`\boldsymbol{I}`   –   macierz  jednostkowa:

   .. math::

      {\boldsymbol{I}} = \left( {\begin{array}{*{20}c} 1 & 0 & \ldots & 0 \\ 0 & 1 & \ldots & 0 \\ \ldots & \ldots & \ldots & \ldots \\ 0 & 0 & \ldots & 1 \\ \end{array}} \right).


Zapis:

.. math::

   \;\det {\boldsymbol{A}} = \det (\alpha _{ij} )_{n \times n}  = \det \left( {\begin{array}{*{20}c}
   {\alpha _{  11} }  & {\alpha _{  12} }  &  \ldots   & {\alpha _{  1n} }   \\
   {\alpha _{  21} }  & {\alpha _{  22} }  &  \ldots   & {\alpha  _{2n} }   \\
   { \ldots }  &  \ldots   &  \ldots   &  \ldots    \\
   {\alpha _{  n  1} }  & {\alpha _{  n2} }  &  \ldots   & {\alpha _{ n n} }   \\
   \end{array}} \right) = \left| {\begin{array}{*{20}c}
   {\alpha _{  11} }  & {\alpha _{  12} }  &  \ldots   & {\alpha _{  1n} }   \\
   {\alpha _{  21} }  & {\alpha _{  22} }  &  \ldots   & {\alpha  _{2n} }   \\
   \ldots   &  \ldots   &  \ldots   &  \ldots    \\
   {\alpha _{  n  1} }  & {\alpha _{  n2} }  &  \ldots   & {\alpha _{ n n} }   \\
   \end{array}} \right|.


Uwagi:


1°	Wyznacznik  jest  określony  tylko  dla  macierzy  kwadratowych  (m = n).
	Nie  istnieje  wyznacznik  macierzy  prostokątnej  niekwadratowej.

2°	Macierz  i  wyznacznik  macierzy  są  zupełnie  różnymi  obiektami  matematycznymi,
	co  powinno  znaleźć  odbicie  w  zapisie  (nawiasy dla macierzy, proste kreski dla wyznacznika).

3°	Z  definicji  nie  wynika  istnienie  funkcji  spełniającej  wymienione  postulaty  ani  jej
	jednoznaczność.  Definicja  nie  podaje  też  praktycznego  sposobu  wyliczania  wyznacznika.
	W  dalszym  ciągu  wykażemy,  że  istnieje  dokładnie  jedna  funkcja  spełniająca  postulaty  		definicji  oraz  wyprowadzimy  wzory  dla  efektywnego  obliczania  wyznaczników.

4°	Jeżeli   :math:`{\boldsymbol{A}},{\boldsymbol{B}} \in M_n (K), \quad \lambda \in K`,
	to   :math:`\det ({\boldsymbol{A}} + {\boldsymbol{B}}) \ne \det {\boldsymbol{A}} + \det {\boldsymbol{B}}, \quad  \det (\lambda {\boldsymbol{A}}) \ne \lambda \det {\boldsymbol{A}} \quad (n > 1)`,
	tzn.  wyznacznik  nie  jest  funkcją  liniową.
	Natomiast,  dla  :math:`{\boldsymbol{A}} = (C_{ 1} ,C_{ 2} , \ldots ,C_n )`  mamy  :math:`\lambda {\boldsymbol{A}} = (\lambda C_{ 1} ,\lambda C_{ 2} , \ldots ,\lambda C_n )`,
	wobec  czego  :math:`\det (\lambda {\boldsymbol{A}}) = \lambda ^n  \cdot \det {\boldsymbol{A}}, \quad n \in \boldsymbol{N}`.





Jawna postać wyznacznika
------------------------

.. admonition:: **Twierdzenie** 

   Istnieje dokładnie jedna funkcja :math:`\det :M_n (K) \to K`,
   spełniająca warunki 1. - 4.  Mianowicie, dla macierzy
   :math:`{\boldsymbol{A}} = (\alpha _{ij} )_{n \times n}` :

   .. math::

      \det {\boldsymbol{A}} = \sum\limits_{\sigma \in \Pi (n)}
      {{\mathop{\rm sgn}} \sigma } \cdot \alpha _{\sigma (1),1} \alpha
      _{\sigma (2),2} \ldots \alpha _{\sigma (n),n} \quad


Postać ta jest też zwana **rozwinięciem permutacyjnym wyznacznika.**
Zastosujmy ją do obliczenia wyznacznika macierzy o rozmiarze :math:`2\times2`:

.. math::

   A = \left(\begin{array}{rr}
      a_{11} & a_{12} \\
      a_{21} & a_{22}
     \end{array}\right)


Mamy dwie możliwe permutacje wskaźników: :math:`\sigma_1 = (1,2) \to
(1,2)` oraz :math:`\sigma_2 = (1,2) \to (2,1)`, o znakach
odpowiednio: +1 i -1. Napiszmy więc:

.. math::

   \det(A) = {{\mathop{\rm sgn}} \sigma_1 } a_{1\sigma_1(1)}
   a_{2\sigma_1(2)} - {{\mathop{\rm sgn}} \sigma_1 } a_{1\sigma_1(1)}
   a_{2\sigma_1(2)} = a_{11} a_{22} - a_{12} a_{21}




.. admonition:: **Poeksperymentuj z Sage**

   | W poniższym programie została zaimplementowana jawna postać
   | wyznacznika w Sage.  

                1) Wypróbuj działanie na różnych macierzach. 
                2) W Sage wyznacznik macierzy A jest obliczany przez funkcję A.det(), porównaj wyniki.
                3) Suma w poniższym wyrażeniu jest po wszystkich
                   permutacjach liczb :math:`1,\dots,N`. Oszacuj czas
                   w latach obliczenia wyznacznika macierzy
                   :math:`20\times20`.  Liczbę permutacji można
                   otrzymać np. wykonując
                   polecenie ``Permutations(N).cardinality()`` a do
                   oszacowania można przyjąć, że komputer wykona sumę
                   po :math:`10^9` w ciągu sekundy.

.. sagecellserver::

   
   N = 3
   A = random_matrix(QQ,N)
   detA = sum ( [ p.signature()*prod( [A[p[i]-1,i] for i in range(N)] ) for p in Permutations(N) ] )
   print detA


Rozwinięcie Laplace'a
---------------------

Praktyczną metodą obliczenia wyznacznika jest zastosowanie procedury
rekurencyjnej zwanej rozwinięciem Laplace'a. 

Niech :math:`\boldsymbol{M_{ij}}` będzie macierzą powstałą z macierzy :math:`\boldsymbol{A}` po wykreśleniu i-tego wiersza i j-tej kolumny. Ponadto niech:

.. math::

   \boldsymbol{A_{ij}} = (-1)^{i+j}\det(\boldsymbol{M_{ij}})
   
Symbol :math:`A_{ij}` jest zwany dopełnieniem
algebraicznym elementu :math:`a_{ij}` macierzy
:math:`\boldsymbol{A}`.

Przy powyższych oznaczeniach wyznacznik macierzy :math:`\boldsymbol{A}` wynosi:

.. math::
   :label: Laplace

   \det \boldsymbol{A} = a_{1j}A_{1j}+a_{2j}A_{2j}+...+a_{Nj}A_{Nj}


dla dowolnego :math:`j\in(1,N)`.

Wzór :eq:`Laplace` zwany jest rozwinięciem Laplace'a wyznacznika względem j-tej kolumny.


.. admonition:: **Poeksperymentuj z Sage**

   Poniższy przykład w Sage definiuje rozwinięcie Laplace'a za pomocą rekurencji. 
   Poeksperymentuj z kodem rozwijając macierze względem różnych kolumn. 

.. sagecellserver::

    def sub_mat(A,i,j):
        "procedura wycinajaca z macierzy i-ty wiersz i j-ta kolumne"
        return block_matrix( 2,2,\
          [A.submatrix(0,0,i,j),\
           A.submatrix(0,j+1,i,A.ncols()-j-1),\
           A.submatrix(i+1,0,A.nrows()-i-1,j),\
           A.submatrix(i+1,j+1,A.nrows()-i-1,A.ncols()-j-1)],\
          subdivide=False)

    def det1(A,verbose=True,ncol=0):
        """
        Rekurencyjna definicja wyznacznika, 
        """
        if A.ncols()==1:
            return(A[0,0])
        a=A.column(ncol)
        detA=0
        for i,el in enumerate(a):
            if verbose:
                s="\quad"*(3*(4-A.ncols()))# trik wcinajacy
                html.table([["$%s$" % s,el," x ",sub_mat(A,i,ncol)]])
            detA+=(-1)^(i+ncol)*el*det1(sub_mat(A,i,ncol),ncol=ncol)
        return detA
    
    A = random_matrix(QQ,3)
    print det(A)
    det1(A)


Praktyczne obliczanie wyznacznika
---------------------------------

Zarówno rozwinięcie Laplace'a jak i jawna postać wzoru na wyznacznik
dla dużych macierzy implikują wykonanie zbyt wielu operacji
arytmetycznych. Jednak pamiętając o własnościach wyznacznika można:

* zauwazyć, że wyznacznik macierzy trojkątnej jest równy iloczynowy elementów na jej diagonali
* zauważyć, że każdą macierz da się sprowadzić do iloczynu macierzy trójkątnych oraz operacji permuatacji.

Z powyższych obserwacji wynika, ze praktycznie, by wyliczyć wyznacznik najlepiej przeprowadzić rozkład LU macierzy i  


A = random_matrix(QQ,3)

Własności  funkcji  det,  wynikające  z  definicji
--------------------------------------------------


I.) Jeżeli jakaś kolumna macierzy składa się z samych zer, to wyznacznik znika:

   .. math::  

      C_j  = \theta \Rightarrow \det (C_{ 1} , \ldots ,C_j , \ldots ,C_n ) = 0, \quad  j = 1,2, \ldots ,n.


II.) Przestawienie dowolnych dwóch kolumn zmienia znak wyznacznika.

   .. math:: 

      \det (C_{ 1} , \ldots ,C_j , \ldots ,C_k , \ldots ,C_n ) = -
      \det (C_{ 1} , \ldots ,C_k , \ldots ,C_j , \ldots ,C_n ) 

   dla :math:`j < k,j, \quad k = 1,2, \ldots ,n`.



III.) Gdy jakiekolwiek dwie kolumny macierzy są równe, to wyznacznik znika.

   .. math::

       C_j = C_k \Rightarrow \det (C_{ 1} , \ldots ,C_j , \ldots ,C_k ,
       \ldots ,C_n ) = 0

   dla :math:`j < k, \quad j, k = 1,2, \ldots ,n`.
   
IV.) Twierdzenie  Cauchy-ego:   

    .. math::

       \det ({\boldsymbol{AB}}) = \det {\boldsymbol{A}} \cdot \det
       {\boldsymbol{B}}.


V.) Wniosek z tw. Cauche-ego:

    .. math::
       :label: SAS

       \det {\boldsymbol{S^{-1}AS}} = \det {\boldsymbol{S^{-1}}}\det
       {\boldsymbol{A}} \det {\boldsymbol{S}} =\\

       \det {\boldsymbol{S^{-1}}}\det {\boldsymbol{S}} \det
       {\boldsymbol{A}} = \det {\boldsymbol{A}} .

    Macierze podobne mają ten sam wyznacznik. Ponieważ macierz
    :math:`\boldsymbol{S^{-1}AS}` jest reprezentacją macierzy
    :math:`\boldsymbol{A}` w bazie składającej się z kolumn macierzy
    :math:`\boldsymbol{S}` to własność :eq:`SAS` oznacza
    niezmnienniczność wyznacznika przy zmianie bazy.


VI.) Wyznacznik macierzy transponowanej:

    .. math::
       :label: AT

       \det {\boldsymbol{A}}^{\rm{T}}  = \det {\boldsymbol{A}}.




**Wniosek** wynikający z równości :eq:`AT`: 
 
Każde twierdzenie dotyczące wyznaczników pozostaje słuszne, jeżeli
słowa "kolumna" zamienić na "wiersz" i odwrotnie.  W szczególności,
samą definicję wyznacznika można podać w terminach wierszy, dochodząc
do wzoru:

.. math::

   \det {\boldsymbol{A}} = \sum\limits_{\sigma \in \Pi (n)}
   {{\mathop{\rm sgn}} \sigma \cdot \alpha _{ 1,\sigma (1)} \alpha _{
   2,\sigma (2)} \ldots \alpha _{ n,\sigma (n)} } .


.. admonition:: **Poeksperymentuj z Sage**

   Poeksperymentuj testując wszystkie powyższe własności wyznacznika
   na losowych macierzach:

.. sagecellserver::

   A = random_matrix(QQ,3)
   show(A),show(B)
   print "wyznacznik iloczynu:", det(A)*det(B),det(A*B)
   print "wyznacznik sumy:", det(A)+det(B),det(A+B)
