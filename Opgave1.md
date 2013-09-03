# Week 1
## Opgave 1
```C#
class NAW
    {
        public string Naam {get; set;}
        public string Adres { get; set; }
        public string Woonplaats { get; set; }

        public bool HeeftNaam(string naam)
        {
            return Naam == naam;
        }

        public bool HeeftAdres(string adres)
        {
            return Adres == adres;
        }

        public bool HeeftWoonplaats(string woonplaats)
        {
            return Woonplaats == woonplaats;
        }
    }
```

## Opgave 2
```C#
class VulClass
    {
        NAW[] Gegevens = new NAW[20];
        const int AANTAL = 10;

        public VulClass()
        {
            for (int i = 0; i < AANTAL; i++)
            {
                NAW nieuweGegevens = new NAW();
                    nieuweGegevens.Naam = "Pietje" + i;
                    nieuweGegevens.Adres = "Blaatstraat 1" + i + " 100" + i + "AA";
                    nieuweGegevens.Woonplaats = "Arnhem" + i;

                Gegevens[i] = nieuweGegevens;
            }
        }

        public int ZoekNaam(string naam)
        {
            for (int i = 0; i < AANTAL; i++)
            {
                if (Gegevens[i].HeeftNaam(naam))
                {
                    return i;
                }
            }
            return -1;
        }

        public int ZoekAdres(string adres)
        {
            for (int i = 0; i < AANTAL; i++)
            {
                if (Gegevens[i].HeeftAdres(adres))
                {
                    return i;
                }
            }
            return -1;
        }

        public int ZoekWoonplaats(string woonplaats)
        {
            for (int i = 0; i < AANTAL; i++)
            {
                if (Gegevens[i].HeeftWoonplaats(woonplaats))
                {
                    return i;
                }
            }
            return -1;
        }

        public int ZoekWoonplaatsEnAdres(string woonplaats, string adres)
        {
            for (int i = 0; i < AANTAL; i++)
            {
                if (Gegevens[i].HeeftAdres(adres) && Gegevens[i].HeeftWoonplaats(woonplaats))
                {
                    return i;
                }
            }
            return -1;
        }
    }
```


## Opgave 3

![Opgave 3 Instance Diagram](http://i.imgur.com/qYMHLmR.jpg)

## Opgave 4
### Verwijder eerste instantie
```C#
public void Verwijder(string naam)
        {
            int index = ZoekNaam(naam);
            if(index != -1)
            {
                Verwijder(index);
            }
        }


        private void Verwijder(int index)
        {
            if (index <= AANTAL)
            {
                for (int i = index; i < AANTAL; i++)
                {
                    if (i == AANTAL)
                    {
                        Gegevens[i] = null;
                    }
                    else
                    {
                        Gegevens[i] = Gegevens[i + 1];
                    }
                }
            }
        }
```

### Verwijder laatste instantie
```C#
 public void Verwijder(string naam)
        {
            for (int i = AANTAL; i > 0; i--)
            {
                if (Gegevens[i].HeeftNaam(naam))
                {
                    Verwijder(i); //Zie methode verwijder eerste instantie
                    return;
                }
            }
        }
```

### Verwijder alle instantie
```C#
 public void Verwijder(string naam)
        {
            for (int i = AANTAL; i > 0; i--)
            {
                if (Gegevens[i].HeeftNaam(naam))
                {
                    Verwijder(i);
                }
            }
        }
```

### Verwijder de eerste instantie op basis van woonplaats en adres
```C#
public void Verwijder(string woonplaats, string adres)
        {
            int index = ZoekWoonplaatsEnAdres(woonplaats, adres);
            if(index != -1)
            {
                Verwijder(index);
            }
        }
```

### Verwijder alle instanties op basis van woonplaats en adres
```C#
 public void Verwijder(string woonplaats, string adres)
        {
            for (int i = AANTAL; i > 0; i--)
            {
                if (Gegevens[i].HeeftAdres(adres) && Gegevens[i].HeeftWoonplaats(woonplaats))
                {
                    Verwijder(i);
                }
            }
        }
```

