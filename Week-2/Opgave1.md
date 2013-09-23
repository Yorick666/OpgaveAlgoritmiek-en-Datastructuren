# Week 2
## Week 2.1.1

Schrijf een selection sort algoritme dat eerst de grootste waarde op de 
goede positie zet.
```C#
class Program
    {
        private static int[] arr = new int[] { 7, 3, 8, 1, 2, 5, 4, 9, 6, 0 };

        static void Main(string[] args)
        {
            for (int i = 0; i < arr.Length; i++)
            {
                Console.WriteLine(arr[i]);
            }

            //BubbleSort(arr);
            Console.WriteLine();
            ReverseBubbleSort(arr);
            for (int i = 0; i < arr.Length; i++)
            {
                Console.WriteLine(arr[i]);
            }
            Console.ReadLine();
        }

        private static void swap(int[] source, int index, int p)
        {
            int tmp = source[index];
            source[index] = source[p];
            source[p] = tmp;
        }

        private static void BubbleSort(int[] input)
        {
            for (int outer = input.Length - 1; outer > 0; outer--)
            {
                for (int inner = 0; inner < outer; inner++)
                {
                    if (input[inner] > input[inner + 1])
                    {
                        swap(input, inner, inner + 1);
                    }
                }
            }
        }

        private static void ReverseBubbleSort(int[] input)
        {
            for (int outer = 0; outer < input.Length; outer++)
            {
                for (int inter = 1; inter < input.Length-outer; inter++)
                {
                    if (input[inter -1] > input[inter])
                    {
                        swap(input, inter -1, inter);
                    }
                }
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
