# PalazzoBernabei-VR
Repository dedicata ai progetti di tesi che riguardano la ricostruzione di Palazzo Bernabei.

## Struttura Repository
Questa Repository è divisa in due cartelle:
1. **Cartella Blender**: contiene i file .blend dove si possono trovare tutti i modelli utilizzati all'interno del progetto, in particolare:
   - **Facciata_ogg_ingresso.blend**: file dove si possono trovare tutti i modelli relativi alla facciata del Palazzo;
   - **Ingresso_Palazzo_Bernabei.blend**: file dove si possono trovare tutti i modelli relativi all'atrio del Palazzo e alla terrazza;
   - **aule_palazzo_bernabei.blend**: file dove si possono trovare tutti i modelli relativi alle stanze al piano inferiore che sono: l'ingresso per le aule, il laboratorio immersivo, il secondo laboratorio di informatica e l'aula insonorizzata;
   -  **stemmi_scansionati.blend**: file dove si possono trovare tutti i modelli scansionati con lo scanner 3D;
2. **Cartella Unity**: contiene a sua volta la cartella Progetto-Assisi, che contiene tutti i file relativi al progetto creato con Unity.
3. **Cartella ImmaginiReadme**: contiene tutte le immagini utilizzate per la scrittura del README.

## Requisiti preliminari
Per lavorare a questo progetto è necessaria una versione di Unity uguale o superiore alla 2022.3.16f1 (LTS), dato che è quella utilizzata per lo sviluppo. Inoltre deve essere utilizzato un visore Meta Quest 2, Meta Quest 3, oppure Meta Quest Pro, ma il progetto in sé è stato pensato per essere eseguito su un Meta Quest 3.

