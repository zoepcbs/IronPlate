# IronPlate
A free, intuitive all-in-one wellness app — meal prep planning, calorie &amp; macro tracking, health calculators, and workout planning. No paywall, no AI, no overwhelm.

---

# 🎯 Project Overview


## ✨ Full Feature List

```
👤 Auth & Onboarding
├── Register / Login (JWT)
├── Profile: age, sex, height, weight, activity level, goal
└── Auto-calculate TDEE, macros, water intake on setup

🍽️ Meal Logging
├── Log by meal type (breakfast, lunch, dinner, snack)
├── USDA food search (300k+ foods)
├── Manual food entry
└── Edit / delete entries

📅 Weekly Meal Planner
├── 7-day calendar grid
├── Drag and drop meals into slots
├── Copy day to another day
└── Daily macro/calorie totals per day

💪 Workout Planner
├── Exercise library (500+ exercises)
├── Build custom workout plans
├── Log sets, reps, weight, duration
├── Weekly workout calendar
├── PR detection
├── Workout templates
└── Streak tracker

🛒 Grocery List
├── Auto-generate from meal plan
├── Group by category
├── Manual add items
└── Check off as you shop

📊 Dashboard
├── Daily calorie ring
├── Macro progress bars
├── Today's meals at a glance
├── Today's workout at a glance
├── Water intake tracker
└── Streak counter

📈 Progress & Insights
├── Weekly calorie averages
├── Macro trends over time
├── Weight lifted over time per exercise
├── Bodyweight log
└── Monthly comparison charts

🧮 Health Calculators
├── BMI
├── TDEE
├── Macro Split
├── Target Heart Rate
├── Ideal Body Weight
├── Body Fat % (Navy Method)
├── Water Intake
└── Protein Needs

💾 Saved Meals & Recipes
├── Save favorite meals
├── Build recipes from ingredients
└── Mark as meal prep friendly
```

---

## 🛠️ Full MERN Tech Stack

```
MongoDB         → All user data, meals, workouts, logs, plans
Express.js      → REST API
React           → All frontend views
Node.js         → Server + business logic

+ Libraries:
├── JWT + bcrypt          → Auth
├── Recharts              → Charts, calorie ring, macro bars
├── React DnD             → Drag and drop planner
├── Tailwind CSS          → Styling
├── Framer Motion         → Animations & transitions
├── Day.js                → Date handling
├── React Hook Form       → All forms
├── USDA FoodData API     → Free food database
└── wger / ExerciseDB     → Free exercise library
```

---

## 🗄️ Full Database Schema

```js
// User
{
  _id, name, email, passwordHash,
  age, sex, height, weight, activityLevel, goal,
  dailyCalorieTarget,
  macroTargets: { protein, carbs, fats },
  waterTarget, createdAt
}

// FoodEntry
{
  _id, userId, date,
  mealType: "breakfast"|"lunch"|"dinner"|"snack",
  foodName, calories,
  macros: { protein, carbs, fats },
  servingSize, servingUnit
}

// MealPlan
{
  _id, userId, weekStartDate,
  days: [{
    date,
    meals: {
      breakfast: [foodEntryId],
      lunch: [foodEntryId],
      dinner: [foodEntryId],
      snack: [foodEntryId]
    }
  }]
}

// Exercise
{
  _id, name, muscleGroup, equipment,
  difficulty, instructions, gifUrl,
  isCustom, userId (if custom)
}

// WorkoutPlan
{
  _id, userId, name,
  days: [{
    dayLabel: "Monday" | "Rest" | etc,
    workoutId
  }]
}

// Workout
{
  _id, userId, name,
  exercises: [{
    exerciseId, sets, reps,
    weight, duration, restTime, notes
  }],
  isTemplate
}

// WorkoutLog
{
  _id, userId, workoutId, date,
  exercises: [{
    exerciseId,
    sets: [{ reps, weight, completed }]
  }],
  duration, notes, completed
}

// PersonalRecord
{
  _id, userId, exerciseId,
  maxWeight, maxReps, date
}

// SavedMeal
{
  _id, userId, name,
  ingredients: [{ foodName, calories, macros, servingSize }],
  totalCalories, totalMacros, mealPrepFriendly
}

// GroceryList
{
  _id, userId, weekStartDate,
  items: [{ name, category, checked }]
}

// BodyweightLog
{
  _id, userId, weight, date, notes
}
```

---

## 🔌 Full API Routes

```
Auth
POST   /api/auth/register
POST   /api/auth/login

User
GET    /api/user/profile
PUT    /api/user/profile
GET    /api/user/stats

Food Log
GET    /api/log?date=
POST   /api/log
PUT    /api/log/:id
DELETE /api/log/:id

Meal Plan
GET    /api/plan?week=
POST   /api/plan

Saved Meals
GET    /api/meals
POST   /api/meals
DELETE /api/meals/:id

Grocery List
GET    /api/grocery?week=
POST   /api/grocery/generate
PUT    /api/grocery/:id

Exercises
GET    /api/exercises             → browse library
GET    /api/exercises/:id
POST   /api/exercises             → add custom

Workouts
GET    /api/workouts              → all user workouts
POST   /api/workouts              → create workout
PUT    /api/workouts/:id
DELETE /api/workouts/:id

Workout Plans
GET    /api/workoutplan
POST   /api/workoutplan
PUT    /api/workoutplan

Workout Logs
GET    /api/workoutlog?date=
POST   /api/workoutlog
PUT    /api/workoutlog/:id

Personal Records
GET    /api/prs
GET    /api/prs/:exerciseId

Bodyweight
GET    /api/bodyweight
POST   /api/bodyweight
```

---

## 📱 All Pages & Views

```
/login & /register       → Auth + onboarding
/dashboard               → Daily overview (meals + workout + water + streaks)
/log                     → Today's food log
/planner                 → Weekly meal calendar
/workout                 → Workout planner & library
/workout/log             → Active workout logging screen
/workout/history         → Past workouts + PRs
/grocery                 → Grocery list
/meals                   → Saved meals & recipes
/calculators             → All 8 health calculators
/progress                → Charts: weight, calories, lifts over time
/settings                → Profile, goals, preferences
```

---

## 🗓️ General Sprint Timeline

| Week | Focus |
|---|---|
| 1 | Setup, auth, onboarding, MongoDB models |
| 2 | Food log CRUD + USDA API |
| 3 | Meal planner (weekly calendar + drag and drop) |
| 4 | Exercise library + workout builder |
| 5 | Workout logging, PRs, streak tracker |
| 6 | Dashboard (calorie ring, macros, today's workout) |
| 7 | Grocery list gen, saved meals, calculators |
| 8 | Progress charts, bodyweight log |
| 9 | UI polish, mobile responsiveness, animations |
| 10 | Testing, bug fixes, deployment (Render + MongoDB Atlas) |

---

## 🏅 What Makes This Stand Out

- **Truly free** — every feature, forever
- **All-in-one** — meal + workout + calculators in one clean app
- **No AI required** — formula-based calculators, real exercise data
- **Simple by design** — max 3 clicks to log a meal or start a workout
- **Grocery list gen** — underrated feature users will love
- **PR detection** — small touch that feels premium
- **Deployable** — Render + MongoDB Atlas = free hosting for demo day
