# assemblylearn
this repo is made to learn assembler in AVR uC
;
; lab01_quarantine.asm
;
; Created: 25.03.2020 13:56:13
; Author : Maciek
; 32kB dostepnego miejsca!!
;dyrektywa EQU
;1.Load immediate value 'ldi'-kopiuje wartosc do wybranego rejestru
;np ldi Rd,K gdzie de(16,31) Ke(0,255)
;2.Realtive jump 'rjmp'-nastepna wykonana instrukcja bedize pobrana
;spod address 'adress' np rjmp address
;
;4 sposoby na przedstawienie danych(liczba 8bitowa):hex,bin,dec,ASCII
;a)hex 0x99=$99 =153(dec)
;b)bin 0b1000 = 8(dec)
;c)ASCII(znak) 'A'
;dec bezprosrednio podajemy+mogą być tez ujemne!!
;
; Replace with your application code

.EQU decimal=10
.EQU hex=$99
.EQU binary=0b1100
.EQU ascii='A'

ldi R16,decimal;   10dec
ldi R17,hex; 153dec
ldi R18,binary; 12 dec
ldi R19,ascii
stop: rjmp stop

