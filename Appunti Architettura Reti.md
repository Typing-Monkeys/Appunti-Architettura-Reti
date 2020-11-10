# Appunti Architettura Reti

**Di:** Antonio Strippoli

**Basati su:**

* Le slide del prof Osvaldo Gervasi
* Reti di Calcolatori (A. Tanenbaum)

**Revisore:** Alessio Amatucci

> Degli appunti per domarli, degli appunti per trovarli, degli appunti per ghermirli e nel buio incatenarli

## Obiettivi

L’obiettivo principale dei presenti appunti è la preparazione personale alla disciplina “Architettura Reti” insegnata dal prof. Osvaldo Gervasi dell’Università di Perugia.

Non conoscendo nulla riguardo l’architettura di una rete ed i suoi protocolli, il materiale reso disponibile dal docente (slides) si è rivelato insufficiente per un ripasso o uno studio nei casi in cui non sia stato presente a lezione. Anche altri appunti resi gentilmente disponibili da altri studenti non si sono rivelati chiari in molti punti.

Per cui, l’obiettivo di questi appunti è fornire una buona visione d’insieme di ogni argomento presente nel programma 2019/20 di Architettura Reti, tenendo a mente che il lettore potrebbe non aver mai letto nulla riguardo la suddetta materia e fornendo quindi anche definizioni basilari e spiegazioni base.

Ove opportuno, alcuni argomenti sono presentati in forma anche leggermente più estesa solamente a scopo di chiarimento. Tuttavia, altri argomenti sono particolarmente dettagliati e non tutti i dettagli sono ovviamente affrontati durante le lezioni. In questi casi, si è deciso di limitarsi ad una visione d’insieme più che sufficiente per la preparazione all’esame, ma che potrebbe non risultare esaustiva per gli studenti più curiosi. Questi argomenti sono singolarmente segnalati in ogni paragrafo qualora si volesse approfondire.

Inoltre, è bene segnalare che non viene trattato l’intero programma dell’anno 2019/2020, in quanto sono stati tralasciati i seguenti argomenti:

* Topologie di reti;
* Livello fisico/data link OSI (mezzi trasmissivi, ethernet, metodi di accesso al bus...);
* Frame Relay e ATM;
* VPN.

