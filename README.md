# git-intro

En kort introduksjon til **git**, et versjonskontrollsystem.
I dette kurset skal vi lære om hvordan man kan bruke **git** sammen med nettstedet **GitHub** til å samarbeide om å skrive kode og til å strukturere arbeidet sitt på en lur måte.

## Hva skal vi lage?

Vi skal fokusere på å lære om git, og ikke sette oss fast i kompileringsfeil. Derfor skal vi ikke programmere i dag, men lage en oversikt over en *familie* med dyr! Dyr er _taksonomisk_ inndelt sånn som dette (mer og mer spesifikt):

* Domene
* Rike
* Rekke
* Klasse
* Orden
* Familie
* Slekt
* Art

Rødvreven vi har her i Norge, for eksempel, ser sånn ut:

* Rike: Dyr
* Rekke: 	Ryggstrengdyr
* Klasse: 	Pattedyr
* Orden: 	Rovpattedyr
* Familie: 	Hundedyr
* Slekt: Reveslekten
* Art: Vulpes vulpes (Rødrev)

Din oppgave blir å lage en oversikt over en familie med dyr. Velg ditt favorittdyr, og finn ut hvilken familie den har. I eksempelet med rødreven vil vi da ha en mappe for hver av slektene innenfor hundefamilien, og en mappe for hver av artene innenfor hver slekt. Det er så farlig om det blir helt nøyaktig, og det trenger heller ikke være fullstendig.  

*Før du går videre velg deg en familie med dyr (eller velg et art og finn ut hvilken familie den tilhører).*

## Ting vi trenger

### Terminal

Vi skal gjøre alt arbeidet på maskinen med "terminalen", også kalt "kommandolinjen". Det er et type program som bruker tekst istendenfor grafikk. Mange nyttige programmer for utviklere har ingen grafisk del, og kan kun brukes fra kommandolinjen. På mac kommer dette innbygget: Åpne opp programmet som heter "Terminal" på macen.

### git 

Vi kaller **git** for et "system", men først og fremst er det et program som kjører på maskinen din. Så aller først må vi installere programmet!  
Hvis du er på mac er det en innebygget måte å få til dette på. Skriv i terminalen din:  

```
git --version
```
  
Hvis du har **git** vil programmet svare med hvilken versjon det er. Hvis ikke vil det komme instruksjoner for hvordan du installerer det. Følg disse instruksjonene.

### GitHub-bruker

Før vi kan bruke GitHub til å dele kode, trenger vi en bruker. GitHub brukeren din kan også bli en slags portefolio for å vise fram hva du kan. Hvis du ikke har en bruker kan du lage en her: https://github.com/join 

### SSH-nøkler

Nå som vi har en bruker, må vi gi maskinen vår tilgang til å laste opp og ned fra den brukeren. Med GitHub er det ikke lov å bruke brukernavn og passord, så vi skal istedenfor bruke noe som heter en SSH-nøkkel (ssh key). Det er et slags veldig langt passord som ligger lagret på maskinen din. 

#### Opprett en ny nøkkel

Først må vi opprette en ny nøkkel. Dette gjør vi fra terminalen med følgende kommando, med din epost:
```
ssh-keygen -t ed25519 -C "dinepost@osloskolen.no"

```

`ssh-keygen` er et program for å lage sånne nøkler, og `ed25519` betyr typen nøkkel vi lager.

Du vil først få tilbakemelding om at programmet henger med:
```
> Generating public/private ed25519 key pair.
```

Så får du spørsmål om hvor på maskinen din nøkkelen skal ligge, trykk enter for å godta standardvalget:
````
> Enter a file in which to save the key (/Users/you/.ssh/id_ed25519): [Press enter]
````

