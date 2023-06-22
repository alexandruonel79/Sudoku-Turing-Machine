# Sudoku-Turing-Machine
 	 Masina Turing care verifica daca un joc de sudoku primit este valid.

Am inceput tema prin a imparti in mai multe probleme,cum erau punctate:linii,coloane
si regiuni.M am gandit ca pot sa fac 3 masini Turing diferite care rezolva problemele
individual si apoi le puteam uni(cand programul ajungea in starea Y inlocuiam cu o noua
stare care continua urmatorul subpunct).Gandirea generala a fost determinarea tuturor 
cazurilor posibile si tratarea acestora.Astfel eficienta din punct de vedere al pasilor
este mai buna,dar creste numarul de stari deci eficienta din punct de vedere al memoriei
scade.

Pe subcapitole:

	Problema pe linii:

Am inceput prin determinarea primei cifre.De exemplu daca numarul este 1234,la gasirea
primei cifre 1 ma voi afla in starea linia1.De acolo ma astept la 2,3 sau 4 fiindca 1 l am gasit deja.Altfel
voi returna N la gasirea lui 1.Am gasit 2 deci trec in starea linia12 unde vreau sa gasesc 3 sau 4 si sa trec
in starea linia123 sau linia124 unde se face verificarea finala.In cazul in care linia este valida voi trece in 
starea start si continui cu urmatoarea linie.Cand ajung la final, in cazul in care liniile au fost corecte trec in 
starea reset unde ma deplasez inapoi pana la inceputul sirului si ma duc in starea prima care face parte din 
problema coloanelor.

	Problema pe coloane:

Este aceasi idee ca la linii,trec in starea prima1 daca prima cifra de pe coloana este 1,iar noutatea este
faptul ca trec intr o stare avans1_4 care va trece in avans1_3 care va trece in avans1_2 si tot asa pana in avans1_0
pentru a ajunge sa verifice cifra corecta.Practic trebuie sa sarim peste cifrele care nu conteaza la verificarea coloanelor
si folosim starile avans pentru asta.In cazul de succes se va duce intr o stare r_col1 si ma voi plasa cu inca 2 stari calibrare
pe pozitia corespunzatoare pentru a incepe verificarea coloanei 2.Aceasta verificare se face prin starea doua in loc de prima.
Singurele modificari sunt inlocuirea avans cu 2avans deoarece ne aflam la a doua coloana,la sectiunea de 2avans_1 a existat o 
problema, am modificat cazul cu ":" deoarece trebuie trecut fortat in starea 2avans_0 pentru coloana a 2a.Dupa toate verificarile,
in cazul de succes voi trece in starea r_col2 care analog cu r_col1.Ideea algoritmului continua pana la ultima coloana unde voi trece
in verificarea regiunilor in caz de succes prin starea "continuare".

	Problema pe regiuni:

Conceptual la fel,am redenumit avans in advance si prima,doua,treia,patra in first,second,third,fourth.De data aceasta la regiuni
este nevoie doar de o deplasare pentru a treia cifra unde ma voi folosi de advance_4 care trece prin cele 5 stari pentru a ajunge la a treia
cifra.Daca pentru prima verificare este okay,voi trece in r_reg1 unde ma folosesc de inapoi pentru a ma pozitiona pentru urmatoarea verificare.
A doua jumatate se face la fel, advance devine 2advance si first devine second.Diferenta vine de la trecerea regiunii 2 la 3 unde avansez in 
loc sa merg inapoi desi am lasat acelasi nume starii(2_inapoi).Apoi se repeta acelasi algoritm de la primele 2 regiuni.

Am colorat in excel pentru exemplul la linii,toate avand aceasi idee la baza.
