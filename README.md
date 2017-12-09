# MONITORERING & LOGGING 

### Abstract 

Mange deployed systemer, benytter ikke monitoring og bliver derfor vanskelige at vedligeholde. <br>
Med monitorering og logging af det allerede kørende system kan man få et bedre indblik i hvordan systemet performer og hvilke fejl der opstår. <br> 
Monitorerings- og logging værktøjer som Grafane, Prometheus og Elk stacken giver teamet bedre mulighed for at finde og løse problemer. <br>
Ved at benytte disse værktøjer kan man opnå et hurtigere og mere stabilt system, med færre fejl og derved også en bedre brugeroplevelse. <br>


### Problemet

Som enhver udvikler ved er logs en kritisk ressource til at finde fejl i komplekse systemer i produktion. 
De giver en rig mulighed for at se hvad der skete, hvornår og hvor i systemet, så en hurtig og præcis løsning til et problem kan udvikles. 
Men at arbejde med logfiler er som regel en meget tidskrævende og administrativ tung opgave. 

Selve implementeringen af logfiler er ligetil at gøre, men hvis du ikke er opmærksom på det fra start, 
kan det hurtigt give dig et problem da du vil komme til at ligge dine logs forskellige steder, 
og de med tiden vil vokse sig større efter jo flere brugere du får til systemet.

Når du som udvikler eller administrator kommer og skal finde ud af hvorfor en fejl er kommet i systemet, 
kan det blive svært at overskue med de mange store logfiler der forekommer på systemet, 
det gør det til en langt mere besværlig og tidskrævende arbejdsopgave end den burde være.
Et andet problem som logging kan have, som typisk vil forekomme i ældre systemer, 
er at logfiler kan have forskellige formater/udseende som ikke stemmer overens med de nyeste implementeringer af samme system, 
hvilket igen giver udvikleren eller administratoren længere behandlingstid, da de nu skal til at skelne mellem forskellige logs

Logging alene vil ikke være tilstrækkelig nytte for dit system, slet ikke hvis dit system bliver stort, 
med millioner af brugere, da det vil blive uoverskueligt at holde styr på det hvis der kommer en fejl.
Uden den rette overvågning vil logging i sig selv ikke være så brugbart som det kan være og det vil stadig være en tidskrævende opgave at finde fejl ud fra.
Dette fører os ind på monitorering, eller manglende monitorering, som vil hjælpe dig til at overvåge dit system og logs.

### Hvorfor bruge monitorering?

Ved at indarbejde monitorering i et system, kan man sikre en hurtig og præcis indsamling af relevant data, som omhandler et opstået problem, 
det giver udvikleren mulighed for at inspicere logfilerne og få lokaliseret et eventuelt problemet hurtigt.

Ved at bruge monitorering har man også mulighed for at udforske og overvåge systemet i produktion, her vil det typisk være monitorering af f.eks. opstået fejl, resource brug samt responstid. 
<br>Ved at monitorere f.eks. et system resursebehov, har udvikler og administrator mulighed for at få en advarsler de kan handle på, når der sker noget uventet, 
det kan f.eks. være massiv tilgang i antallet af bruger eller hvis en del af systemet pludselig bliver overbelastet på anden måde så systemet har et stort resursebehov og derved bliver langsomt. 
<br>Ud fra det kan man hurtigt beslutte hvad man ønsker gøre, om det er behov for skalering eller nedlukning af dele af systemet der er brug for. 

### Værktøjer der kan hjælpe dig

Der er flere værktøjer som kan bruges til at implementere monitorering, et par af disse kunne f.eks. være Grafana, Prometheus og Elk stacken. 
De nævnte værktøjer dækker og hjælper med at sætte et godt monitorering set-up op, så du er rustet til at klare de udfordringer du vil komme ud for.  

#### Grafana
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


