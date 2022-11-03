# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu.([UC2](#uc2))
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu.([UC3](#uc3))

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.


## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję.
* [UC2](#uc2): Otrzymanie płatności za produkt
* [UC3](#uc3): Potwierdzenie wysyłki produktu.


[Kupujący](#ac2)
* [UC2](#uc1): Kupno/płatność za produkt 
* [UC3](#uc2): Otrzymanie produktu

---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.
2. System prosi o podanie danych produktu i ceny wywoławczej.
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą.
4. System weryfikuje poprawność danych.
5. System informuje o pomyślnym wystawieniu produktu na aukcję.

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane produktu.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 2.

---
<a id="uc2"></a>
### UC2: Kupno/płatność za produkt 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Scenariusz główny:**
1. [Kupujący](#ac2) prosi o podanie szczegółów płatności za produkt
2. System prosi [sprzedającego](#ac1) o podanie danych dla przekazania płatności
3. [Sprzedający](#ac2) podaję niezbędne dane do przekazywania płatności
4. System weryfikuje poprawność tych danych 
5. System prosi o płatności za produkt [kupującego](#ac2)
6. [Kupujący](#ac2) dokonuje płatność na kwotę ustaloną podczas aukcji 
7. System czeka na potwierdzenie płatności
8. System powiadamia [sprzedającego](#ac1) o dokonaniu udanej zapłaty za produkt     

**Scenariusze alternatywne:** 

4.A. Podano niepoprawne lub niekompletne dane.
* 4.A.1. System informuje o błędnie podanych danych.
* 4.A.2. Przejdź do kroku 3.

5.A. [Kupujący](#ac2) zrezygnował z płatności.
* 5.A.1. System informuje o brakie płatności [sprzedającego](#ac1).
* 5.A.2. Odnowienie aukcji.
 
 7.A. Nieotrzymanie potwierdzenia zapłaty 
 * 7.A.1 System informuje [kupującego](#ac2) o nieotrzymanie potwierdzenia płatności 
 * Przejdź do kroku 6.
---

<a id="uc3"></a>
### UC3: Potwierdzenie wysyłki produktu 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Scenariusz główny:**
1. System prosi [kupującego](#ac2) o podanie danych dla wysyłki produktu.
2. [Kupującego](#ac2) zgłasza do systemu dane do wysyłki produktu.
3. System weryfikuje poprawność wskazanych danych 
4. System prosi [sprzedającego](#ac1) o wybraniu daty wysyłki.
5. [Sprzedający](#ac1) wybiera wygodną dla niego datę dla przekazania produktu kurierowi i przekazuje systemowi.
6. System sprawdza dostępność kuriera na wybraną date 
7. System zamawia kuriera na podaną datę dla wysyłki produktu.
8. [Sprzedający](#ac1) oddaje produkt kurierowi.
9. system informuje [kupującego](#ac2) o przekazaniu produktu kurierowi 

**Scenariusze alternatywne:** 

2.A. [Kupujący](#ac2) zrezygnował z produktu.
* 2.A.1. System informuje [sprzedającego](#ac1) o rezygnacji z produktu.
* 2.A.2. System prosi [Kupującego](#ac2) o podanie danych dla zwrotu kwoty.
* 2.A.3. System wysyła kwotę [Kupującemu](#ac2).

3.A Podano niepoprawne lub niekompletne dane
  * 3.A.1. System informuje o błędnie podanych danych.
  * 3.A.2. Przejdź do kroku 2.

6.A. W terminie podanym przez sprzedawcę nie ma kurierów 
* 6.A.1. System informuje o braku kurierów.
* 6.A.2. Przejdź do kroku 5.


---

## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | Sprzedający | Kupujący|
| ------------------------------------------------- | ------ | ------- | ----------- | ------- |
| UC1: Wystawienia produktu na aukcję               |    C   |    C    |      R      |         |
| UC2: Kupno/płatność za produkt                    |    U   |         |      R      |    R    |
| UC3: Potwierdzenie wysyłki produktu.              |    D   |    D    |      R      |    R    |
 
