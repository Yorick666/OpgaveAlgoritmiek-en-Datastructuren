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

```C#
 public int zoek(NAW waarde)
        {
            int midden, laag = 0, hoog = AANTAL - 1;

            while (laag <= hoog)
            {
                midden = (laag + hoog) / 2;

                if (Gegevens[midden].CompareTo(waarde) == 0)
                    return midden;

                if (Gegevens[midden].CompareTo(waarde) < 0)
                    laag = midden + 1;
                else
                    hoog = midden - 1;
            }

            return AANTAL;
        }
```

## Week 1.2.2
In het instance diagram is geen verschil met die uit opgave 1.1.3.
![ Week 1.2.2 Instance Diagram](http://i.imgur.com/qYMHLmR.jpg)
De gegevens veranderen niet, alleen de methodes om te sorteren vernaderen.


