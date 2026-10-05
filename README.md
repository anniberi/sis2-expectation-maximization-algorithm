# Expectation-Maximization Algorithm

A seminar paper and from-scratch Python implementation of the Expectation-Maximization (EM) algorithm for estimating the parameters of a mixture of two normal distributions. The work presents the general EM framework and its application to Gaussian mixture models, then validates the implementation on a textbook dataset and on a larger synthetic one. Plots track how the log-likelihood and every parameter evolve across iterations.

> **Note:** Apart from this summary, everything in this project is written in Bosnian: the rest of this README, the source code, the comments and the technical documentation.

> **Napomena:** Izvorni kod, komentari i tehnička dokumentacija za ovaj projekat su napisani na bosanskom jeziku.

## O projektu

Seminarski rad iz predmeta **Signali i sistemi 2** na Elektrotehničkom fakultetu Univerziteta u Sarajevu (akademska 2022/2023. godina).

Expectation Maximization (EM) je iterativni postupak za procjenu parametara statističkih modela sa skrivenim (latentnim) varijablama metodom maksimalne vjerodostojnosti. Rad obrađuje:

1. **Generalizirani EM algoritam:** osnovna ideja i primjena na modele Gausovih mješavina (GMM).
2. **Model sa dvije normalne raspodjele:** teorijska pozadina i pseudokod algoritma.
3. **Primjer 1:** primjena na skup od 20 tačaka iz literature.
4. **Primjer 2:** primjena na sintetički skup od 10 000 tačaka.
5. **Prilog A:** korištene definicije i teoreme.
6. **Prilog B:** implementacija algoritma.

## Metodologija

Model pretpostavlja da podaci potiču iz mješavine dvije normalne raspodjele s parametrima μ₁, σ₁, μ₂, σ₂ i težinskim koeficijentom π. Algoritam naizmjenično izvodi dva koraka:

- **E-korak:** za svaku tačku računa se odgovornost (engl. *responsibility*), odnosno vjerovatnoća da tačka pripada drugoj komponenti mješavine pri trenutnim procjenama parametara;
- **M-korak:** parametri se ponovo procjenjuju kao otežane srednje vrijednosti i varijanse te kao prosječna odgovornost.

Postupak se ponavlja dok kvadrat promjene funkcije logaritamske vjerodostojnosti između dvije uzastopne iteracije ne padne ispod zadane tolerancije ε ili dok se ne dostigne maksimalan broj iteracija.

Početne vrijednosti: μ₁ i μ₂ biraju se iz skupa podataka, σ₁ i σ₂ jednake su standardnoj devijaciji cijelog skupa, a π = 0,5.

**Primjeri:**

- **Primjer 1:** 20 tačaka iz literature, tolerancija 10⁻¹⁰.
- **Primjer 2:** 4000 uzoraka iz N(20, 5²) i 6000 uzoraka iz N(40, 1²), nasumično izmiješanih, tolerancija 10⁻⁶.

Za oba primjera prikazani su histogram podataka s procijenjenom gustinom, kretanje funkcije logaritamske vjerodostojnosti i promjena svih parametara kroz iteracije.

## Struktura repozitorija

```
.
├── Kodovi/
│   ├── primjer.ipynb       # Implementacija EM algoritma i oba primjera
│   └── *.png               # Grafici koje generiše notebook
├── Slike/                  # Dodatni grafici funkcije logaritamske vjerodostojnosti
├── Prezentacija/           # Prezentacija projekta
└── Seminarski_rad_SIS2_Berina_Biberovic.pdf   # Finalna verzija rada
```

## Pokretanje

**Preduslovi:** Python 3 s paketima `numpy`, `scipy`, `matplotlib` i `jupyter`.

```bash
pip install numpy scipy matplotlib jupyter
cd Kodovi
jupyter notebook primjer.ipynb
```

Ćelije notebooka treba pokrenuti redom. Grafici se snimaju kao `.png` datoteke u direktorij `Kodovi/`. Primjer 2 koristi nasumično generisane podatke, pa se dobiveni rezultati neznatno razlikuju pri svakom pokretanju.

## Autor

- **Student:** Berina Biberović
- **Predmetni profesor:** prof. dr Emir Sokić
- **Ustanova:** Elektrotehnički fakultet, Univerzitet u Sarajevu, Odsjek za automatiku i elektroniku