Tilslutt får vi spørsmål om nøkkelen skal ha et passord. Dette er viktig om noen andre har tilgang på datamaskinen din. Sålenge alle er forsiktige med å låse maskinen når du går fra den er det greit å trykke enter for ingen passord:
```
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

#### Legg til nøkkelen i GitHub

Vi har nå fått et "nøkkelpar" (key pair) med to deler: en "private" del i `/Users/navnetditt/.ssh/id_ed25519` og en "public" del i `/Users/navnetditt/.ssh/id_ed25519.pub`. Det er "public"-delen vi skal putte i GitHub. GitHub kan da bruke public-nøkkelen for å bekrefte at en nedlasting kommer fra en maskin som har den hemmelige "private" nøkkelen. (Fordi matematikk)  


Vi kan kopiere **public** delen av nøkkelen med denne kommandoen:

```
cat /Users/navnetditt/.ssh/id_ed25519.pub | pbcopy
```

Og limer den inn i GitHub her: https://github.com/settings/keys

TODO: add images?

## Git Started

Vi skal nå opprette en mappe for prosjektet vårt, opprette den første filen, og laste dette opp til GitHub.

### Lokalt repository

Et prosjekt som vi holder styr på med git kaller vi et "repository" eller bare "repo". Det betyr noe sånt som "oppbevaringssted". Vi skal opprette en tom mappe og gi git beskjed om å holde styr på filene der. Å opprette mapper og bevege oss rundt i dem er også noe vi kan gjøre med terminalen!

La oss opprette en tom mappe som heter "im-git-intro"


### Gjør en endring

Det er en konvensjon å bruke en fil med navnet `README.md` til å forklare hva et repo er til for. GitHub vil gjenkjenne og automatisk vise en README.md-fil, så la oss begynne der. Vi bruker verktøyet `nano` til å redigere tekstfiler rett i terminalen. Kjør denne kommandoen for å opprette og redigere README.md:

```
nano README.md
```

Nå redigerer vi med nano! Bruk Ctrl-O for å lagre, og Ctrl-X for å gå ut av filen når du er ferdig.

### Hva vet git?

Når du har lagret filen skal git ha fått med seg endringen. Vi sjekker:
```
git status
```

Git skal da vise at den har fått med seg at filen er blitt endret på, men den er i klar for å lastes opp helt enda.

### "Stage" en endring

For at endringer skal bli lastet opp må den først puttes i "Staging Area", så vi kaller å gjøre en endring klar for å "stage" den. Vi stager en fil med kommandoen:

```
git add README.md
```

### Commit

Når alt som skal være med i opplastingen ligger i Staging, skal vi lage en "commit". En commit er en samling med endringer som gir mening sammen. En god hovedregel er at koden skal fungere på hver commit. Vi opprettet en commit med kommandoen:

`git commit -m "Add README.md"`

Hvor teksten mellom "" er en beskrivelse av endringene. Det er kjempenyttig når du jobber med andre, men kan også være lurt for å minne på seg selv hva det er man har gjort. Commiten med arbeid er nå klar til å lastes opp, men vi har ikke enda et sted å laste opp til.

### Opprette et repository i GitHub

TODO Opprett i github

### Koble til GitHub

TODO add remote
Nå skal vi koble vår lokale mappe til github

### Push

TODO push 

### Vi sjekker at 

## Vi lager en branch

Hva skjer hvis noen andre jobber samtidig? Hva hvis noe bare er delvis ferdig? Det er mye ryddigere å jobbe med en kopi av koden. Vi kaller en sånn kopi en "branch"

### Lag en branch og bytt til den


### Vi gjør en ny endring

Nå som er trygt i vår egen branch kan vi gjøre 

## Vi lager en pull request, og gjør en egen-review

Vi får endringene våre over fra forgreining til

En pull request er altså en *forespørsel* om at de som eier repoet (i dette tilfellet dere selv) skal *trekke* dine endringer inn i repoet. 

## Merge en Pull Request

Når requesten er OK, kan vi merge den. Det vil si at vi spleiser endringene fra en forgreining inn i en annen. I dette tilfellet merger branchen hvor vi har gjort endringer inn i main.

## Hent endringer fra Github ned til din datamaskin

Vi gjøre en pull fra remote til din lokale maskin.

Git pull.

Git Log.

## Legg til mer i artsdatabasen!

Fortsett med å legge til flere slekter og arter. Ikke gjør alt på en gang! Stykk opp arbeidet ditt. Da er det enklere for deg å holde oversikt, og det er enklere for noen som leser historikken senere å forstå hva som har skjedd i vært steg.

Husk prosessen: 
* Lag og switch til en ny branch fra main
* gjør endringer med nano
* commit endringene
* push til github
* opprett en PR i github
* merge PRen i github
* pull ny main.

## TODO

* Bli invitert og gjøre en request hos noen andre?
* .gitignore
* nano som standard redigeringsverktøy
* kommandolinje-operasjoner

