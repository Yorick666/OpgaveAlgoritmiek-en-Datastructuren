# Week 1
## Week 1.2.1

### Tip : CompareTo()
```C#
 public int CompareTo(NAW other)
        {
            if (other == null)
            {
                return 1;
            }

            if (other.Woonplaats != Woonplaats)
            {
                return Woonplaats.CompareTo(other.Woonplaats);
            }

            if (other.Naam != Naam)
            {
                return Naam.CompareTo(other.Naam);
            }

            if (other.Adres != Adres)
            {
                return Adres.CompareTo(other.Adres);
            }
            return 0;
        }
```

Schrijf een methode om:
* een NAW – instantie te zoeken. Schrijf een binair zoekalgoritme.
* een NAW – instantie toe te voegen.
* een NAW – instantie (met in te voeren eigenschappen) te verwijderen
* een NAW – instantie te wijzigen

```C#
public int zoek(NAW waarde)
        {
            int midden, laag = 0, hoog = AANTAL - 1;

            while (laag <= hoog)
            {
                midden = (laag + hoog) / 2;

                if (Gegevens[midden].CompareTo(waarde) == 0)
                {

                    return midden;
                }
                else if (Gegevens[midden].CompareTo(waarde) < 0)
                {
                    laag = midden + 1;
                }
                else
                {
                    hoog = midden - 1;
                }
            }

            return AANTAL;
        }


        public void toevoegen(NAW nieuweNAW)
        {
            int index = Gegevens.Length + 1;
            Gegevens[index] = nieuweNAW;
        }

        public void Verwijder(string naam, string woonplaats, string adres)
        {
            for (int i = AANTAL; i > 0; i--)
            {
                if (Gegevens[i].HeeftAdres(adres) && Gegevens[i].HeeftWoonplaats(woonplaats) && Gegevens[i].HeeftNaam(naam))
                {
                    Verwijder(i);
                }
            }
        }

        public void wijzig(NAW oud, NAW nieuw)
        {
            int index = zoek(oud);
            Gegevens[index] = nieuw;
        }
```

## Week 1.2.2
In het instance diagram is geen verschil met die uit opgave 1.1.3.
![ Week 1.2.2 Instance Diagram](http://i.imgur.com/qYMHLmR.jpg)
De gegevens veranderen niet, alleen de methodes om te sorteren vernaderen.


