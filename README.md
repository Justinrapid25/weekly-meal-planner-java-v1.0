# Weekly Meal Planner

A command-line Java application that generates a personalized seven-day dinner plan based on user-selected cuisine categories and a custom food-allergy profile. The program filters its recipe database to exclude any recipe containing a flagged allergen, matches the remaining recipes to the user's chosen cuisines, and assembles a randomized weekly plan. Users can view full recipe details for any day and swap out individual days without regenerating the entire week.

Built as an object-oriented application across eight classes, with business logic fully separated from the user interface to support a future graphical interface.

---

## Features

- **Cuisine category selection** across nine categories (American, Italian, Mexican, Asian, Mediterranean, BBQ, Soul Food, Middle Eastern, Seafood)
- **Allergy profile management** supporting sixteen allergens
- **Allergy-aware filtering** that excludes any recipe containing a flagged allergen before suggestions are made
- **Randomized weekly plan generation** producing a unique seven-day plan
- **Full recipe display** including ingredients and step-by-step instructions
- **Single-day replacement** to swap one day's meal without regenerating the whole week
- **Full week regeneration** on demand
- **Case-insensitive input** for both categories and allergens
- **Graceful error handling** for invalid input and empty results

---

## How It Works

The user selects one or more cuisine categories and optionally builds an allergy profile. When generating a plan, the program:

1. Retrieves all recipes from the database
2. Filters out any recipe containing a flagged allergen
3. Keeps only recipes matching the selected categories
4. Shuffles the results and selects up to seven unique meals
5. Displays the weekly plan

From there the user can view the full recipe for any day, replace an individual day, or regenerate the entire week.

---

## Architecture

The application is divided into eight classes, each with a single responsibility. Only the entry-point class interacts with the user; every other class is pure logic and data, which keeps the core independent of the interface.

| Class | Responsibility |
|-------|----------------|
| `Ingredient` | Represents an ingredient and the allergens it contains |
| `Recipe` | Holds a recipe's name, category, ingredients, instructions, and servings |
| `RecipeDatabase` | Stores all recipes; filters by category and by allergy safety |
| `AllergyProfile` | Stores the user's allergens and checks whether a recipe is safe |
| `UserPreferences` | Stores the user's selected cuisine categories |
| `MealPlanner` | Core logic: generates the weekly plan and replaces individual days |
| `WeeklyMealPlan` | Stores the seven selected recipes and handles display |
| `MainMealPlanner` | Entry point; runs the CLI menu and coordinates all other classes |

---

## Concepts Demonstrated

- Object-oriented design with encapsulation and single-responsibility classes
- Collections (`List`, `Set`) and generics
- Static data management
- Nested loops and boolean logic for the allergy-safety check
- Separation of business logic from the user interface
- Defensive programming with guard clauses and input validation

---

## Getting Started

### Prerequisites
- Java Development Kit (JDK) 17 or higher

### Compile
Compile the files in dependency order:

```bash
javac Ingredient.java Recipe.java AllergyProfile.java UserPreferences.java RecipeDatabase.java WeeklyMealPlan.java MealPlanner.java MainMealPlanner.java
```

### Run
```bash
java MainMealPlanner
```

### Example Session
```
1. Select cuisine categories (e.g. American, Asian)
2. Set an allergy profile (e.g. onions)
3. Generate the weekly meal plan
4. View the full recipe for any day
5. Replace a single day
6. Exit
```

---

## Roadmap

Planned enhancements, supported by the existing architecture:

- Graphical user interface (JavaFX or Swing)
- Loading the recipe database from an external JSON or text file
- User-added ingredients and recipes at runtime
- Saving and loading meal plans and profiles to a file
- A shopping-list generator compiled from the weekly plan

---

## About

Built as a learning project for a Program Development in Java course, designed from a written specification through to a fully working application. The allergy-aware filtering logic reflects a background in cybersecurity, where safety-first design and careful input handling are second nature.

**Author:** Justin Coover