## Cartella Progetto-Assisi
Nella cartella Assets relativa al progetto realizzato in Unity si possono trovare le seguenti sottocartelle:
- **CharacterPack Lowpoly** e **Distant Lands**: contiene asset scaricati dallo store di Unity che sono stati usati per i modelli delle persone che si possono trovare nel laboratorio immersivo.
- **Decorative Plants** e **Stylized Plants Kit**: contiene asset scaricati dallo store di Unity che sono stati usati per i modelli delle piante che si possono trovare nella terrazza.
- **Models**: contiene tutti i modelli importati da Blender, suddivisi nelle sottocartelle: aula1 (laboratorio immersivo), aula 2 (secondo laboratorio di informatica), aula3 (aula immersiva), ingressoAule, corridoio (struttura di collegamento tra le aule), Citta (modelli usati per le case inserite nell'oggetto Terreno), Ingresso, Terrazzo e Facciata. La stessa suddivisione si troverà anche nella Hierarchy su Unity.
-**Materials**: contiene tutti i materiali applicati ai modelli.
- **Scenes**: contiene 4 scene:
    1. **Aule**: scena relativa sollo alle stanze al piano inferiore;
    2. **Facciata**: scena relativa sollo alla facciata del Palazzo;
    3. **Ingresso**: scena relativa sollo all'atrio del Palazzo e alla terrazza;
    4. **Palazzo Bernabei**: scena che contiene il Palazzo completo;
- **Textures**: contiene tutte le texture utilizzate per creare i materiali. 

## Configurazione e implementazione del visore Meta Quest 3 su Unity:
### Configurazione
Se il visore viene acceso per la prima volta è necessario seguire i passaggi che vengono indicati nel Meta Quest stesso quando viene indossato.
Innanzitutto è necessario abilitare la modalità sviluppatore, in modo tale da poter connettere il visore al computer e installare le build di prova dell'applicazione. Per fare ciò prima di tutto è necessaria la creazione di un account sviluppatore da questo link https://developer.oculus.com/. Successivamente deve essere creata un'organizzazione cliccando "Manage Your App" nella scheda "Utilize insights with Developer Dashboard".
![Sito Oculus](/ImmaginiReadme/sito_oculus.png)

Dopo aver fatto ciò, dall'App mobile scaricata durante il setup iniziale, si può abilitare la modalità sviluppatore per il visore.
Per gestire il visore quando è collegato al computer in maniera più comoda si può installare l'App Meta Quest Developer Hub.
A questo punto per sviluppare un'App su Unity che funzioni per il visore è necessario installare i moduli Android per la versione che si sta utilizzando. Per farlo bisogna andare nella sezione "Installs" dello Unity Hub, cliccare sull'icona delle impostazioni della versione e infine cliccare su "Add Modules". Una volta fatto, selezionare "Android Build Support" e poi cliccare sul pulsante "Install".
![Add Modules](/ImmaginiReadme/add_modules.png)

Successivamente si può aprire il progetto su Unity, andare nelle Build Settings, recarsi sulla scheda dedicata ad Android e cambiare piattaforma. Quando il processo di cambio è finito, se il visore è collegato si può scegliere come dispositivo su cui installare le build e successivamente cliccare su "Build" o "Build And Run" per costruire l'App.
![Add Modules](/ImmaginiReadme/build_settings.png)

L'ultima operazione da fare è andare nelle Project Settings, recarsi nella sezione "XR Plug-in Management", poi nella scheda dedicata ad Android e abilitare la checkbox "Oculus" per avere la possibilità di installare i pacchetti dedicati al Meta Quest.
![Add Modules](/ImmaginiReadme/project_settings_xrplugin.png)

Anche se nel progetto caricato in questa Repository i pacchetti necessari dovrebbero già essere installati, se ci fossero problemi va importato dall'Asset Store il pacchetto "Meta XR All-In-One SDK".

### Implementazione
Per implementare i movimenti di base dell'utente e la gestione delle interazioni è necessario aggiungere nella Hierarchy 2 prefab: OVRPlayerController e OVRCameraRigInteraction. Questi sono 2 asset saranno disponibili dopo aver importato il pacchetto sopracitato e si potranno trovare cercandoli tra i file del progetto nella finestra "Project" di Unity, filtrando la ricerca con l'opzione "In Packages".
Dopo aver aggiunto l'OVRPlayerController alla scena, bisogna aggiungere l'OVRCameraRigInteraction come figlio sostituendola a l'OVRCameraRig che si trova di base. Di conseguenza si dovrebbe avere una gerarchia come quella mostrata nell'immagine.
![Add Modules](/ImmaginiReadme/prefab_hierarchy.png)

Dopo aver importato i prefab si devono modificare alcune cose:
- nell'inspector di OVRPlayerController bisogna cambiare il parametro "Height" per simulare l'altezza di un essere umano;
- sempre nell'inspector di OVRPlayerController disabilitare la checkbox "Snap Rotation";
- nel prefab TeleportControllerInteractor, che si trova sia in LeftController che in RightController, disabilitare gli script "Teleport Interactor", "Teleport Arc Gravity" e "Active State Tracker";
- nel prefab ControllerTurnerInteractor cambiare l'opzione "Turn Method" da "Snap" a "Smooth";

Una volta fatte queste modifiche i movimenti di base e interazioni dovrebbero essere funzionanti.
Per realizzare un'interazione con un oggetto generico è necessario aggiungere un GameObject Interaction SDK. Per fare ciò si deve cliccare il tasto destro del mouse sull'oggetto che si vuole rendere interagibile, andare sulla sezione "Interaction SDK" e scegliere il tipo di interazione. Tramite la finestra che apparirà automaticamente si dovranno selezionare le componenti necessarie a far funzionare l'interazione.
![Add Modules](/ImmaginiReadme/finestra_interaction.png)

Alcune interazioni particolari hanno delle accortezze in più. 
Ad esempio per quanto riguarda l'apertura delle porte bisogna fare alcune operazioni:
- aggiungere all'oggetto che rappresenta la porta la componente HingeJoint, che vincola il movimento di rotazione rispetto ad un pivot;
- aggiungere al nuovo oggetto Interaction SDK (in questo caso ISDK_HandGrabInteraction) lo script "One Grab Rotate Transformer" che controlla il movimento nel momento in cui sta avvenendo l'interazione e sulla sezione "Optionals" -> "Pivot Transform" associare un GameObject vuoto che rappresenta il pivot;
![One Grab Rotate Transformer](/ImmaginiReadme/interaction_sdk_2.png)
- sempre nell'oggetto Interaction SDK, nello script "Grabbable" -> "Optionals" -> "One Grab Transformer" associare l'oggetto stesso;
![Grabbable](/ImmaginiReadme/interaction_sdk_1.png)

## Unity Version Control
Per collaborarare in più persone nella stessa scena è stato utilizzato lo Unity Version Control, parte della suite di strumenti offerti da Unity, che permette (nella sua versione gratuita) la collaborazione fino a tre partecipanti con progetti non superiori a 2GB di spazio. Lo strumento è installabile all'interno del progetto dal Package Manager (sezione Packages - Unity). Ulteriori informazioni sono disponibili al link https://unity.com/solutions/version-control.
Il Version Control funziona essenzialmente come Git, permettendo di creare un Branch per ogni partecipante per non intaccare il lavoro degli altri, pushare le modifiche nel branch quando sono presenti cambiamenti pendenti (Pending Changes), navigare fra i vari Changeset (cioè i commit effettuati) e anche fra Branch diversi, e ovviamente fare il Merge fra Branch per unire in un unico Changeset tutti gli aggiornamenti effettuati da ogni partecipante, con la possibilità di risolvere i possibili conflitti.

### Configurazione
Dato che si è usato un sistema diverso da Git per quanto riguarda questi aspetti, è bene tenere separata la cartella scaricata da GitHub, copiandola in locale nella propria workspace di lavoro e poi continuare da lì, lasciando quella di GiHub inalterata, per evitare problemi o fare le stesse operazioni due volte. Si consiglia quindi di scaricare solo il file zip da Github e non di configurare una cartella come repository Git locale. Per collegare il progetto ad una repository dello Unity Version Control bisogna prima creare quest'ultima. Per fare ciò si deve andare a questo link https://cloud.unity.com/home/login, fare il login, andare nella sezione "Products"->"DevOps" e cliccare sul pulsante "Launch". Una volta fatto questo navigare a "UVCS Organizations" e cliccare il pulsante "Subscribe" per effettuare il processo di creazione dell'organizzazione. Una volta creata si può inizializzare una nuova repository e, se il lavoro viene svolto in gruppo, invitare nuovi membri all'organizzazione (nella sezione "DevOps"->"Seats"). Una volta creata la repository, va collegata al progetto in locale. Per fare ciò si utilizza l'applicazione Unity DevOps Version Control scaricabile dal link precedente navigando su "DevOps"->"Help and Support" e cliccando sul pulsante "Download UVCS Desktop Client". Dopo aver aperto il programma si naviga alla sezione "Open or create other workspace" cliccando sul pulsante accanto alla Home. All'interno della finestra che si aprirà, cliccando sul pulsante "Create a new workspace" si potrà creare una nuova workspace e collegarla ad una repository già esistente. Infine per lavorare con il progetto presente in questa repository, copiare i file scaricati da qui, incollarli sulla nuova workspace e fare un primo push. Il processo di creazione dell'organizzazione e della repository va fatto soltanto da una persona.

### Configurazione delle scene e branch
Una volta configurato il progetto, per evitare conflitti, conviene creare un branch per ogni partecipante che sarà associato ad una propria scena in cui lavorerà soltanto alla propria parte. Invece il branch Main sarà utilizzato per aggiornare la scena con tutte le parti del progetto unite. In fase di merge le singole scene dei vari partecipanti saranno aggiornate con la versione più recente, e fatto ciò sarà necessario copiare la Hierachy di ciascuna di esse e incollarla a quella della scena completa. Tutto ciò viene fatto perché quando si lavora tutti in una singola scena ci sono troppi conflitti da risolvere e ci possono essere problemi per l'aggiornamento del contenuto di essa.

### Alternative
Questo strumento è abbastanza funzionante, ma durante lo sviluppo ha presentato dei comportamenti strani che sono stati tutti risolti. Quindi se si vuole non si è obbligati ad utilizzare lo Unity Version Control ma si possono cercare delle alternative. Ad esempio è stato trovato un programma scaricabile da questo link https://kinematicsoup.com/scene-fusion/download. Esso non è stato approfondito ma potrebbe rappresentare una valida alternativa. 
