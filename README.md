# 🍕 PIZZACURTA Game - Vicenza

Risoluzione di un problema di ottimizzazione (*Set Covering Problem*) per l'apertura di nuove sedi della catena di pizzerie **PIZZACURTA** nella città di Vicenza.

## 🎯 Il Problema

L'obiettivo è individuare i quartieri ottimali in cui aprire le pizzerie in modo da:
1. Garantire che tutti i cittadini dei **22 quartieri** di Vicenza possano raggiungere almeno una sede in massimo **5 minuti**.
2. **Minimizzare il costo totale di affitto** delle sedi scelte.

### Assunzioni del modello
* Tutti i residenti di un quartiere sono concentrati nelle coordinate del sito potenziale (fornite nel dataset `Pizzeria_VI_dati.csv`).
* Le distanze sono calcolate in linea d'aria.
* La velocità media di percorrenza è di $20\text{ km/h}$.

## ⚙️ Metodologia di Risoluzione

1. **Conversione Coordinate:** Trasformazione delle coordinate geografiche (Latitudine, Longitudine) in coordinate planari metriche tramite il sistema ENU (*East-North-Up*) usando la libreria `pymap3d`.
2. **Raggio di Copertura:** Calcolo della distanza massima percorribile in $5\text{ minuti}$ a $20\text{ km/h}$, pari a un raggio $R \approx 1666.67\text{ metri}$.
3. **Pre-processing (Riduzione del problema):**
   * **Isolati singoli:** Individuazione dei quartieri che non possono essere coperti da nessun altro sito (scelta obbligata).
   * **Coppie indipendenti:** Individuazione di coppie di quartieri isolate dal resto della mappa, selezionando direttamente la sede con l'affitto minore.
4. **Ricerca Esaustiva:** Calcolo delle combinazioni valide sui quartieri rimanenti per trovare il sottoinsieme che garantisce il $100\%$ di copertura al costo totale minimo.
5. **Esportazione:** Generazione della matrice di adiacenza/copertura (`matrix.csv`) per la risoluzione tramite programmazione lineare (Metodo del Simplesso).

## 🛠️ Librerie Utilizzate

Il codice è scritto in Python e richiede le seguenti librerie:

```bash
pip install pandas numpy matplotlib pymap3d geopy
```

## 👤 Autore

* **Tommaso Pintonato** (Matricola: 2069337)
