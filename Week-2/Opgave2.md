# Week 2
## Week 2.1.1

Schrijf een selection sort algoritme dat eerst de grootste waarde op de 
goede positie zet.
```C#
class Program
    {
        static int AANTAL = 10;
        static int [] data =  new int [10] {100, 50, 20, 40, 10, 60, 80, 70, 90, 30};

        static void Main(string[] args)
        {
            for (int i = 0; i < AANTAL; i++)
            {
                Console.WriteLine("array[" + i + "] = " + data[i]);
            }

            ReverseSelectionSort(data);
            Console.WriteLine("");
            for (int i = 0; i < AANTAL; i++)
            {
                Console.WriteLine("array[" + i + "] = " + data[i]);
            }
            Console.Read();
        }

        public static void ReverseSelectionSort(int[] array)
        {
            int i, j;
            int max, temp;

            for (i = AANTAL-1; i > 0; i--)
            {
                max = i;
                for(j = i; j >=0; j--)
                {
                    if (array[j] > array[max])
                    {
                        max = j;
                    }
                }

                //Swap
                temp = array[i];
                array[i] = array[max];
                array[max] = temp;
            }
        }
    }
```

Het algortitme is O(N^2) aangezien elke for loop met een grotere input ook groter wordt.
De loops zijn genest dus de vergroting wordt dan exponentieel.

# Week 2.1.2
```C#
private static void NAWBubbelSort(NAW[] input)
        {
            for (int outer = input.Length - 1; outer > 0; outer--)
            {
                for (int inner = 0; inner < outer; inner++)
                {
                    if (input[inner].CompareTo(input[inner + 1]) != -1)
                    {
                        swap(input, inner, inner + 1);
                    }
                }
            }
        }
```
Ja de plaatsen zijn na het uitvoeren binnen de naam gesorteerd.
Het algoritme is dus stabiel.
