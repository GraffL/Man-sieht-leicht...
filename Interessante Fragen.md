Was hat der "SO(3)-Handtrick" mit der tatsächlichen topologischen Struktur von SO(3) zu tun? Insbesondere: Warum codiert die Verdrehung des Armes die Zusammenziehbarkeit einer Kurve (der Hand)?
	-> evtl. besser verständliche Variante mit einem an beiden Enden festgehaltenen Gürtel?

-------------------	
	
Wie viel Prozent der Zahlen im Pascalschen Dreieck sind ungerade? Evtl. besteht hier ein Zusammenhang zur Hausdorff-Dimension (= fraktale Dimension?) des Sirpinski-Dreiecks, das man ja erhält, wenn man alle ungerade Zahlen anmalt.

-------------------

Warum bricht die Regel Integral(x^n) = 1/n \* x^(n-1) für n = -1? Antwort von http://math.stackexchange.com/a/2157376 :  
Betrachte \integral_a^b x^n dx = \integral_a^2a x^n dx + \integral_2a^4a x^n dx + \integral_4a^8a + ... + \integral_0.5b^b x^n dx (log (b/a) Summanden)  
Ist n < -1, so dominiert der erste Summand, ist n > -1, so dominiert der letzte Summand. Ist aber n = -1, so sind alle Summanden gleich und man erhält folglich (bis auf einen konstanten Faktor) log(b/a) = log(b)-log(a).  
Denn \integral_{2^k a}^{2^(k+1) a} x^n dx ={Substitution x = 2^k y}= \integral_{a}^{2a} 2^(kn) y^n 2dy = 2^(kn+1) \integral_{a}^{2a} y^n dy  
Frage: Kann man jetzt auch irgendwas für die Fälle n != -1 sagen?

Ein ähnliches (gleiches?) Phänomen tritt beim Mastertheorem auf: Es gibt drei Fälle: Der erste Rekursionsschritt dominiert, der letzte Rekursionsschritt dominiert (und damit die Anzahl dieser) oder beide haben gleiches "Gewicht" - und man erhält einen logarithmischen Faktor in der Laufzeit (vgl. Anschauung im Informatik III-Skript von Professor Hagerup)