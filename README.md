# OredermanagementSystem
# Order Management System - UML Modeling Project

## Descriere

Acest proiect prezintă modelarea unui sistem de gestiune a comenzilor pentru un magazin online. Scopul proiectului este identificarea problemelor de design existente într-o implementare inițială și propunerea unei arhitecturi îmbunătățite prin refactorizare.

## Diagrame incluse

* Use Case Diagram
* Class Diagram (Before Refactoring)
* Class Diagram (After Refactoring)
* Sequence Diagram – Place Order
* Sequence Diagram – Cancel Order

## Probleme identificate în versiunea inițială

În structura inițială, clasa `OrderManager` centralizează majoritatea funcționalităților sistemului:

* gestionarea comenzilor;
* validarea stocului;
* procesarea plăților;
* trimiterea emailurilor;
* accesul la baza de date;
* generarea facturilor.

Această abordare conduce la următoarele probleme:

* God Class;
* High Coupling;
* Mixed Responsibilities;
* Direct Database Access;
* dificultate în testare și mentenanță.

## Soluția propusă

Pentru îmbunătățirea designului, responsabilitățile au fost separate în componente specializate:

* `OrderController` – gestionează cererile utilizatorilor;
* `OrderService` – conține logica principală de business;
* `PaymentService` – procesează plățile;
* `EmailService` – gestionează notificările prin email;
* `StockService` – verifică și actualizează stocul;
* `OrderRepository` și `ProductRepository` – gestionează accesul la baza de date.

## Beneficiile refactorizării

* respectarea principiului Single Responsibility Principle;
* reducerea cuplării dintre componente;
* creșterea coeziunii claselor;
* testare mai ușoară;
* întreținere și extindere mai simplă a aplicației.

## Fluxuri modelate

### Plasare comandă

Clientul trimite o cerere de plasare a unei comenzi. Sistemul verifică stocul, procesează plata, salvează comanda și trimite un email de confirmare.

### Anulare comandă

Clientul solicită anularea unei comenzi. Dacă aceasta nu a fost expediată, anularea este efectuată și se trimite o notificare. Dacă a fost deja expediată, sistemul refuză anularea.
