# Dashboard locali

## Regola fissa: pubblicare sempre in automatico

Ogni volta che l'utente chiede una modifica, senza aspettare altre conferme:

1. Fai la modifica, commit e push sul branch di lavoro.
2. Apri tu la pull request verso `main`.
3. Uniscila (merge) subito, così il sito si aggiorna da solo.
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
bilancio/{uid}/locali/locali   kid, iv, ct   {"v":1,"locali":[{"id","nome"}]}
```

Gli id dei locali (room26, inspace, zonacalda, grottaaurelia, sunbay) sono fissi; il nome si cambia.
`firestore.rules` = regole di dashgio + la sezione `locali`: vanno pubblicate a mano dalla console Firebase
(sono le regole di tutto il progetto).
