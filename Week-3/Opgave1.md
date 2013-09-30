# Week 3
## Week 3.1.1
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
![Instance diagram](http://i.imgur.com/bQyrSh5.jpg)

![Instance diagram](http://i.imgur.com/ZNKpYVC.jpg)

## Week 3.1.3
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
