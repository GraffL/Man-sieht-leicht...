## Dynamische Systeme ## 

Ein _dynamisches System_ (auf einem Raum X) ist gegeben durch eine Funktion F: X x T -> X. Diese gibt an, wie sich Elemente des Zustandsraumes X im Laufe der Zeit T ändern. Für T = IN ist F oft gegeben durch eine Funktion f: X -> X und F(x,n) := f^n(x), d.h. für jeden Zeitschritt wird einmal f angewandt.

Eine _Kontrollmenge_ D \subseteq M (M Mfg) ist eine maximale Teilmenge mit den beiden Eigenschaften:
	* Kontrollierte Invarianz: \forall x \in D: \exists u \in U (Kontrollfunktionen): \phi(IR_+,x,u) \subseteq D (\phi(_,x,u) Lsg d. definierierenden Differenzialgleichung mit Anfangswert x)
		(d.h. Kontrollfluss bleibt in D)
	* Approximative Kontrolloerbarkeit: \forall x,y \in D, \epsilon > 0: \exists u \in U, T > 0: d(\phi(T,x,u), y) < \epsilon 
		(d.h. Kontrollfluss läst sich beliebig nahe an y steuern)
		
Ein linearer Operator A: IR^n -> IR^n heißt _hyperbolisch_ :<=> A hat keine EWe auf S^1 <=> IR^n = E^- + E^+: AE^+ \subseteq E^+ und A ist auf E^- Kontraktion und auf E^+ Expansion.

Gleichmäßige Hyperbolizität modelliert chaotisches Verhalten.



## Algebra ##

Warum können die Quarternionen kein Körper sein? Dann wären sie eine endliche Körpererweiterung von IC - IC ist aber algebraisch abgeschlossen und enthält damit alle algebraischen Ereweiterungen.
	-> In welchem Sinne ist das wirklich eine Antwort? Setzt das z.B. schon voraus, dass die IC ein Unterring von IH sein soll?

	

## Algebraische Topologie ##

Motto: Für ausreichend gute Raumpaare gilt: Homologie von Raumpaar = Homologie von Quotient der beiden Räume
	-> gilt bspw. NICHT für RP^n, RP^{n-1} (siehe AlgTopo B11/A3)
	
### Spektra ###

Ein Spektrum E ist eine Folge punktierter CW-Komplexe (E_n, *)_{n\in IZ}, sodass \Sigma E_n \subseteq E_{n+1} (die Einhängung von E_n hat (zelluläre) Inklusion in E_{n+1})

Ein Unterspektrum E' \subseteq E heißt kofinal :<=> jede Zelle in E liegt "irgendwann" (nach endlich vielen Einhängungen) in E'

Ein Morphismus zwischen Spektra f: E -> F ist eine auf einem kofinalen Unterspektrum definierte Abbildung f: E' -> F, f_n:E'_n -> F_n, s.d.:
	  E'_{n+1}  ----f_{n+1}--->   F_{n+1}
	     U|                          U|
	\Sigma E'_n --\Sigma f_n--> \Sigma F_n
kommutiert.


## Graphentheorie ##

* Ein Graph ist bipartit <=> er enthält keine Kreise ungerader Länge (dieser und der folgende Fakt entstammen einem Vortrag zu degenerierten Hilbert-Schemata)
* Man kann ein (symmetrisches) Produkt von (gerichteten?) Graphen definieren indem man sie als Delta-Komplexe ("Simplizialkomplexe mit Schleifen") auffasst. 


## Optimierung ##

### Fahrplanoptimierung ###

_(Zug-)Fahrplanprobleme_ kann man als Ereignisnetzwerk (E,A) modellieren. Dabei ist E (Knoten) die Menge der Ereignisse "Zug A hält an Bahnhof B" und "Zug A fährt von Bahnhof B ab" und A (Kanten) die Menge der Aktivitäten "Zug fährt" (von Bahnhof zu Bahnhof), "Zug wartet" (von Ankunft zu Abfahrt), "Umsteigen" (von Ankunft zu Abfahrt (verschiedener Züge)); zusätzlich wird über Aktivitätskanten modelliert, welcher Zug zuerst fahren darf (damit Gleise nicht mehrfach belegt sind). Für periodische Fahrpläne wird zusätzlich eine Periode T vorgegeben und dann alle Zeiten mod T gerechnet.
Aktivitätskanten erhalten zusätzlich untere und obere Zeitschranken [L_a, U_a]

	Ein Fahrplan entspricht nun einer Zuweisung von Zeiten \pi_e zu jedem Ereignis e.

