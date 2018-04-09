# GENERICS

JUST ADDED THIS TO TOP FOR NEW COMMIT


Derek Banas Youtube video of generics in C3
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace GENERICS
{
    class Program
    {
        static void Main(string[] args)
        {
            List<Animal> animalList = new List<Animal>(); //parenthesis calls constructor

            animalList.Add(new Animal() { Name1 = "Doug" });
            animalList.Add(new Animal() { Name1 = "Paul" });
            animalList.Add(new Animal() { Name1 = "Sally" });

            animalList.Insert(1, new Animal() { Name1 = "Steve" }); //adds 'Steve' animal to list at index 1 (everything else moves right)
           // animalList.RemoveAt(1); //removes animal in list at index 1

            Console.WriteLine("number of animals: {0}", animalList.Count()); //counts number of items (animals) in list
           
            foreach(Animal a in animalList) //writes name of each item in list
            {
                Console.WriteLine(a.Name1);
            }

            //Stack<T>, Queue<T>, Dictionary<T>  LOOK AT THESE ALSO

            int x = 5, y = 4;
            Animal.GetSum(ref x, ref y);
            string k = "5", s = "4";
            Animal.GetSum(ref k, ref s);

            Rectangle<int> rec1 = new Rectangle<int>(20, 50); //Rectangle built with int
            Console.WriteLine(rec1.GetArea());
            Rectangle<string> rec2 = new Rectangle<string>("20", "50"); //Rectangle built with string
            Console.WriteLine(rec2.GetArea());

            Arithmetic add, sub, addSub;
            add = new Arithmetic(Add);
            sub = new Arithmetic(Subtract);
            addSub = add + sub;
            sub = addSub - add;
            Console.WriteLine($"Add 6 & 10");
            add(6, 10);
            Console.WriteLine($"Add & Subtract 10 & 4");
            addSub(10, 4);

            Hello keith, james;
            keith = new Hello(Greet);
            //james = new Hello(Greet); 
            Console.WriteLine($"keith meets james...");
            keith("James","Keith");

            Console.ReadLine();
        }

        public struct Rectangle<T>
        {
            private T width;
            private T length;

            public T Width
            {
                get { return width; }
                set { width = value; }
            }
            public T Length
            {
                get { return length; }
                set { length = value; }
            }
            public Rectangle(T w, T l)
            {
                width = w;
                length = l;
            }
            public string GetArea()
            {
                double dblWidth = Convert.ToDouble(Width);
                double dlbLength = Convert.ToDouble(Length);
                return string.Format($"{Width} * {Length} = {dblWidth * dlbLength}");
            }
        }

        public delegate void Arithmetic(double num1, double num2); //public delegate that doesn't return a value and receives 2 doubles                                                                   
        public static void Add(double num1, double num2)
        {
            Console.WriteLine($"{num1} + {num2} = {num1 + num2}");

        }
        public static void Subtract(double num1, double num2)
        {
            Console.WriteLine($"{num1} - {num2} = {num1 - num2}");

        }

        public delegate void Hello(string hello, string name);
        public static void Greet(string hello, string name)
        {
            Console.WriteLine($"{hello}! Welcome to the game. My name is {name}");
        }



    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace GENERICS
{
    class Animal
    {
        private string Name;

        public string Name1 { get => Name; set => Name = value; }

        public Animal(string name = "no name")
        {
            Name1 = name;
        }

        public static void GetSum<T>(ref T num1, ref T num2)
        {
            double dblX = Convert.ToDouble(num1);
            double dblY = Convert.ToDouble(num2);
            Console.WriteLine($"{dblX} + {dblY} = {dblX + dblY}");
        }



    }
}
