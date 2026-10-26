# Static Verification Review Checklist

| Category | Item / Question | Status (Pass/Fail) | Notes / Findings |
| :--- | :--- | :---: | :--- |
| **Initialization** | Are variables properly initialized before use? | **FAIL** | Uninitialized `double sum` in `averageAttack()`. |
| **Initialization** | Are dynamic arrays/pointers zeroed or initialized on creation? | **FAIL** | Dynamic array allocated with `new char[10]` without initialization or boundary checks. |
| **Pointers** | Are pointers checked for `nullptr` prior to dereferencing? | **FAIL** | Multiple nullptr dereferences in `attackMonster`, `getMonsterLabel`, `defeatMonster` when searching for non-existent IDs. |
| **Pointers** | Are deleted pointers zeroed or prevented from dangling/use-after-free? | **FAIL** | Use-after-free in `defeatMonster()` (`m->name` accessed after `delete m`). Incorrect `delete` on array allocated pointer `delete name`. |
| **Pointers** | Are dynamic memory allocations matched with correct delete types? | **FAIL** | `delete name;` used instead of `delete[] name;`. Memory leak on `Monster* bonus` in `main()`. |
| **Arrays** | Are array boundary bounds checked during access/insertion? | **FAIL** | Buffer overflow in `spawnMonster()` when `monsterCount >= MAX_MONSTERS` (spawning 6th monster `Bat`). Buffer overflow in `readBoss()` (`cin >> name` into size 10). |
| **Loops** | Are loop boundary conditions strictly correct? | **FAIL** | Off-by-one error in `totalMonsterHealth()` using `<=` instead of `<`. |
| **Arithmetic** | Are calculations free of integer truncation/precision issues? | **FAIL** | In `calculateDamage()`, `attack * armorPercent / 100` performs integer division prior to conversion. |
| **Arithmetic** | Are signed/unsigned comparisons and underflows prevented? | **FAIL** | Underflow bug in `m->health - dmg < 0` due to implicit unsigned conversion. |
| **Control Flow** | Are equality comparisons (`==`) correctly formatted? | **FAIL** | Assignment operator used inside conditional `if (monsters[i]->id = id)` in `findMonster()`. |
| **Control Flow** | Do all execution paths return a value in non-void functions? | **FAIL** | Missing return statement in `playerRank(int score)` when `score <= 100`. |
| **Function Calls** | Are local auto/stack variables safely returned? | **FAIL** | Returning reference to local temporary string in `getMonsterLabel()`. |
| **Classes** | Are Copy Constructors / Assignment Operators implemented for classes managing heap memory? | **FAIL** | Shallow copy occurring in `Game copy = game;` causing double-free on destructor. |
