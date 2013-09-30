# Week 3
## Week 3.1.1
Maak een gekoppelde lijst waarin je NAW –gegevens opslaat. 
* Maak de Link–klasse en LinkedList–klasse. 
* Maak een methode om NAW –gegevens toe te voegen aan het begin van de 
gekoppelde lijst. 
* Maak een methode om een NAW–instantie te zoeken. 
* Maak een methode om alle NAW–gegevens te tonen. 
* Maak een methode om bepaalde NAW – gegevens te verwijderen. 


```C#
﻿using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace AlgoritmiekDatastructuren
{
    public class LinkedList<T>
    {
        public Link<NAW> First { get; set; }
        public int Size { get; private set; }

        public void AddFirst(NAW o)
        {
            Link<NAW> e = new Link<NAW>(o);

            if (Size == 0)
                First = e;
            else
            {
                e.Next = First;
                First = e;
            }
            Size++;
        }

        public bool Search(NAW n)
        {
            Link<NAW> e = First;
            while (e != null)
            {
                if (n.naam.Equals(e.Naw.naam) && n.adres.Equals(e.Naw.adres) && n.woonplaats.Equals(e.Naw.woonplaats))
                {
                    RemoveLink(e);
                    return true;
                }
                e = e.Next;
            }
            return false;
        }

        public void ShowAll()
        {
            Link<NAW> e = First;
            while (e != null)
            {
                Console.WriteLine(e.Naw.naam);
                Console.WriteLine(e.Naw.adres);
                Console.WriteLine(e.Naw.woonplaats);
                Console.WriteLine("----------");
                e = e.Next;
            }
        }

        public void RemoveLink(Link<NAW> e)
        {
            Size--;
            if (Size == 0)
                First = null;
            else
            {
                if (e == First)
                {
                    First = e.Next;
                }
                else
                {
                    Link<NAW> n = First;
                    while (n != null)
                    {
                        if (n.Next.Equals(e))
                            n.Next = n.Next.Next;
                        n = n.Next;
                    }
                }
            }
        }

        private bool WithinBounds(int index)
        {
            return !(index < 0 || index >= Size);
        }

        public Link<NAW> getEntry(int n)
        {
            Link<NAW> e = First;

                while (n-- > 0)
                    e = e.Next;
            return e;
        }
    }
}
```

## Week 3.1.2
Je kunt een gekoppelde lijst waar NAW – gegevens in zijn opgeslagen maken met 
verschillende Link – klassen. In deze opgave ga je voor twee verschillende 
benaderingen een objectdiagram maken. Van elke benadering worden de 
attributen van de Link –klasse beschreven:
![Instance diagram](http://i.imgur.com/bQyrSh5.jpg)

![Instance diagram](http://i.imgur.com/ZNKpYVC.jpg)

## Week 3.1.3
Maak een methode waarmee je een instantie uit een gekoppelde lijst kunt 
opvragen aan de hand van de index (een accessor). Met de methode 
getAt(int index) geef je de instantie met “index” terug of null als ie 
niet bestaat. In de volgende gekoppelde lijst geeft getAt(2) de waarde 6 
terug.
_GetAt_
```C#
 public NAW GetAt(int index)
        {
            if (!WithinBounds(index))
            {
                return default(NAW);
            }
            return getEntry(index).Naw;
        }
```

_SetAt_
```C#

        public NAW SetAt(int index, NAW o)
        {
            if (!WithinBounds(index))
            {
                return default(NAW);
            }
            Link<NAW> e = getEntry(index);
            NAW old = e.Naw;
            e.Naw = o;
            return old;
        }
```

Maak twee methode met de naam length1() en length2() waarmee je 
kunt opvragen hoeveel elementen een gekoppelde lijst heeft. In de eerste 
methode tel je het aantal knooppunten (Link–instanties). In de tweede methode 
geef je de waarde van het attribuut private int length waarin het 
aantal Links staat, terug. Dit attribuut dient in andere methodes aangepast te 
worden.

_Length1_ & _Length2_
```C#
 private int Length1()
        {
            Link<NAW> e = First;
            int count = 1;
            while (e != null)
            {
                count++;
                e = e.Next;
            }
            return count;
        }

        private int Length2()
        {
            return Size;
        }
```

## Week 3.1.4
Herschrijf het bubble – sort –algoritme zodat je met behulp van de 
getAt – methode een gekoppelde lijst kunt sorteren.
```C#
public static void BubbleSort(LinkedList<NAW> list)
        {
            Link<NAW> current = list.First;
            bool foundChange = true;
            while (foundChange)
            {
                foundChange = false;
                while (current.Next != null)
                {
                    if (String.Compare(current.Naw.naam, current.Next.Naw.naam)>0)
                    {
                        NAW n = current.Naw;
                        current.Naw = current.Next.Naw;
                        current.Next.Naw = n;
                        foundChange = true;
                    }
                    else if (String.Compare(current.Naw.naam, current.Next.Naw.naam) == 0 && String.Compare(current.Naw.adres, current.Next.Naw.adres) > 0)
                    {
                        NAW n = current.Naw;
                        current.Naw = current.Next.Naw;
                        current.Next.Naw = n;
                        foundChange = true;
                    }
                    else if (String.Compare(current.Naw.naam, current.Next.Naw.naam) == 0 && String.Compare(current.Naw.adres, current.Next.Naw.adres) == 0 && String.Compare(current.Naw.woonplaats, current.Next.Naw.woonplaats) > 0)
                    {
                        NAW n = current.Naw;
                        current.Naw = current.Next.Naw;
                        current.Next.Naw = n;
                        foundChange = true;
                    }
                    current = current.Next;
                }
                current = list.First;
            }
        }
```

Geef in de big–O Notatie aan van welke orde dit algoritme is. Verklaar 
je antwoord. 
_Het algoritme is ook O(N^2) aangezien we hier weer twee genest loops hebben die beide grooter worden zodra de input groote toeneemt._


Vul een gekoppelde lijst met respectievelijk 100, 1000, 10.000 en 
100.000 random – waarden. Onderzoek de sorteersnelheid. Komt 
deze overeen met de orde van het algoritme? Verklaar je antwoord.
_Ja zodra we de grootte met 10-voud verhogen wordt de executie tijd ongeveer 10^2 keer zo groot. Zelfs met 1.000.000 waardes._
