# Dashboard locali

## Regola fissa: pubblicare sempre in automatico

Ogni volta che l'utente chiede una modifica, senza aspettare altre conferme:

1. Fai la modifica, commit e push sul branch di lavoro.
2. Apri tu la pull request verso `main`.
3. Uniscila (merge) subito, così il sito si aggiorna da solo. Usa il merge normale ("merge"), non "squash":
   così il branch di lavoro resta allineato a `main` e non nascono conflitti alla modifica dopo.
4. Alla fine dai all'utente il link della pull request.

L'utente l'ha chiesto espressamente: non deve aprire né unire nulla a mano.

## Tema

Stesso tema della Dashboard di Giordano (repo `gasbarrigiordano-max/dashgio`):
sfondo caldo sfumato, pannelli in vetro, accento `#F2711C`, font Manrope e
JetBrains Mono, barra a icone con suggerimenti, riquadri bianchi.

## Dati (Firebase)

Stessa cassaforte di `dashgio`: progetto Firebase `contabilit-1a500`, stesso account e stessa passphrase,
cifratura nel browser. `comune/cassaforte.js` e `comune/sfondo.svg` sono COPIE da `dashgio/comune/`:
se cambiano lì, ricopiarle qui.

```
bilancio/{uid}/locali/locali   kid, iv, ct
  {"v":2,
   "locali":[{"id","nome","perc"}],
   "tavoli":[{"id","locale","data":"AAAA-MM-GG","cent":importo in centesimi,"perc","nome","pagata"}]}
```

Gli id dei locali (room26, inspace, zonacalda, grottaaurelia, sunbay) sono fissi; nome e percentuale si cambiano.
Ogni tavolo tiene la percentuale del momento in cui è stato segnato.

## Cosa fa

Dashboard da PR: si segnano i tavoli fatti nelle serate e si calcola la propria percentuale.
Percentuali: Room 26 15%, In Space 20% (sul sito Elite si chiama HYN), Grotta Aurelia 15%, Sunbay 15%.
Zona Calda ha una gestione separata: resta nella barra con il logo, ma niente tavoli e niente totali.

Loghi in `loghi/`: room26.png e inspace.png (= hyn.png) dal repo SITO-ELITE, zonacalda.svg (diavoletto neon)
dal repo sito-zonacalda. Grotta Aurelia e Sunbay: logo da avere dall'utente (per ora la sigla).
`firestore.rules` = regole di dashgio + la sezione `locali`: vanno pubblicate a mano dalla console Firebase
(sono le regole di tutto il progetto).
