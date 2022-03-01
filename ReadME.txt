Il codice che abbiamo implementato per la Challenge è organizzato come segue:
- A. 	ReadCASCADEcontours: 
	1.	Lettura dei file DICOM e dei contorni delle carotidi segmentate manualmente
	2.	Conversione dei contorni di lume e wall in maschere
	3.	Centering del collo del soggetto nelle immagini
	4.	Pulizia del dataset: eliminazione delle segmentazioni incomplete e riassegnazione delle segmentazioni manuali alla giusta label (ICAL, ICAR, ECAL, ECAR) in caso di errori
5.	Salvataggio di immagini e maschere delle slice di cui è disponibile una segmentazione sotto forma di volumi in formato .tiff all’interno della cartella ‘3D_dataset’
- B. 	Preprocessing:
	1.	Eliminazione automatica delle slice contenenti biforcazioni
	2.	Preparazione delle matrici da fornire alle reti per l’allenamento
- C. 	Training: Allenamento delle reti neurali
- D. 	Testing: 
	1.	Creazione delle maschere automatiche e salvataggio nella cartella 'RESULTS'
	2.	Calcolo delle metriche di valutazione delle performance

All'interno dell'archivio 'Folders.zip' sono contenute le seguenti cartelle:
	- DATASET: Dataset originale da cui è stato rimosso il soggetto P16
	- 3D_dataset: Slice e maschere manuali dei soggetti di Training e Validation set, salvate come volumi .tiff
	- PICKLE_and_JSON: File utili da passare tra gli script
	- Trained_Nets: reti neurali allenate

NOTA: In assenza delle cartelle '3D_dataset', 'PICKLE_and_JSON' e 'Trained_Nets' i codici devono essere runnati in ordine al fine di disporre di tutte le cartelle e file necessari all’esecuzione dei codici successivi. Poiché insieme al codice forniamo tutto il necessario, questo obbligo viene meno. L'unico vincolo che rimane valido è che se viene runnato lo script A, deve essere successivamente runnato anche il B, in quanto entrambi gli script sovrascrivono dei file (dizionari .json).