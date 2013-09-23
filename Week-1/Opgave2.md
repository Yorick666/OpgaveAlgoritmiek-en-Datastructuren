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

## Week 1.2.3.a

```C#
 public int find(int searchKey)
        {

            int lowerBound = 0;
            int upperBound = nElems - 1;
            int curIn;
            while (true)
            {
                curIn = (lowerBound + upperBound) / 2;
                if (a[curIn] == searchKey)
                    return curIn; // found it
                else if (lowerBound > upperBound)
                {
                    Console.WriteLine("LowerBound= " + lowerBound);
                    Console.WriteLine("UpperBound= " + upperBound);
                    Console.WriteLine("------------");
                    return nElems; // can’t find it
                }
                else // divide range
                {
                    if (a[curIn] < searchKey)
                        lowerBound = curIn + 1; // it’s in upper half
                    else
                        upperBound = curIn - 1; // it’s in lower half
                } // end else divide range
            } // end while
        } // end find()
```
        
## Week 1.2.3.b

    LB: 0
    UB: -1

    LB: 1
    UB: 0

    LB: 2
    UB: 1

    LB: 6
    UB: 5

    LB: 6
    UB: 5

    LB: 7
    UB: 6


## Week 1.2.3.c

Als de array gesorteerd is van laag naar hoog, dan zal de gezochte waarden ergens tussen lower en upper bounds moeten liggen, zolang de lower bound kleiner is dan de upper bound.

## Week 1.2.3.d

```C#
public int findAdd(int addKey)
        {

            int lowerBound = 0;
            int upperBound = nElems-1;
            int curIn;

            while (true)
            {
                curIn = (lowerBound + upperBound) / 2;
                if (a[curIn] == addKey)
                {
                    Console.WriteLine("Added " + addKey + " to index: " + AddKey(addKey, curIn + 1));
                    for (int i = 0; i < nElems; i++)
                    {
                        Console.WriteLine(a[i]);
                    }
                    return (curIn + 1); // found it
                }
                else if (lowerBound > upperBound)
                {
                    Console.WriteLine("Added " + addKey +" to index: " + AddKey(addKey, lowerBound));
                    for (int i = 0; i < nElems; i++)
                    {
                        Console.WriteLine(a[i]);
                    }
                    return nElems; // can’t find it
                }
                else // divide range
                {
                    if (a[curIn] < addKey)
                        lowerBound = curIn + 1; // it’s in upper half
                    else
                        upperBound = curIn - 1; // it’s in lower half
                } // end else divide range
            } // end while
        } // end find()

        private int AddKey(int key, int index)
        {
            for (int i = nElems; i >= index; i--)
            {
                if(a.Length!=i+1)
                a[i + 1] = a[i];
                if (i == index)
                    a[i] = key;

            }
            nElems++;
            return index;
        }
```
