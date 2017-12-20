# MONITORERING & LOGGING 

### Abstract 

Mange deployed systemer, benytter ikke logging og monitoring og bliver derfor mere vanskeligt og tidskrævende at vedligeholde. 
Med logging og monitorering af et allerede kørende system, kan man få et bedre indblik i hvordan systemet performer og hvilke fejl der opstår. Logging- og monitoreringsværktøjer som Elk stacken, Grafane og Prometheus giver teamet bedre mulighed for at finde og løse problemer. 
<br>
Ved at benytte disse værktøjer kan man opnå et hurtigere og mere stabilt system, med færre fejl og derved også en bedre brugeroplevelse. 
<br>



### Problemet

Som enhver udvikler ved er logging en kritisk ressource til at finde fejl i komplekse systemer i produktion. Logging giver en rig mulighed for at se hvad der skete, hvornår og hvor i systemet, så en hurtig og præcis løsning til et problem kan udvikles. Men at arbejde med logfiler er som regel en meget tidskrævende og administrativ tung opgave.
Selve implementeringen af logging er ligetil, men hvis du ikke er opmærksom på det fra start, kan det hurtigt give dig et problem da du vil komme til at ligge dine logs forskellige steder, og de med tiden vil vokse sig større efter jo flere brugere du får til systemet.
<br>
Når du som udvikler eller administrator kommer og skal finde ud af hvorfor en fejl er opstået i systemet, kan det blive svært at overskue de mange store logfiler, der forekommer på systemet, det gør det til en langt mere besværlig og tidskrævende arbejdsopgave end den burde være, hvis du manuelt skal sidde og kigge dem igennem. Et andet problem som logging kan have, som typisk vil forekomme i ældre systemer, er at logfiler kan have forskellige formater/udseende som ikke stemmer overens med de nyeste implementeringer af samme system, hvilket igen giver udvikleren eller administratoren længere behandlingstid, da de nu skal til at skelne mellem forskellige logs.
<br>
Et godt eksempel på hvor forskellige formater en logfil kan have fandt vi ud af i vores Hackernews projekt, hvor vi har implementeret logging. Her har vi gjort det på et allerede eksisterende projekt, efter selve implementeringen fandt vi ud af at vores logfiler ikke havde samme format og at de derfor blev sværere at analysere. I den ene logfil kunne vi se hvad der kom ind i systemet, men heller ikke meget mere end det: 

Billede badlog

Her vil en god logfil have fortalt tid, dato, år samt hvilken user der postede enten det specifikke post eller comment, samt hvad useren postede eller kommenterede. Så den logfil er mere eller mindre ubrugelig. I den anden logfil, hvor vi overvåger hvem der får adgang til systemet, havde vi lavet en god og informativ log:

Billede goodlog

Ved at vi har en god log kan vi se hvornår, altså tid, dato, år, hvor kritisk det er, om brugeren har fået adgang samt hvilken ip-adresse brugen prøver at tilgå vores system fra. 
<br>
Logging alene vil i langt de fleste tilfælde ikke være tilstrækkelig til dit system, slet ikke hvis dit system bliver stort, med flere tusinder af brugere, da det vil blive uoverskueligt at holde styr på det hvis der opstår en fejl eller sikkerhedsbrist. Uden den rette monitorering vil logging i sig selv ikke være så brugbart. Dette fører os ind på monitorering, som kan hjælpe dig til at overvåge dit system og logfiler.

### Hvorfor bruge monitorering?

Ved at indarbejde monitorering i et system, kan man sikre en hurtig og præcis indsamling af relevant data, som omhandler et opstået problem, det giver udvikleren mulighed for at inspicere logfilerne og få lokaliseret et eventuelt problem hurtigere.
Ved at bruge monitorering har man også mulighed for at udforske og overvåge systemet i produktion, her vil det typisk være monitorering af f.eks. opstået fejl, resource brug samt responstid. 
<br>
I vores Hackernews projekt har vi sat monitorering op med Prometheus, for at få et mere overskueligt billede af hvordan vores system virker, her monitorerer vi f.eks. Antallet af request til vores system i perioden fra d. 7 - 14 december 2017, som det også ses er der ikke sket noget uventet i den periode ved at antallet pludselig er steget fuldstændigt sindsygt. 

Billede total request

Billede total requests
Ved at monitorere f.eks. et systems resursebehov, har udvikleren og administratoren mulighed for at få en advarsler de kan handle på, når der sker noget uventet, det kan f.eks. være massiv tilgang i antallet af bruger eller hvis en del af systemet pludselig bliver overbelastet, så systemet har et stort resursebehov og derved bliver langsomt. Ud fra det kan man hurtigt beslutte hvad man ønsker gøre, om der er et behov for skalering eller nedlukning af dele af systemet. 
<br>
Efter at vi selv har prøvet at bruge logging- og monitoreringsværktøjer, vil vi sige at det er noget man bør bygge op gradvist, startende med blot at implementere en log. Derefter kan man, i takt med at systemet vokser sig større og mere kompliceret og begynde at implementerer monitoreringssystemet. 

