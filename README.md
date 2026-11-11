# Hiking

![L'escalette](https://upload.wikimedia.org/wikipedia/commons/thumb/0/07/Pyrenees_escalette.JPG/320px-Pyrenees_escalette.JPG)

# What to Do

You have to solve [Day 10 of the Advent of Code 2024 **Part 1**](https://adventofcode.com/2024/day/10).

The problem is protected by Copyright, in consequence we cannot copy it here and you have to read the linked website and understand the problem. You **don't need** to connect to Advent of Code to read **Part 1** of the problem.

In a file called `hiking.py`, write a Python program that reads the topographic map (the puzzle input) from a file whose name is given on the command line, then prints the answer of **Part 1**: the sum of the scores of all the trailheads of the map.

```bash
$ python hiking.py small_map.txt
3
```

Your program should print only this number, nothing else.

There must be exactly one command-line argument (the file name).
If not, the program should print `Usage: python hiking.py filename` and stop.

```bash
$ python hiking.py
Usage: python hiking.py filename
$ python hiking.py small_map.txt large_map.txt
Usage: python hiking.py filename
```

The map files of this exercise contain only digits (`0` to `9`), one row of the map per line, and all the lines have the same length.
Some small examples of the puzzle page contain `.` for impassable tiles: you don't need to handle them.

> [!TIP]
> The command-line arguments are stored in the list `sys.argv` (after `import sys`).
> `sys.argv[0]` is the name of the script, so for `python hiking.py small_map.txt`, `sys.argv` is `['hiking.py', 'small_map.txt']`.
> `sys.exit()` stops the program.

> [!TIP]
> The method `read()` returns the whole content of a file as one `str`, and the method `splitlines()` cuts it into a list of lines (without the `'\n'`):
> ```python
> with open(filename) as map_file:
>     rows = map_file.read().splitlines()
> ```
> Then `rows[row][col]` is the character at row `row` and column `col` (both numbered from `0`).
> Be careful, it is a `str` (`'7'`), not an `int` (`7`).

> [!WARNING]
> In Python, a negative index is **not** an error: `rows[-1]` is the **last** row of the map.
> So before looking at a neighbour, check that its row and its column are inside the map (between `0` and the number of rows or columns, excluded).

> [!TIP]
> The score of a trailhead counts **different** 9s: a `set` of positions (`(row, col)` tuples) avoids counting the same 9 twice.

# How to Test

Two map files are given for testing:

```bash
$ python hiking.py small_map.txt
3
$ python hiking.py large_map.txt
64
```

Then test your program from the exercise folder with:

```bash
python test_hiking.py
```

(use `python3` instead of `python` if that is how you run Python on your computer).

The script runs your program as a user would: it writes a map in a file, gives the name of this file to your program on the command line, then checks what your program prints.
When a test fails, it explains what is wrong and gives the trailheads that can reach a 9 with their scores, so that you can compare them with yours.
After all the tests, it tries to find the probable cause of the wrong results.

Don't forget it's important to test your program yourself too.
Copy the examples of the puzzle page (those with digits only) in files and check the answers of your program.
What happens if:
* a 0 is on the edge of the map (first or last row, first or last column)?
* the same 9 can be reached by two different hiking trails?
* the map has only one row? only one column?
* there is no newline at the end of the file?
* you forget the file name on the command line?

# How to Submit

Once you're done with all tasks, submit all your python files for the week on Moodle.

# Licence

Advent of Code is a registered trademark in the United States. The design elements, language, styles, and concept of Advent of Code are all the sole property of Advent of Code and may not be replicated or used by any other person or entity without express written consent of Advent of Code. Copyright 2015-2024 Advent of Code. All rights reserved.

You may link to or reference puzzles from Advent of Code in discussions, classes, source code, printed material, etc., even in commercial contexts. Advent of Code does not claim ownership or copyright over your solution implementation.
