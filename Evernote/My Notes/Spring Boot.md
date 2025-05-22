---
---
### Cosa succede quando un'applicazione Spring Boot parte?

Quando un'applicazione Spring Boot parte, accadono diverse cose:

1. Bootstrapping del Contesto Applicativo: Spring Boot avvia un contesto applicativo (un'istanza di `ApplicationContext`). Questo contesto è il contenitore IoC che gestisce i bean.
	
2. Scansione dei Componenti: Spring Boot scansiona il classpath per trovare classi annotate con annotazioni come `@Component`, `@Service`, `@Repository`, e `@Controller`, che indicano che queste classi dovrebbero essere gestite come bean nel contenitore IoC.
	
3. Creazione e Iniezione dei Bean: Una volta identificate le classi, Spring crea istanze di queste classi (bean) e risolve le loro dipendenze, iniettando i bean necessari nelle classi che ne hanno bisogno. Questo può avvenire tramite iniezione per costruttore, iniezione per setter, o iniezione di campo (field injection).
	
4. Configurazione Automatica: Grazie alla configurazione automatica, Spring Boot configura automaticamente molti aspetti dell'applicazione, basandosi sulle dipendenze trovate nel classpath. Ad esempio, se hai una dipendenza per un database, Spring Boot configura automaticamente una connessione al database.
	
5. Avvio del Server Web (se applicabile): Se stai costruendo un'applicazione web, Spring Boot avvia un server web incorporato come Tomcat, Jetty o Undertow. Il server web avvia e mette in ascolto le richieste HTTP.
	
6. Esecuzione della Logica di Avvio: Se hai definito dei bean di tipo `CommandLineRunner` o `ApplicationRunner`, il loro metodo `run` viene eseguito dopo che il contesto applicativo è stato avviato, permettendoti di eseguire del codice all'avvio dell'applicazione.
	

|     |     |
| --- | --- |
| Concetto | Descrizione |
| Spring Framework | Un framework Java che fornisce un'infrastruttura completa per lo sviluppo di applicazioni Java. |
| Spring Boot | Un'estensione del framework Spring che semplifica lo sviluppo di applicazioni stand-alone, production-grade Spring-based con configurazione minima. |
| Inversion of Control (IoC) | Un principio di programmazione che sposta il controllo degli oggetti o delle porzioni di programma ad un contenitore o framework. |
| Dependency Injection (DI) | Un design pattern che consente di creare istanze di classi e di iniettarle nelle classi che ne hanno bisogno, facilitando la gestione delle dipendenze. |
| Application Context | Un contenitore avanzato di Spring che gestisce la configurazione e il ciclo di vita dei bean. |
| Bean | Un oggetto gestito dal contenitore IoC di Spring. |
| Aspect-Oriented Programming (AOP) | Un paradigma di programmazione che aumenta la modularità separando le preoccupazioni trasversali (cross-cutting concerns), come la logging, la gestione delle transazioni, ecc. |
| Spring MVC | Un framework che fornisce un'architettura Model-View-Controller per lo sviluppo di applicazioni web. |
| Spring Data | Un progetto che semplifica l'accesso ai database relazionali e NoSQL. |
| Spring Security | Un framework che fornisce l'autenticazione, l'autorizzazione e altre funzionalità di sicurezza per le applicazioni Spring. |
| Spring Boot Starter | Un set di dipendenze preconfigurate per iniziare rapidamente lo sviluppo di applicazioni Spring Boot. |
| Spring Boot Auto-Configuration | Una funzionalità che consente di configurare automaticamente i bean necessari in base alle dipendenze presenti nel classpath. |
| Spring Boot Actuator | Un insieme di endpoint che consentono di monitorare e gestire l'applicazione in produzione. |
| Spring Boot CLI | Un'interfaccia a riga di comando che permette di sviluppare applicazioni Spring Boot con codice Groovy. |
| Spring Boot DevTools | Una serie di strumenti per migliorare l'esperienza di sviluppo, come il live reload e la configurazione automatica in modalità di sviluppo. |
| Spring Boot Profiles | Un meccanismo per separare la configurazione in base all'ambiente, ad esempio, sviluppo, test, e produzione. |
| Spring REST | Supporto per creare servizi RESTful in modo semplice. |
| Spring Batch | Un framework per l'elaborazione di grandi volumi di dati attraverso operazioni batch. |
| Spring Cloud | Un insieme di strumenti per costruire applicazioni distribuite e microservizi, integrando sistemi di gestione delle configurazioni, service discovery, circuit breakers, ecc. |
| Spring WebFlux | Un framework per applicazioni reattive basato su Reactor, per costruire applicazioni non bloccanti e ad alte prestazioni. |