-> PESP (Periodic Event Scheduling Problem): 
	min_\pi \sum_{(i,j)\in A} w_ij [\pi_j - \pi_i -L_ij] 
	s.t. L_ij <= \pi_j - \pi_i <= U_ij mod T
	     \pi_i \in {0, 1, ..., T-1}
	(NP-schwer! - enthält z.B. Hamiltonkreis-Problem)
	

### Chance Constrained Optimization ###	
	
_Chance Constrained Optimization_: Optimierungsprobleme bei denen Nebenbedingungen Zufallsvariablen sind.
* Chance Constrained Linear Programming: min c^Tx s.t. P(Ax <= b) < \epsilon, x => 0, A,b Zufallsvariablen (Unsicherheit in c kann immerin Nebenbedingungen verschoben werden)
	-> "stochastische Optimierung" (Lösung ist mit einer gewissen (kleinen) Wahrscheinlichkeit nicht zulässig)
* Uncertain Linear Optimization: {min {c^T x: Ax <= b}}_{(a,A,b) \in U}, U "Unsicherheitsmenge"
	-> robuste zulässige Lösung Ax <= b f.a. (c,A,b) \in U (selbst im "schlimmsten Fall noch zulässig" -> sehr konservativ, oft also verhältnismäßig teuer)
	
	
### Capacitated Network Design Games ###
	(aus Vortrag von Thomas Erlebach)

_Network Design Game_: Spiel läuft auf Graphen mit (festen) Kantengewichten, jeder Spieler hat einen Quell- und einen Zielknoten. Kosten von genutzten Kanten werden gleichmäßig an alle sie nutzende Spieler verteilt.

_Capacitated Network Design Game_: Network Design Game, bei denen jede Kante zusätzlich eine Kapazität hat, welche die Zahl der Spieler beschränkt, die sie gleichzeitig nutzen können. Dies sind also i.A. keine nicht-kooperativen Spiele.
	-> PoA ist unbeschränkt (Graph <|>, zwei Spieler von links nach rechts, alle Kanten Kapazität 1 und Kosten 0, außer senkrechte mit 2 und \infty.
	-> Best-Responce-Dynamik kann 2^m Schritte benötigen (auf O(m) großem Netzwerk).
	-> PoS mit max-cost als sozialen Kosten ist \theta(n log n) in asymmetrischen CND
	-> PoS mit max-cost als sozialen Kosten ist O(n) in symmetrischen CND

Ein exaktes Potential für diese Spiele ist \sum_{Kanten e}\sum_{i=1}^{last auf e} Kosten(e)/i
	
	
	
## Topostheorie ## 

Ein elementarer Topos ist eine Kategorie, die folgendes besitzt:
* Alle endlichen Limiten
* innere Homobjekte
* einen Unterobjektklassifizierer (Verallgemeinerung der 2-elementigen Menge, mit deren Hilfe man Teilmengen definieren kann (entsprechen Abbildungen in diese Menge hinein))

Einführung: https://rawgit.com/iblech/mathezirkel-kurs/master/superturingmaschinen/was-sind-und-was-sollen-die-topoi.pdf


* _geometric/first order_ theory: Alle Axiome lassen sich in der Form \forall x: (\phi => \psi) schreiben, wobei \phi und \psi geometrische Formeln sind, d.h. sie enthalten nur endliches und, unendliches oder und Existenzquantoren

* Die Gelfand-Dualität ist ein Spezialfall von Morita-Äquivalenz (= Äquivalenz mathematischer Theorien)



## ART ##

In der Newtonschen Physik wird das Gravitationspotential \Phi beschrieben durch die Gleichung 
	\Laplace\Phi = 4\pi\rho 
(wobei \rho die Dichte beschreibt und die Einheiten so gewählt sind, dass die Gravitationskonstante 1 ist  (sonst ist diese ein multiplikativer Faktor auf der rechten Seite), D.h. also "die Gravitation wird von der Dichte erzeugt"

In der ART wird die Krümmung der Raumzeit G beschrieben durch
	G = 8\pi T
D.h. also "die Gravitation wird vom Energier-Impuls-Tensor erzeugt". Warum nicht von der Dichte? Die Dichte ist Koordinatensystemabhängig! (siehe: http://scienceblogs.de/hier-wohnen-drachen/2017/02/03/der-energie-impuls-tensor/?all=1 )


## Elementares ##

Den _euklidischen Algorithmus_ kann man wie folgt geometrisch realisieren: Um denn ggT(a,b) zu bestimmen zeichne ein Rechteck mit Seitenlängen a und b. Zeichne darin nebeneinander Quadrate maximaler Seitenlänge. Wird das Rechteck damit vollständig gefüllt, entspricht die Seitenlänge des Quadrates dem ggT. Andernfalls bleibt ein ungefülltes Rechteck übrig, mit dem der Prozess wiederholt wird.