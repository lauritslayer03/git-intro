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

La oss opprette en tom mappe som heter "im-git-intro", og så gå inn i den:

```
mkdir im-git-intro
cd im-git-intro
```

`mkdir`står for "Make Directory", altså opprett mappe, og `cd` står for "Change Directory", altså endre mappe.
Så skal vi initialisere denne mappen som et git-prosjekt med en git-kommando:

```
git init -b main
```

Med denne kommandoen opprettes et tomt git-repo med en **branch** til å begynne med som heter `main`. Det brukes litt forskjellige navn på den første branchen som `main`, `master` eller `trunk`. GitHub bruker `main`, og derfor bruker vi det.

### Gjør en endring

Det er en konvensjon å bruke en fil med navnet `README.md` til å forklare hva et repo er til for. GitHub vil gjenkjenne og automatisk vise en README filen, så la oss begynne der. Vi bruker verktøyet `nano` til å redigere tekstfiler rett i terminalen. Kjør denne kommandoen for å opprette og redigere README.md:

```
nano README.md
```

Nå redigerer vi med nano! README er en **markdown** fil, som er et enkelt format for å skrive tekster. Vi kan skrive en overskrift sånn her:
```markdown
# Artene i Hundedyr-familien
```

Bruk Ctrl-O for å lagre, og Ctrl-X for å gå ut av filen når du er ferdig.

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

Du oppretter et nytt repository i GitHub med den grønne "New"-knappen i hjemskjermen når du er logget inn.

Bruk samme navn på repoet som mappen vi opprettet. Du velger selv om du vil opprettet repoet offentlig eller privat, du kan alltids gjøre det offentlig senere, om du oppretter det privat. Ikke trykk på noen av check-boksene. 

### Koble til GitHub

Nå skal vi koble vår lokale mappe til github. GitHub-repoet vi akkurat opprettet skal vi legge til som en **remote**, altså et "fjernlager".

```
git remote add origin https://github.com/(dinbruker)/(ditt-repository).git

```

`origin` er nå kallenavnet for repoet i GitHub. `origin` er en konvensjon for når man kun har en **remote** man jobber med.

### Push

Vi er nå klare til å laste opp. Git gjør ikke så mange antakelser, så vi eksplisitt at ikke bare skal laste opp med `push`, men at vi skal pushe til stedet som heter `origin`, og at vi skal `push`e til branchen som heter `main`.

```
git push -u origin main
```

### Gikk alt bra?

Gå inn i repositoryet ditt på GitHub, nå skal vi ha en README-fil som vises i nettleseren!

## Vi lager en branch

Nå har vi jobbet og `push`et rett til `main`, som er vår hoved-branch. Hvis man er flere som jobber samtidig kan dette fort bli rotete. Derfor er det lurt å jobbe med hver sin kopi eller forgreining av koden, eller `branch`. Så når vi nå skal begynne å legge inn arter og slekter i repositoryet vårt, skal vi lage `branch` først.

### Lag en branch og bytt til den

Vi bruker `branch` kommandoen for å opprette og liste opp brancher:

```
git branch
```
Viser at vi har kun en branch: `main`.
For å lager en ny branch med navnet "mappestruktur", kjører vi kommandoen:

```
git branch mappestruktur
```
Nå kan vi se at den er opprettet;
```
git branch
```
Men stjernen ved siden av navnet `main` viser at det fortsatt er den som er valgt. For å bytte til å jobbe i den nye branchen kan vi bruke `switch`:

```
git switch mappestruktur
```
For å både opprette og bytte på én gang kan vi bruke `switch -c` (kort for `--create`):
```
git switch -c ny-branch
```

### Vi gjør en ny endring

Nå som er trygt i vår egen branch kan vi begynne på artsdatabasen! Opprett en mappe med samme navn som familien du har valgt i roten av repoet med `mkdir`, gå inn i den med `cd`, og bruk `nano` for å skrive en `README.md`-fil inni den mappen med en kort beskrivelse av dyrefamilien (hent gjerne fra wikipedia). Så lenge vi kaller filen `README` vil den automatisk vises i GitHub, så vi kan gå gjennom mappene som en nettside og lese om de forskjellige artene.

