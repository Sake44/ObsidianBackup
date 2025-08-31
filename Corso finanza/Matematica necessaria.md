Come calcolare il rendimento di un asset. Banalmente sarebbe x (investimento iniziale) - y (costo al momento di vendita). 
In finanza il guadagno si esprime in percentuale. 
La variabile cardine della finanza è il tempo (t). 
Il tempo in finanza è fondamentale. A seconda di quando accadono gli eventi cambia moltissimo. 

Per calcolare il rendimento di un asset: 
```
(x-y)/y

# Dove y è l'investimento iniziale e x è il profitto
```

Per esempio, consideriamo: 
Investimento iniziale (01/01/2025): 173,94 euro
Investimento maturato(01/01/2026): 273,94 euro

Secondo quanto detto prima, per calcolare il nostro ritorno possiamo:
```
Investimento maturato/Investimento iniziale -1
```

Se consideriamo di reinvestire la stessa somma, l'anno successivo (01/01/2027), il nostro investimento maturato sarà: 
```
Investimento maturato (2026) + Investimento maturato (2026) * gain (anno precedente)
```

Di conseguenza se il nostro gain è stato: 57%, avremo:
```
273,94 + 273,94 * 57%
```
Dovremmo usare questa formula: 
```
(1 + 57%) * 273,94
```

In finanza viene definito come **Interesse composto**. 
Formula per annualizzare i rendimenti:
```
(1+ rendimento)^(365/(inizio investimento - fine inv)) -1
```

### TIR (Tasso Interno di Rendimento)
Per calcolare il rendimento di un investimento che dura nel tempo dobbiamo tenere conto proprio del tempo (t). Le cose successe prima in finanza valgono di più. 
Per farsi che l'interesse composto abbia veramente effetto si devono avere tanti anni di investimento.
Come possiamo tenere conto del tempo sul nostro investimento? VAN o TIR.
Possiamo calcolare il TIR con la formula Excel XIRR:
```
=XIRR(inv init:prof fin;init inv;fin inv)
```
