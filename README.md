# Palazzo-Bernabei-VR
Repository dedicata ai progetti di tesi che riguardano la ricostruzione di Palazzo Bernabei.

## Struttura Repository
Questa Repository è divisa in due cartelle:
1. **Cartella Blender**: contiene i file .blend dove si possono trovare tutti i modelli utilizzati all'interno del progetto, in particolare:
   - **Facciata_ogg_ingresso.blend**: file dove si possono trovare tutti i modelli relativi alla facciata del Palazzo;
   - **Ingresso_Palazzo_Bernabei.blend**: file dove si possono trovare tutti i modelli relativi all'atrio del Palazzo e alla terrazza;
   - **aule_palazzo_bernabei.blend**: file dove si possono trovare tutti i modelli relativi alle stanze al piano inferiore che sono: l'ingresso per le aule, il laboratorio immersivo, il secondo laboratorio di informatica e l'aula insonorizzata;
   -  **stemmi_scansionati.blend**: file dove si possono trovare tutti i modelli scansionati con lo scanner 3D;
2. **Cartella Unity**: contiene a sua volta la cartella Progetto-Assisi, che contiene tutti i file relativi al progetto creato con Unity.

## Cartella Progetto-Assisi
Nella cartella Assets relativa al progetto realizzato in Unity si possono trovare le seguenti sottocartelle:
- **CharacterPack Lowpoly** e **Distant Lands**: contiene asset scaricati dallo store di Unity che sono stati usati per i modelli delle persone che si possono trovare nel laboratorio immersivo.
- **Decorative Plants** e **Stylized Plants Kit**: contiene asset scaricati dallo store di Unity che sono stati usati per i modelli delle piante che si possono trovare nella terrazza.
- **Models**: contiene tutti i modelli importati da Blender, suddivisi nelle sottocartelle: aula1 (laboratorio immersivo), aula 2 (secondo laboratorio di informatica), aula3 (aula immersiva), ingressoAule, corridoio (struttura di collegamento tra le aule), Citta (modelli usati per le case inserite nell'oggetto terreno), Ingresso, Terrazzo e Facciata. La stessa suddivisione si troverà anche nella Hierarchy su Unity.
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
