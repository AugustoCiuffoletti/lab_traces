### Tracce di traffico internet per protocolli specifici

Questo repository contiene alcune tracce utili per lo studio dei protocolli di comunicazione.

Una **traccia** è la registrazione dei pacchetti scambiati su una collegamento di rete. I pacchetti vengono registrati nella traccia come una sequenza di bit difficilmente intepretabili senza l'aiuto di applicazioni specifiche. Wireshark, che utilizziamo nel corso per catturare pacchetti, è in grado di interpretare una traccia e di descriverne nel dettaglio i pacchetti.

Per interpretare una traccia si utilizza il comando *Open* del menu *File* di Wireshark, navigando poi sul file contenente la traccia che si vuole visualizzare.

La traccia contiene tutto il traffico, non solo i pacchetti interessanti. Per selezionare i pacchetti che si vogliono analizzare si imposta un **filtro di visualizzazione** nel box sopra la finestra principale di Wireshark. Un filtro descrive una proprietà dei pacchetti che si vogliono selezionare, ad esempio l'appartenenza ad un certo protocollo. Premendo *a capo*, o la freccia bianca su campo azzurro a destra, il filtro viene impostato, e nella finestra in basso compaiono solo i pacchetti che lo soddisfano. Selezionando un pacchetto specifico questo viene *esploso* nella finestra sottostante, mostrando i vari payload incapsulati. Ciascuno di questi può essere selezionato, ed il contenuto dello header compare nella finestra ancora sottostante.

La sintassi del filtro di visualizzazione è relativamente semplice, conoscendo il contenuto dell'intestazione dei protocolli. Si tratta di una espressione logica, del genere di quelle che si trovano nei linguaggi di programmazione.

Nel caso semplice che si desideri selezionare i pacchetti appartenenti ad un protocollo, si inserirà nel box il nome del protocollo. Ad esempio la stringa `icmp` seleziona tutti i pacchetti del protocollo ICMP.

Nel caso in cui sia necessario limitare la visualizzazione a particolari pacchetti di un certo protocollo, se ne specifica il valore di un campo. Ad esempio, per i pacchetti TCP con destinazione la porta 80, scriverò `tcp.dst.port == 80`. Se vogliamo pacchetti con origine o destinazione sulla porta 80, possiamo specificare `tcp.port == 80`, oppure `tcp.dest.port == 80 and tcp.src.port == 80`. Possono essere anche inserite proprietà relative a protocolli diversi. Ad esempio `tcp.dst.prot == 80 and ip.dst == 172.16.1.3` per i pacchetti dirett all'host con indirizzo IP 172.16.1.3 sulla porta 80.

Per un elenco completo dei filtri di visualizzazione Wireshark: https://packetlife.net/media/library/13/Wireshark_Display_Filters.pdf
Per istruzioni più approfondite: https://gitlab.com/wireshark/wireshark/-/wikis/DisplayFilters
