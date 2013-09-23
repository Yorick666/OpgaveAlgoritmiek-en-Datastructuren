# Week 3
## Week 3.2.1
Geef in de big–O Notatie aan van welke orde dit algoritme is. Verklaar 
je antwoord.
* Ook dit algoritme is O(N^2). Beide loops groeien qwa tijd liniear met de input grootte.
De loops zijn genest wat de N^2 veroorzaakt.

Vul een gekoppelde lijst met respectievelijk 100, 1000, 10.000 en 
100.000 random – waarden. Onderzoek de sorteersnelheid. Komt 
deze overeen met de orde van het algoritme? Verklaar je antwoord.
* Ja het lijkt erop als of de tijd die het duurt exponentieel grooter wordt met de input grootte.

Vergelijk je antwoord met vraag 4 van vorige week.
* Er is geen vraag 4 in week 2.


## Week 3.2.2
Maak een gekoppelde lijst die handelingen als integers opslaat. De 
gekoppelde lijst dient de methodes _undo_, _redo_ en _insert_ te bezitten.

* De klasse krijgt een extra Property genaamt current. Deze is standaard gelijk aan Last.
* De klasse LinkedList zoals in de bijlage dient de volgende methodes te krijgen.

```C#
public void undo()
        {
            Current = Current.Previous;
        }

        public void redo()
        {
            Current = Current.Next;
        }

        public void insert(T item)
        {
            Current.Item = item;
        }
```

* De methode _GetLastLink() wordt ook aangepast.
```C#
private void AddLastLink(Link<T> e)
        {
            if (Size == 0)
                First = Last = Current = e;
            else
            {
                e.Previous = Last;
                Last.Next = e;
                Last = e;
                Current = Last;
            }
            Size++;
        }```

### Bijlage
__LinkedList.cs__
```C#
public class LinkedList<T>
    {
        public Link<T> First { get; set; }
        public Link<T> Last { get; set; }
        public int Size { get; private set; }

        public Link<T> getEntry(int n)
        {
            Link<T> e;
            if (n < Size / 2)
            {
                e = First;
                // n less than size/2, iterate from start
                while (n-- > 0)
                    e = e.Next;
            }
            else
            {
                e = Last;
                // n greater than size/2, iterate from end
                while (++n < Size)
                    e = e.Previous;
            }
            return e;
        }

        void RemoveLink(Link<T> e)
        {
            Size--;
            if (Size == 0)
                First = Last = null;
            else
            {
                if (e == First)
                {
                    First = e.Next;
                    e.Next.Previous = null;
                }
                else if (e == Last)
                {
                    Last = e.Previous;
                    e.Previous.Next = null;
                }
                else
                {
                    e.Next.Previous = e.Previous;
                    e.Previous.Next = e.Next;
                }
            }
        }

        private bool WithinBounds(int index)
        {
            return !(index < 0 || index >= Size);
        }

        public T GetFirst()
        {
            if (Size == 0)
                return default(T);

            return First.Item;
        }

        public T GetLast()
        {
            if (Size == 0)
                return default(T);

            return Last.Item;
        }

        public void AddFirst(T o)
        {
            Link<T> e = new Link<T>(o);

            if (Size == 0)
                First = Last = e;
            else
            {
                e.Next = First;
                First.Previous = e;
                First = e;
            }
            Size++;
        }

        public void AddLast(T o)
        {
            AddLastLink(new Link<T>(o));
        }

        private void AddLastLink(Link<T> e)
        {
            if (Size == 0)
                First = Last = e;
            else
            {
                e.Previous = Last;
                Last.Next = e;
                Last = e;
            }
            Size++;
        }

        public bool Remove(Object o)
        {
            Link<T> e = First;
            while (e != null)
            {
                if (o.Equals(e.Item))
                {
                    RemoveLink(e);
                    return true;
                }
                e = e.Next;
            }
            return false;
        }

        public T GetAt(int index)
        {
            if (!WithinBounds(index))
            {
                return default(T);
            }
            return getEntry(index).Item;
        }

        public T SetAt(int index, T o)
        {
            if (!WithinBounds(index))
            {
                return default(T);
            }
            Link<T> e = getEntry(index);
            T old = e.Item;
            e.Item = o;
            return old;
        }

        public T Remove(int index)
        {
            if (!WithinBounds(index))
            {
                return default(T);
            }
            Link<T> e = getEntry(index);
            RemoveLink(e);
            return e.Item;
        }

    }
```

__Link.cs__
```C#
public class Link<E>
    {
        public E Item { get; set; }
        public Link<E> Previous { get; set; }
        public Link<E> Next { get; set; }


        public Link(E item)
        {
            Item = item;
        }

        public void SwapRight()
        {
            E item = Item;
            Item = Next.Item;
            Next.Item = item;
        }
    }
```
