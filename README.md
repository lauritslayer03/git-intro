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
`git --version`
  
Hvis du har **git** vil programmet svare med hvilken versjon det er. Hvis ikke vil det komme instruksjoner for hvordan du installerer det. Følg disse instruksjonene.

### GitHub-bruker

Før vi kan bruke GitHub til å dele kode, trenger vi en bruker. GitHub brukeren din kan også bli en slags portefolio for å hvis fram hva du kan. Hvis du ikke har en bruker kan du lage en her: https://github.com/join 

### SSH-nøkler

todo

#### Opprett en ny nøkkel

todo

#### Legg til nøkkelen i GitHub

https://github.com/settings/keys

## Vi setter opp et lokalt repository

Vi setter opp et lokalt repoet vårt osv.

## Vi kommer i gang med github

setter opp ssh nøkler

oppretter et tomt repo på github som tilsvarer vårt lokale repo.

## Make a change

Vi lager vår første commit (bunt) og pusher (laster opp) til main på github.

### Gjør en endring

Bruke nano til å oppdatere README.md. 

### "Stage" en endring

Legger til endringen på "Staging Area"

### Commit

En "bunt" med arbeid. Vi legger til arbeidet vi har gjort i en commit.

### Push

Vi laster opp arbeidet ved å gjøre en push.

## Vi lager en branch

Hva skjer hvis noen andre jobber samtidig? Hva hvis noe bare er delvis ferdig? Vi lager en forgrening


## Vi gjør en ny endring

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

