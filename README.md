# Library Management System

A command-line library system in Python, made to learn object-oriented programming (OOP). Members can borrow and return books and leave short reviews, and everything is saved in a SQLite database.

**Status:** Finished
**Context:** Mandatory assignment in Programming, 2nd semester, IT-Technology at Zealand (EASJ), March 2026. Individual project.

The assignment was to write a library management system that uses classes, objects, inheritance and polymorphism. I chose to make it for private people: a family or a book club can register their own books and lend them to each other.

## Features

- Add, remove and update books
- Add, remove and update members
- Display all books and members
- Borrow and return books
- Write and store reviews (max. 200 characters)
- Search for books by title or author
- Everything saved in a SQLite database
- A numbered command-line menu (options 0–10)
- Safe delete, in case of misclicks

## How to run it

You only need Python. There are no extra packages.

```
python main.py
```

Use the numbers in the menu to navigate. The first time you run it, the program creates `library.db`. Delete that file to start over with an empty library.

## Object-oriented concepts

The program has four classes:

- **`Book`** – a book with title, author, number of copies, ID and user comments
- **`Member`** – a library user who can borrow and return books
- **`Library`** – manages the system: books, members, saving to and loading from the database
- **`Displayable`** – a simple parent class that requires its subclasses to implement `display()`

**Encapsulation:** `Book`, `Member` and `Library` use private attributes. It isn't strictly necessary in a program this size, but it keeps the structure clean and prevents accidents, like adding 20,000 books at once. A librarian subclass with extra privileges would be a natural next step.

**Inheritance and polymorphism:** `Book` and `Member` both inherit from `Displayable` and override `display()` in their own way. That lets the menu list books and members with the same call. I added `Displayable` late in the project, so it's only used in a small part of the menu, but it makes it easy to add new types later.

## Database (SQLite)

The database gives the program persistence, so the library is still there next time you run it. Without it, everything would live in Python lists and disappear when the program closes. It has tables for books, members and comments.

## Code structure

| File | Contents |
| --- | --- |
| `main.py` | The `Book`, `Member`, `Library` and `Displayable` classes, and the CLI menu |
| `unitest.py` | Unit tests for `main.py` |
| `library.db` | The database. Created automatically, so it isn't in the repository |

## Unit tests

```
python unitest.py
```

> ⚠️ **The test wipes the database.** There is no separate test database yet, so don't run it on a library you want to keep.

The tests cover:

1. **`Book`:** create, borrow, return, check availability
2. **`Member`:** borrow, return
3. **`Library`:** reset, add a book, add a member, borrow, return

## Extra features (not part of the assignment)

- **SQLite database:** a program meant to store lots of data made no sense without persistence.
- **Comments:** a library for a book club should let members review books.
- **Search:** it was easy to add.
- **CLI:** building a menu was essential for understanding how the whole program fits together.
- **Safe delete:** in case of misclicks.

## Ideas for further development

- A separate test database, so the tests don't wipe the real one
- Track each member's borrowing history and current loans
- More levels in the menu
- Log-in and security
- Wishlists for members
- Other things to borrow, like CDs and films
- An admin subclass of `Member` for a book club leader or librarian

## Credits

Created by Lea Mette Jacobsen, with help from and thanks to our teacher Zuhair Haroon Khan.

Sources:

- [Building a Library Management System with OOP in Python (Medium)](https://medium.com/@sabaumar07/building-a-library-management-system-with-object-oriented-programming-oop-in-python-45df56704456)
- [Library Management System using Python (GeeksforGeeks)](https://www.geeksforgeeks.org/python/library-management-system-using-python/)
- [YouTube tutorial](https://www.youtube.com/watch?v=Bmxt1c09I30)
- Microsoft Copilot
