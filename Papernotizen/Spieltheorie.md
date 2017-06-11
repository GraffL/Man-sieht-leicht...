## Non-Cooperative Games (John Nash - 1951) ##

* Gegenstück (kooperative Spiele): "Theory of Games an Economic Behavior" von Neumann/Morgenstern

* Zu einem gegebenen gemischten(!) Strategieprofil gibt es immer wenigstens eine reine Strategie als beste Antwort. Insbesondere genügt es daher nur reine (Alternativ-)strategien zu betrachten, wenn man prüfen will, ob ein gegebenes Strategieprofil ein Nash-Gleichgewicht ist. Ferner können nur solche reinen besten Antworten Teil eines gemischten NG sein - und umgekehrt ist das eine hinreichende Bedingung dafür ein gem. NG zu sein.

* _Theorem 1_: Jedes endliche Spiel besitzt ein gemischtes Nash-Gleichgewicht. 
		Beweis: Definiere eine Funktion auf dem (gemischten) Strategieprofilraum, die in jeder gemischten Strategie die Anteile der (reinen) besseren Antworten an der gemischten Strategie erhöht (proportional zu ihrem Verbesserungseffekt). Fixpunkte dieser Funktion entsprechen genau den gemischten NG - und existieren nach Browerschem Fixpunktsatz.
		
* *Automorphismus/Symmetrie* von Spielen: Permutation der Spieler und (passende) Permutation innerhalb der Strategieräume, sodass die induzierte Abb. auf Strategieprofilraum kostenerhaltend ist. Ein *symmetrisches (gemischtes) Strategieprofil* ist eines, das unter allen solchen Abbildungen erhalten bleibt.

* _Theorem 2_: Jedes endliche Spiel hat ein symmetrisches (gemischtes) Nash-Gleichgewicht. 
		Beweis: Menge der symmetrischen gem. Strategieprofile ist nicht-leere (uniforme Strategien sind symmetrisch) konvexe Menge und Symmetrien sind verträglich mit der Abbildung aus dem Beweis von Theorem 1. Damit folgt die Aussage mit Browerschem Fixpunktsatz (Funktion einschränken auf symmetrische Strategieprofile).
		
* Ein Spiel heißt *lösbar*, wenn die Menge der (gemischten) NGs abgeschlossen unter Austausch von einzelnen Strategien ist (also (t, r_i), s NGe => (s, r_i) NG). Ein Spiel heißt *stark lösbar*, wenn eine für den abweichenden Spieler kostenerhaltende Abweichung von einem NG zu einem weiteren NG führt.

* Einige Aussagen über die Geometrie von bestimmten Teilmengen des Strategieprofilraums (vgl. Menge der symmetrischen Profile in Th 2).

* Einbettung von kooperativen Spielen in nicht-kooperative: Mache Verhandlungen zu Beginn des Spiels zum Teil des Spiels (zusätzliche Strategien) und mache Auszahlungsfunktion davon abhängig (entspricht Transfer von Auszahlungen). Dadurch erhält man ein (unendliches) kooperatives Spiel.