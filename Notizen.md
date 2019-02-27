## Allgemeines ##

### Ungleichungen/Abschätzungen ###

* (aus Bachelorarbeitsvortrag von Lukas Hofelich):
	-- Verwende bekannte Ungleichungen um zu zeigende Ungleichung als Linearkombination davon (mit noch zu wählenden Koeffizienten) zu formulieren
	-- erhalte Restriktionen an die Koeffizienten daraus, dass die zu zeigende(n) Ungleichung(en) gelten müssen.
	-- erhalte eine Variable, die die Stärke der Gesamtabschätzung beschreibt (etwa m in: x <= ... <(aus Lin.komb.)= ... <= m y)
	Löse LP: "min m udN Restriktionen an Koeffizienten + Zusammensetzung von m aus Koeffizienten" um bestmögliche Abschätzung zu erhalten


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
	
	
Motto: Homotopietheorie untersucht Wegzusammenhang, Homologietheorie untersucht Zusammenhang (von Eschenburg, via Stefan A.)
	-> Frage: Was bedeutet das konkreter?
	-> Frage: Aus Wegzusammenhang folgt Zusammenhang. Zeigt das einen Zusammenhang zwischen Homotopie- und Homologietheorie?
	
	
Motto: Kohomologie ist besser/einfacher/...(?) als Homologie (zumindest scheint man öfter ersteres anzuwenden)
	-> Frage: Stimmt das überhaupt? Falls ja, warum bzw. in welchem Sinne?
	
	
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


### Vermischtes ###

* Möchte man in einem Optimierungsproblem "dünne" Vektoren (mit vielen Nulleinträgen) bevorzugen, kann man einen Term \tau ||x||_1 zur Zielfunktion addieren. Soll die Zielfunktion differenzierbar sein, kann man den Betrag durch Pseudo-Huber-Approximation ersetzen: |x| -> \sqrt(\mu^2 + x_1^2) - \mu

* _P-Repräsentation_ eines Polyeders: P = {Mx | a <= Bx <= b, l <= x <= u} -> Ziel: Bestimme _V-Repräsentation_ P = {x | ... }
	zugehöriges Problem: (MOLP) min (Mx, -e^TMx) udN a <= Bx <= b l <= x <= u
	
* _Stackelberg-Game_: 2 Spieler: "Leader" entscheidet zuerst, dann entscheidet "Follower" (wobei er die Entscheidung des Leaders kennt)

* _Generalized Nash Games_: Strategieraum von Spieler i hängt von den gewählten Strategien der anderen Spieler ab, ist also von der Form X_i(x^{-i}). Verallgemeinertes Nash-Gleichgewicht ist NG in diesem Spiel (Abweichung im jeweils durch die momentane Strategie bestimmten Strategieraum des jeweiligen Spielers). Bspw. kann der Strategieraum jetzt ein Polyeder sein. Andere Sichtweise: Jeder Spieler hat ein spielerspezifisches Optimierungsproblem mit von den Strategien der anderen Spieler abhängigen Restriktionen.

* _Standard Quadratic Problem_: max {x^TAx | x \in D} mit D := {x >= 0 | e^T x = 1}. Beobachtung: Ist A eine Adjazenzmatrix, so entspricht das Problem der Suche nach einer maximalen Clique. (warum?)

* _(enlarged) inner parallel set_: Eine aus dem gegebenen Zulässigkeitsbereich eines MILP erhaltener Bereich (spezieller Bauart), sodass jede darauf gefundene Lösung auch nach Runden noch zulässig ist. "Inner parallel set" ist also einfach die entsprechende Verkleinerung der relaxierten Zulässigkeitsmenge. 

* Umwandeln eines Biobjective Minimization Problems (min f_1(x) und min f_2(x) udN x \in X) in eine Single Objective Problem:
	** _Weighted Sum_: min (f_1(x) + \gamma f_2(x)) udN x \in X (für ein fest gewähltes \gamma > 0)
	** Budget constraint_: min f_2(x) udN f_1(x) <= B, x \in X (für ein fest gewähltes B > 0)
	Aus \alpha-Approximationsagorithmus für Weighted Sum erhält man (\alpha(1+2\epsilon), \alpha(1+1/\epsilon))-Approximations Algorithmus für Budget (d.h. Budget wird nur bis auf zweite Konstante eingehalten)
	
* Ein Mengensystem ist genau dann ein Matroid, wenn für jede denkbare Kostenfunktion auf den Mengen der Greedy-Ansatz eine optimale Lösung findet. Ein Beispiel dafür, dass es nicht genügt, wenn Greedy für eine bestimmte Kostenfunktion optimal ist, ist das "Cabin Manager"-Problem (entspricht Maximum Independent Set für Intervallgraphen)

* Vereinigung (mit nicht notwendigerweise identischen Grundmengen) und direkte Summe (entspricht Vereinigung von disjunkten Grundmengen) von Matroiden sind Matroide.
	-> Daher kann man Greedy bspw. auch nutzen, um minimale disjunkte Spannbäue zu finden
	Hat man für die vereinigten Matroide "Unabhängigkeitsorakel" (welche besagen, ob eine Menge unabhängig ist oder nicht), so erhält man auch ein Orakel für den Vereinigungsmatroid (zumindest im Falle identischer Grundmengen).
	
* _Generic Covering/Packing Problem_: E endliche Menge, F Familie von Teilmengen von E, c Kapazitätsvektor, r Rewardvektor(beide ganzzahlig), A ganzzahlige positive Matrix. 
		** Dann min{c^T x | Ax >= r, x >= 0} Covering Problem
		** Dann max{r^T y | A^T y <= c, y >= 0} Packing Problem (dual)
	
	
	
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


## Geometrie ##

