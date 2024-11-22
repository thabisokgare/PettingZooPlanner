# PettingZooPlanner
Certainly! Here's a README for your Zoo School Visit Planner project that demonstrates the fundamentals of methods in C#:

---

# Zoo School Visit Planner

**Zoo School Visit Planner** is a console application written in C# designed to plan and organize school visits to a petting zoo. It uses fundamental programming concepts, focusing on methods to perform specific tasks, maintain modularity, and improve readability and maintainability.

## Features

- **Randomize Animals**: Shuffle the list of animals to ensure a unique experience for each visit.
- **Assign Animals to Groups**: Divide the list of animals into groups for the school visit.
- **Display Groups**: Print out the assigned groups of animals for each school.

## Prerequisites

- [.NET SDK](https://dotnet.microsoft.com/download) installed on your machine.

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/zooschoolvisitplanner.git
   cd zooschoolvisitplanner
   ```

2. **Build the Project**:
   ```bash
   dotnet build
   ```

3. **Run the Project**:
   ```bash
   dotnet run
   ```

## Project Structure

```
ZooSchoolVisitPlanner/
│
├── Program.cs         # Entry point of the application
└── README.md          # Project documentation
```

## Usage

### Main Menu

When you run the application, it automatically plans visits for three schools with different group configurations.

### Methods Overview

- **PlanSchoolVisit**: Plans the visit for a school, randomizing animals and assigning them to groups.
- **RandomizeAnimals**: Shuffles the list of animals.
- **AssignGroup**: Divides the shuffled list of animals into specified groups.
- **PrintGroup**: Prints the groups of animals to the console.

## Example Output

Running the application will produce output similar to the following:

```
School A
Group 1: alpacas  chickens  emus  
Group 2: capybaras  ducks  geese  
Group 3: goats  iguanas  kangaroos  
Group 4: lemurs  llamas  macaws  
Group 5: ostriches  pigs  ponies  
Group 6: rabbits  sheep  tortoises  

School B
Group 1: macaws  ducks  iguanas  capybaras  ponies  geese  
Group 2: tortoises  pigs  kangaroos  llamas  sheep  rabbits  
Group 3: goats  lemurs  ostriches  alpacas  chickens  emus  

School C
Group 1: chickens  emus  llamas  macaws  alpacas  ponies  ducks  kangaroos  pigs  
Group 2: goats  iguanas  lemurs  ostriches  capybaras  geese  rabbits  sheep  tortoises  
```

## Code Explanation

### Main Class (`Program.cs`)

Here’s a brief overview of the methods used in the application:

- **Main Method**:
  - Initializes the list of animals.
  - Calls `PlanSchoolVisit` for three different schools.

```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        string[] pettingZoo = 
        {
            "alpacas", "capybaras", "chickens", "ducks", "emus", "geese", 
            "goats", "iguanas", "kangaroos", "lemurs", "llamas", "macaws", 
            "ostriches", "pigs", "ponies", "rabbits", "sheep", "tortoises",
        };

        PlanSchoolVisit("School A");
        PlanSchoolVisit("School B", 3);
        PlanSchoolVisit("School C", 2);

        void PlanSchoolVisit(string schoolName, int groups = 6) 
        {
            RandomizeAnimals(); 
            string[,] group1 = AssignGroup(groups);
            Console.WriteLine(schoolName);
            PrintGroup(group1);
        }

        void RandomizeAnimals() 
        {
            Random random = new Random();

            for (int i = 0; i < pettingZoo.Length; i++) 
            {
                int r = random.Next(i, pettingZoo.Length);

                string temp = pettingZoo[r];
                pettingZoo[r] = pettingZoo[i];
                pettingZoo[i] = temp;
            }
        }

        string[,] AssignGroup(int groups = 6) 
        {
            string[,] result = new string[groups, pettingZoo.Length / groups];
            int start = 0;

            for (int i = 0; i < groups; i++) 
            {
                for (int j = 0; j < result.GetLength(1); j++) 
                {
                    result[i, j] = pettingZoo[start++];
                }
            }

            return result;
        }

        void PrintGroup(string[,] groups) 
        {
            for (int i = 0; i < groups.GetLength(0); i++) 
            {
                Console.Write($"Group {i + 1}: ");
                for (int j = 0; j < groups.GetLength(1); j++) 
                {
                    Console.Write($"{groups[i, j]}  ");
                }
                Console.WriteLine();
            }
        }
    }
}
```

### Explanation of Methods:

1. **`PlanSchoolVisit` Method**:
   - Shuffles the list of animals.
   - Assigns animals to groups.
   - Prints the assigned groups.

2. **`RandomizeAnimals` Method**:
   - Shuffles the `pettingZoo` array using the Fisher-Yates algorithm.

3. **`AssignGroup` Method**:
   - Splits the `pettingZoo` array into a specified number of groups.

4. **`PrintGroup` Method**:
   - Prints each group of animals.

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

This README provides a clear overview of your Zoo School Visit Planner project, including its purpose, features, usage, and a detailed explanation of the methods used. Let me know if you need any further adjustments or additional details! 😊

Enjoy organizing your zoo visits! 🦙🐐🦘