Når den nye filen er lagret legg den til i stage med `git add`, og legg den til i en **commit** med `git commit -m`. Husk å ta med en beskrivelse! Til slutt, last opp endringen til github med `git push -u origin mappestruktur`. Vi må fortsatt spesifisere at vi pusher til `origin` og til `mappestruktur`.

## Vi lager en pull request, og gjør en egen-review

Når endringene er ferdig, er det på tide å få dem inn i main. Hensikten er at main skal være versjonen med den endelige koden. For overføre koden bruker vi det som i GitHub kalles en **Pull Request**. En pull request er altså en *forespørsel* om at de som eier repoet (i dette tilfellet deg selv) skal *trekke* dine endringer inn i repoet.  

Gå inn i repoet i GitHub. Siden vi pushet til branchen nylig, skal det komme en stor fin grønn knapp øverst i repoet "Compare & Pull request".  

Først skal vi opprette requesten, gjerne med en beskrivelse av hvorfor vi gjør denne endringen. Det kan vi la stå tomt for nå. Vi trykker på "Create".  

Så kommer vi til en oversikt. Hvis dere trykker på "Files Changed" fanen, kan dere se en oversikt over endringene som er med i denne requesten. Se over at det ikke er noen skrivefeil.

## Merge en Pull Request

Når requesten er OK, kan vi `merge` den. Det vil si at vi "spleiser" endringene fra en branch inn i en annen. I dette tilfellet merger `mappestruktur` inn i `main`. GitHub kan gjøre dette automatisk for oss, med enda en fin, grønn knapp. Trykk på den.

## Hent endringer fra Github ned til din datamaskin

Ettersom GitHub tok seg av å `merge` fra `mappestruktur` til `main`, er ikke de endringen i `main` på din maskin. Vi skal gjøre et motsatt en av `push`, nemlig en `pull`. Først må vi tilbake til `main`:

```git switch main```

For så å laste ned endringene fra GitHub med `pull`:
```git pull```

Hvis dette gikk som det skulle, skal nå både commiten og den nye mappen være lastet ned. Vi kan sjekke at commiten er kommet med å sjekke listen over commits med `log`:

```git log```  

Vi kan sjekke at mappen og filen er kommet ved å bruke kommandoen `ls` (kort for "list"), som viser alt i nåværende mappe: 
```ls```

## Legg til mer i artsdatabasen!

Inne i famile-mappen skal du opprette en mappe for hver av slektene i familien. Inne i hver av slekt-mappene, oppretter du en mappe om hver av artene. Da får vi mapper som ser sånn ut:

* /Hundefamilien
    * README.md
    * /Vulpes
        * README.md
        * /vulpes
            * README.md
        * /chama
            * README.md
    * /Canis
        * README.md
        * /latrans
            * README.md
    * /Lycaloplex
        * README.md


Ikke gjør alt på en gang! Stykk opp arbeidet ditt. Da er det enklere for deg å holde oversikt, og det er enklere for noen som leser historikken senere å forstå hva som har skjedd i vært steg.

Husk prosessen: 
* Lag og switch til en ny branch fra main
* gjør endringer med nano
* commit endringene
* push til github
* opprett en PR i github
* merge PRen i github
* pull ny main.

## git gud

Nå kan du alt du trenger for å gjøre endringer med **git**! Det virker kanskje litt mer tungvint enn å skrive i Word, men når man er flere som skriver kode, er det essentielt for å ikke få store problemer.

## Overflow

Hvis du er ferdig med å legge til arter og slekter, kan du lære mer om markdown ved å prøve å legge til bilder, eller du kan du prøve deg på noen mer avansert git-teknikker her: https://learngitbranching.js.org/

## TODO

* Bli invitert og gjøre en request hos noen andre?
* .gitignore
* nano som standard redigeringsverktøy