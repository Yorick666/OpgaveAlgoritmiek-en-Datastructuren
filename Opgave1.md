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
