** Dynamische Systeme ** 

Ein _dynamisches System_ (auf einem Raum X) ist gegeben durch eine Funktion F: X x T -> X. Diese gibt an, wie sich Elemente des Zustandsraumes X im Laufe der Zeit T ändern. Für T = IN ist F oft gegeben durch eine Funktion f: X -> X und F(x,n) := f^n(x), d.h. für jeden Zeitschritt wird einmal f angewandt.

Eine _Kontrollmenge_ D \subseteq M (M Mfg) ist eine maximale Teilmenge mit den beiden Eigenschaften:
	* Kontrollierte Invarianz: \forall x \in D: \exists u \in U (Kontrollfunktionen): \phi(IR_+,x,u) \subseteq D (\phi(_,x,u) Lsg d. definierierenden Differenzialgleichung mit Anfangswert x)
		(d.h. Kontrollfluss bleibt in D)
	* Approximative Kontrolloerbarkeit: \forall x,y \in D, \epsilon > 0: \exists u \in U, T > 0: d(\phi(T,x,u), y) < \epsilon 
		(d.h. Kontrollfluss läst sich beliebig nahe an y steuern)
		
Ein linearer Operator A: IR^n -> IR^n heißt _hyperbolisch_ :<=> A hat keine EWe auf S^1 <=> IR^n = E^- + E^+: AE^+ \subseteq E^+ und A ist auf E^- Kontraktion und auf E^+ Expansion.

Gleichmäßige Hyperbolizität modelliert chaotisches Verhalten.



** Algebra **

Warum können die Quarternionen kein Körper sein? Dann wären sie eine endliche Körpererweiterung von IC - IC ist aber algebraisch abgeschlossen und enthält damit alle algebraischen Ereweiterungen.
	-> In welchem Sinne ist das wirklich eine Antwort? Setzt das z.B. schon voraus, dass die IC ein Unterring von IH sein soll?
	

** Algebraische Topologie **

Motto: Für ausreichend gute Raumpaare gilt: Homologie von Raumpaar = Homologie von Quotient der beiden Räume
	-> gilt bspw. NICHT für RP^n, RP^{n-1} (siehe AlgTopo B11/A3)
	
*** Spektra ***

Ein Spektrum E ist eine Folge punktierter CW-Komplexe (E_n, *)_{n\in IZ}, sodass \Sigma E_n \subseteq E_{n+1} (die Einhängung von E_n hat (zelluläre) Inklusion in E_{n+1})

Ein Unterspektrum E' \subseteq E heißt kofinal :<=> jede Zelle in E liegt "irgendwann" (nach endlich vielen Einhängungen) in E'

Ein Morphismus zwischen Spektra f: E -> F ist eine auf einem kofinalen Unterspektrum definierte Abbildung f: E' -> F, f_n:E'_n -> F_n, s.d.:
	  E'_{n+1}  ----f_{n+1}--->   F_{n+1}
	     U|                          U|
	\Sigma E'_n --\Sigma f_n--> \Sigma F_n
kommutiert.


