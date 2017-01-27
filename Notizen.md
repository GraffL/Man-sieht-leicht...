** Dynamische Systeme ** 

Ein _dynamisches System_ (auf einem Raum X) ist gegeben durch eine Funktion F: X x T -> X. Diese gibt an, wie sich Elemente des Zustandsraumes X im Laufe der Zeit T �ndern. F�r T = IN ist F oft gegeben durch eine Funktion f: X -> X und F(x,n) := f^n(x), d.h. f�r jeden Zeitschritt wird einmal f angewandt.

Eine _Kontrollmenge_ D \subseteq M (M Mfg) ist eine maximale Teilmenge mit den beiden Eigenschaften:
	* Kontrollierte Invarianz: \forall x \in D: \exists u \in U (Kontrollfunktionen): \phi(IR_+,x,u) \subseteq D (\phi(_,x,u) Lsg d. definierierenden Differenzialgleichung mit Anfangswert x)
		(d.h. Kontrollfluss bleibt in D)
	* Approximative Kontrolloerbarkeit: \forall x,y \in D, \epsilon > 0: \exists u \in U, T > 0: d(\phi(T,x,u), y) < \epsilon 
		(d.h. Kontrollfluss l�st sich beliebig nahe an y steuern)
		
Ein linearer Operator A: IR^n -> IR^n hei�t _hyperbolisch_ :<=> A hat keine EWe auf S^1 <=> IR^n = E^- + E^+: AE^+ \subseteq E^+ und A ist auf E^- Kontraktion und auf E^+ Expansion.

Gleichm��ige Hyperbolizit�t modelliert chaotisches Verhalten.



** Algebra **

Warum k�nnen die Quarternionen kein K�rper sein? Dann w�ren sie eine endliche K�rpererweiterung von IC - IC ist aber algebraisch abgeschlossen und enth�lt damit alle algebraischen Ereweiterungen.
	-> In welchem Sinne ist das wirklich eine Antwort? Setzt das z.B. schon voraus, dass die IC ein Unterring von IH sein soll?

	

** Algebraische Topologie **

Motto: F�r ausreichend gute Raumpaare gilt: Homologie von Raumpaar = Homologie von Quotient der beiden R�ume
	-> gilt bspw. NICHT f�r RP^n, RP^{n-1} (siehe AlgTopo B11/A3)
	
*** Spektra ***

Ein Spektrum E ist eine Folge punktierter CW-Komplexe (E_n, *)_{n\in IZ}, sodass \Sigma E_n \subseteq E_{n+1} (die Einh�ngung von E_n hat (zellul�re) Inklusion in E_{n+1})

Ein Unterspektrum E' \subseteq E hei�t kofinal :<=> jede Zelle in E liegt "irgendwann" (nach endlich vielen Einh�ngungen) in E'

Ein Morphismus zwischen Spektra f: E -> F ist eine auf einem kofinalen Unterspektrum definierte Abbildung f: E' -> F, f_n:E'_n -> F_n, s.d.:
	  E'_{n+1}  ----f_{n+1}--->   F_{n+1}
	     U|                          U|
	\Sigma E'_n --\Sigma f_n--> \Sigma F_n
kommutiert.



** Optimierung **

*** Fahrplanoptimierung ***

_(Zug-)Fahrplanprobleme_ kann man als Ereignisnetzwerk (E,A) modellieren. Dabei ist E (Knoten) die Menge der Ereignisse "Zug A h�lt an Bahnhof B" und "Zug A f�hrt von Bahnhof B ab" und A (Kanten) die Menge der Aktivit�ten "Zug f�hrt" (von Bahnhof zu Bahnhof), "Zug wartet" (von Ankunft zu Abfahrt), "Umsteigen" (von Ankunft zu Abfahrt (verschiedener Z�ge)); zus�tzlich wird �ber Aktivit�tskanten modelliert, welcher Zug zuerst fahren darf (damit Gleise nicht mehrfach belegt sind). F�r periodische Fahrpl�ne wird zus�tzlich eine Periode T vorgegeben und dann alle Zeiten mod T gerechnet.
Aktivit�tskanten erhalten zus�tzlich untere und obere Zeitschranken [L_a, U_a]

	Ein Fahrplan entspricht nun einer Zuweisung von Zeiten \pi_e zu jedem Ereignis e.

-> PESP (Periodic Event Scheduling Problem): 
	min_\pi \sum_{(i,j)\in A} w_ij [\pi_j - \pi_i -L_ij] 
	s.t. L_ij <= \pi_j - \pi_i <= U_ij mod T
	     \pi_i \in {0, 1, ..., T-1}
	(NP-schwer! - enth�lt z.B. Hamiltonkreis-Problem)
	

*** Chance Constrained Optimization ***	
	
_Chance Constrained Optimization_: Optimierungsprobleme bei denen Nebenbedingungen Zufallsvariablen sind.
* Chance Constrained Linear Programming: min c^Tx s.t. P(Ax <= b) < \epsilon, x => 0, A,b Zufallsvariablen (Unsicherheit in c kann immerin Nebenbedingungen verschoben werden)
	-> "stochastische Optimierung" (L�sung ist mit einer gewissen (kleinen) Wahrscheinlichkeit nicht zul�ssig)
* Uncertain Linear Optimization: {min {c^T x: Ax <= b}}_{(a,A,b) \in U}, U "Unsicherheitsmenge"
	-> robuste zul�ssige L�sung Ax <= b f.a. (c,A,b) \in U (selbst im "schlimmsten Fall noch zul�ssig" -> sehr konservativ, oft also verh�ltnism��ig teuer)
	
	
	
** Topostheorie ** 

Ein elementarer Topos ist eine Kategorie, die folgendes besitzt:
* Alle endlichen Limiten
* innere Homobjekte
* einen Unterobjektklassifizierer (Verallgemeinerung der 2-elementigen Menge, mit deren Hilfe man Teilmengen definieren kann (entsprechen Abbildungen in diese Menge hinein))