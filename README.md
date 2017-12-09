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
Ved at monitorere f.eks. et system resursebehov, har udvikler og administrator mulighed for at få en advarsler de kan handle på, når der sker noget uventet, 
det kan f.eks. være massiv tilgang i antallet af bruger eller hvis en del af systemet pludselig bliver overbelastet på anden måde så systemet har et stort resursebehov og derved bliver langsomt. 
Ud fra det kan man hurtigt beslutte hvad man ønsker gøre, om det er behov for skalering eller nedlukning af dele af systemet der er brug for. 

