# assemblylearn
this repo is made to learn assembler in AVR uC

;
; lab01_quarantine.asm
;
; Created: 25.03.2020 13:56:13
; Author : Maciek
; 32kB dostepnego miejsca!!
;0).dyrektywa EQU, np deklaracja zmiennej .EQU decimal=10
;1).Load immediate value 'ldi'-kopiuje wartosc do wybranego rejestru
;	np ldi Rd,K gdzie de(16,31) Ke(0,255)
;2).Realtive jump 'rjmp'-nastepna wykonana instrukcja bedize pobrana
;	spod address 'adress' np rjmp address
;
;	4 sposoby na przedstawienie danych(liczba 8bitowa):hex,bin,dec,ASCII
;	a)hex 0x99=$99 =153(dec)
;	b)bin 0b1000 = 8(dec)
;	c)ASCII(znak) 'A'
;	dec bezprosrednio podajemy+mogą być tez ujemne!!
;
;
;	programowanie portów we/wy:
;	output value register 'portX'
;	direction register 'ddrX'
;	przykladowe adresy:
;	Nazwa:	Adres:	funkcja:
;	porta	$3b		output
;	ddra   $3a		direction
;	Aby wszystkie końcówki portu A pełniły rolę wyjścia należy do rejestru ddra
;	wpisać wartość 0b11111111(lub opcjonalnie 0xff,lub 255), Aby był wejsciem 
;	należy wpisać 0b00000000.Po włączeniu uC wszystkie porty mają wartosci 0 
;	w rejestrach ddr
;3).Store to SRAM 'sts'- zapis wartosci rejestru ogolnego pod podany adres
;	np: ldi r16,0x55 ;	r10=55 (in hex)
;			sts 0x3b, r10 ;  copy r10 to port A
;4). Instrukcja Output 'out'zapis zawartosci rejestru ogolnego w rejestrze we/wy
;
;ROZNICA MIEDZY STS A OUT!!:
;	adres tego samego rejestru we/wy będzie inny w instrukcji out, a inny w instrukcji
;	sts. Konkretnie adres dla sts będzie większy o wartość 32. Na przykład 'out 0x16, 
;	r20' kopiuje zawartość rejestru r20 pod adres 0x16 w przestrzeni adresowej we/wy,
;	ale w rzeczywistości jest to adres $36 w przestrzeni SRAM !!!
;
;nazwa rejestru:	adres w SRAM(sts):	adres we/wy:	funkcja:
;	porta			$3b					$1b				Wyjscie portu
;   ddra			$3a					$1a				Kierunek
;
;instrukcja Set Bit in I/O Register (sbi)
;ustawia wskazany bit w rejestrze we/wy.Instrukcja interpretuje adres
;jako adres w przestrzeni we/wy.(np sbi $12,7)
;
;sbi A, b ; ustaw bit b w rejestrze A, Ae(0,31) be(0,7)
;
;instrukcja Clear Bit in I/O Register (cbi)
;KASUJE wskazany bit w rejestrze we/wy.Instrukcja interpretuje adres
;jako adres w przestrzeni we/wy.(np cbi $12,7)
;
;cbi A,b wyczyść bit w rejestrze A,  Ae(0,31) be(0,7)
;
start:

.EQU wy=0b11111111;
ldi R16,wy;
out $1a,R16;
out $1b,R16;

sbi $1b,0;ustawienie 0 bitu = stan wysoki
cbi $1b,1;wyczyszczenie 1 bitu =stan niski(diody odwrotnie=tutaj zaswieci)

sbi $1b,2;ustawienie 2 bitu = stan wysoki
cbi $1b,3;wyczyszczenie 3 bitu =stan niski

sbi $1b,4;ustawienie 4 bitu = stan wysoki
cbi $1b,5;wyczyszczenie 5 bitu =stan niski

sbi $1b,6;ustawienie 6 bitu = stan wysoki
cbi $1b,7;wyczyszczenie 7 bitu =stan niski

stop: rjmp stop;