### Værktøjer der kan hjælpe dig

Der er flere værktøjer som kan bruges til at implementere monitorering, et par af disse kunne f.eks. være Grafana, Prometheus og Elk stacken. 
De nævnte værktøjer dækker og hjælper med at sætte et godt monitorering set-up op, så du er rustet til at klare de udfordringer du vil komme ud for.  

#### Grafana 
![Grafana](https://github.com/JonasSimonsen/UFO/blob/master/pictures/grafana.png) <br>
Grafana er et visuelt overvågnings værktøj som bl.a. giver dig mulighed for at lave grafer, alarmer, notifikationer, og filtrere din data på en pæn og overskuelig måde.
Et eksempel på hvor Grafana er godt at bruge er med dets alert / notifikation system, som giver dig besked når den opfanger noget uregelmæssigt, baseret på dine filtre, så du hurtigt får besked om at du skal tage et kig på dit system.
Det kan være hvis dit system er langsomt til at beregne et request, eller hvis dit ressourceforbrug lige pludselig bliver tårnhøjt, baseret på det normale forbrug. 

#### Prometheus
Prometheus er et værktøj som samler din data ét sted, for at danne et overblik.
Typisk data du sender til Prometheus kan være hvor mange gange et API bliver kaldt, eller hvor lang tid dine metoder er om at behandle et request.
Men du er ikke bundet til kun at indsamle data om dit projekt, du har også mulighed for at overvåge din server.

#### Elk
Elk stacken er et sæt værktøjer som kan bruges til at give et godt overblik over bl.a. dine logfiler.
##### Elastic search
Elastic search er en søgemaskine som er enormt hurtig, meget tæt på øjeblikkeligt feedback,  til at analysere og søge i store mængder dokumenter, heriblandt log filer. Dette gør du næsten ingen ventetid har på at skulle søge din data igennem, som ville stoppe dit workflow.
##### Logging
Logging er vigtigt at have med i et system da det vil hjælpe dig hvis du støder ind i en fejl.
En ting at være opmærksom på fra start er at finde et logging format som man fælles kan blive enig om i systemet og benytte sig af det hele vejen igennem, for let at kunne overskue dem når man skal se dem igennem.
##### Kibana
Kibana er et visuelt værktøj til at analysere den data som kommer fra elastic search, så man på den måde får en ide om hvad der foregår i ens system.  Det kan bl.a. bruges til at lave grafer over dine logfiler ved at sammenligne mønstre i dem.
Det gør du slipper for at skulle læse hver linje igennem, men du istedet kan se en graf over de forskellige handlinger. Det er også muligt at søge inden for bestemte tidspunkter, eller hvis man ønsker at finde ud af hvor i verden flest bruger af systemet sidder eller hvorfor man pludseligt midt om natten får en ekstrem tilgang i antal request.  

### Hvad holder implementering af monitorering tilbage?
 
En manglende faktor til at man vælger at sætte monitorering op på et allerede eksisterende system kan bl.a. være at det er en meget tidskrævende process hvis man ikke præcis ved hvad man laver. Ved at implementeringen kan være tidskrævende kan det også være dyrt, idet man ikke føler at man får noget, for den tid man bruger på at implementere det. En anden grundlæggende faktor for ikke at implementere det i et allerede eksisterende system kan være at implementeringen hurtigt bliver besværliggjort eftersom at systemet mange gange er placeret på flere forskellige server. Den sidste afgørende faktor kan være at udviklings teamet ikke har den fornødne know how til at kunne implementere det på en sådan måde at man får det optimale ud af både logging og monitorerings delen.

### Hvad får du ud af at monitorere og logge?
Implementere af logging og monitorering i dit system, vil på sigt spare både tid og penge i forhold til vedligeholdelse af dit system, da du hurtigere finder fejlene, i logfilerne, og du får hurtigere en melding om fejlene, ved hjælp af monitorering.
Det kræver tid at implementere i starten, specielt hvis det er ældre systemer, som kan være store og komplicerede at finde rundt i, men hvis du oplever fejl og har svært ved at lokalisere dem, vil logging og monitorering med garanti hjælpe dig til at både finde fejlene hurtigere. På den lange bane forventes det, at være en god investering, da det ligesom refaktorering gør det hele nemmere senere hen og der vil spares en masse tid, idet man ved en vellykket opsætning ikke skal sidde og lede i logfilerne.