Si noti che è comunque possibile contribuire alla repository dedicata su GitHub ([https://github.com/CoffeeStraw/Appunti-Architettura-Reti](https://github.com/CoffeeStraw/Appunti-Architettura-Reti)) per ultimare e tenere aggiornati i presenti appunti, modificando il file .docx con cui sono stati scritti e rigenerando il .pdf utilizzato per la distribuzione.

## Indice

1. **Definizioni Generali**
    1. [Rete](#11-rete)
    2. [Internet](#12-internet)
    3. [Intranet](#13-intranet)
    4. [Extranet](#14-extranet)
    5. [ISP](#15-isp)
    6. [Protocollo](#16-protocollo)
    7. [Modello client/server](#17-modello-client/server)
    8. [Gateway](#18-gateway)
    9. [LAN](#19-lan)
    10. [MAN](110-MAN)
    11. [WAN](#111-WAN)
    12. [Servizio connection oriented](#112-servizio-connection-oriented)
    13. [Servizio connectionless](#113-servizio-connectionless)
    14. [Servizio best effort](#114-servizio-best-effort)
    15. [Quality of Service](#115-quality-of-service)
    16. [Unicasting, Multicasting e Broadcasting](#116-unicasting,-multicasting-e-broadcasting)
    17. [RFC](#117-rfc)

# 1 Definizioni Generali

## 1.1 Rete

Una **rete** è un insieme di dispositivi collegati in modo da permettere lo scambio di dati e la comunicazione tra più utenti. I dati vengono trasferiti sotto forma di **pacchetti** (a volte detti **PDU**, **Packet Data Unit**). 

Si distingue da un sistema distribuito, che invece appare ai propri utenti come un singolo sistema coerente. 

## 1.2 Internet

**Internet (o Internetwork)** è l’interconnessione di reti di varia natura che consente lo scambio di informazione rappresentata in forma digitale, cioè come sequenza di cifre binarie (bit).

Si può dire che **un computer è su Internet** se esegue la pila di protocolli TCP/IP, ha un indirizzo IP, e può spedire pacchetti IP a tutti gli altri computer su Internet (questi argomenti saranno trattati nei capitoli successivi).

## 1.3 Intranet

**Intranet** è un sistema telematico di collegamento effettuato con le stesse modalità di Internet, ma riservato a un circuito chiuso di utenti (all’interno di aziende, di strutture pubbliche, di organizzazioni di ricerca ecc.).

## 1.4 Extranet

L’**Extranet** è una Intranet estesa ad alcuni soggetti non operanti nella stessa rete (p.e. clienti, fornitori, consulenti).

## 1.5 ISP

Un **ISP (Internet Service Provider)** indica un’organizzazione o un’infrastruttura che mette a disposizione dei servizi inerenti a Internet per degli utenti, come la posta elettronica o l’accesso al World Wide Web.

## 1.6 Protocollo

Informalmente, un **protocollo** è un accordo, tra le parti che comunicano, sul modo in cui deve procedere la comunicazione. Violare il protocollo rende la comunicazione più difficile, se non del tutto impossibile.

Formalmente, un **protocollo** è un _insieme di regole_ che definisce l’interazione tra sistemi.

## 1.7 Modello client/server

Il **modello client/server** è un modello in cui sono presenti due entità (client e server), nel quale il client si connette al server mediante una rete, per la fruizione di un certo servizio (come la condivisione dati).

## 1.8 Gateway

Un gateway è un dispositivo di rete (generalmente un router) che collega due reti eterogenee. Il suo scopo principale è quello di veicolare i pacchetti di rete all’esterno di una rete locale.

## 1.9 LAN

Le **LAN (Local Area Network)** sono reti private installate all’interno di un singolo edificio o campus, con dimensione _fino a qualche Km_, ed hanno come scopo la condivisione di risorse (come stampanti) e lo scambio di informazioni.

## 1.10 MAN

Una **MAN (Metropolitan Area Network)** è una rete che copre un’intera città e collega più LAN geograficamente vicine. Di solito si tratta di singole filiali di un’azienda, che vengono connesse ad una MAN attraverso l’affitto di linee dedicate.

## 1.11 WAN

Una **WAN (Wide Area Network)** è una rete che copre un’area geograficamente estesa, spesso una nazione o un continente. Il numero di reti locali o singoli computer che si possono connettere ad una singola WAN è teoricamente illimitato.

## 1.12 Servizio connection oriented

Un servizio **connection oriented (orientato alla connessione)** è un servizio di rete in cui l’utente che lo vuole usare deve _stabilire una connessione_ (mediante la creazione di un circuito, che sia fisico o virtuale), _usarla_ e quindi _rilasciarla_. Nella maggior parte dei casi, l’ordine dei bit inviati è conservato e arrivano nella sequenza con cui sono stati trasmessi, che rende questa categoria di servizi **affidabile**.

Un’analogia utile per capire, è quella tra il servizio connection oriented e il **sistema telefonico**. Per parlare con qualcuno si deve prendere il telefono, comporre il numero, parlare e poi riagganciare.

## 1.13 Servizio connectionless

Un servizio **connectionless (senza connessione)** si contrappone al servizio con connessione e non viene quindi stabilita una connessione. I dati vengono instradati in maniera indipendente l’uno dall’altro, senza verificare che il destinatario sia raggiungibile e senza controllare che i dati arrivino nell’ordine desiderato, che rende questa categoria di servizi **inaffidabile**.

Un’analogia utile per capire, è quella tra il servizio connectionless e la **posta**. Ogni messaggio (lettera) trasporta l’indirizzo completo del destinatario ed è instradato attraverso il sistema postale in modo indipendente dagli altri. Normalmente, quando si mandano due messaggi alla stessa destinazione, il primo inviato è anche il primo ad arrivare; ma è possibile che incontri un ritardo, e quindi arrivi dopo il secondo.

## 1.14 Servizio best effort

Un servizio **best effort** (**massimo impegno**, interpretato “come va, va”) è un servizio inaffidabile che non offre alcuna garanzia di consegna dei pacchetti (alcuni di essi possono perdersi e avere bisogno di essere ritrasmessi, o andare fuori sequenza) né di controllo di errore, di flusso e di congestione.

## 1.15 Quality of Service

Il termine **Quality of Service** (abbreviato **QoS**) è utilizzato per indicare i parametri usati per caratterizzare la qualità del servizio offerto da una rete (ad esempio perdita di pacchetti, ritardo), o gli strumenti o tecniche per ottenere una qualità di servizio desiderata. Si contrappone al termine best effort.

## 1.16 Unicasting, Multicasting e Broadcasting

**Unicasting, Multicasting e Broadcasting** sono delle metodologie per la trasmissione dei dati. La distinzione avviene in base al numero dei ricevitori:

* Unicasting: trasmissione di dati tra un trasmettitore e un ricevitore (1-1);
* Multicasting: trasmissione di dati tra un trasmettitore ed un sottoinsieme di tutte le macchine della rete (1-n);
* Broadcasting: trasmissione di dati tra un trasmettitore e tutte le macchine della rete (1-tutti).

## 1.17 RFC

Gli **RFC (Request For Comment)**, sono una serie di rapporti tecnici numerati cronologicamente che riportano informazioni o specifiche riguardanti nuove ricerche, innovazioni e metodologie di Internet. Sono redatti da un organismo internazionale chiamato **IETF (Internet Engineering Task Force)**, e sono tutti consultabili su [www.ietf.org/rfc/](www.ietf.org/rfc/). 
