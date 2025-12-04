Hello Kitty Sudoku \- Boundary Testing  
—————————  
Logic Point A \- Selecting the Cell

A1:                                         Why is it a boundary?

| Selecting a 0 or 8 column/row index | It is in the valid boundary range but at the very ends. |
| :---- | :---- |
| Selecting a 9 or \-1 row/column index | It is slightly outside of the valid boundary range |
| Selecting an already filled coordinate. | It is outside the valid boundary range |

A2:                                              Test Data

| Selecting a 0 or 8 column/row index | Selecting the index on either edge of the valid index. |
| :---- | :---- |
| Selecting a 9 or \-1 row/column index | Code miscalculates and passes an incorrect index. |
| Selecting an already filled coordinate. | Player clicks on a box that is already filled in. |

A3:                                                Test Data                          Expected Outcome

| Selecting a 0 or 8 column/row index | Selecting the index on either edge of the valid index. | Works as expected, fills in the box on the valid coordinate. |
| :---- | :---- | :---- |
| Selecting a 9 or \-1 row/column index | Code miscalculates and passes an incorrect index. | Game catches that it is out of index and function ends. |
| Selecting an already filled coordinate. | Player clicks on a box that is already filled in. | Function checks if box is already filled and functions ends. |

Logic Point B \- Inputting the Number

B1:                                         Why is it a boundary?

| Entering number into already filled cell. | It is a valid index but invalid cell. |
| :---- | :---- |
| Selecting a 0 or \-1 row/column index | It is slightly outside of the valid number range |
| Selecting a number already selected in the same 3x3 grid | It is within a valid cell and valid number but it is already in the same 3x3 grid |

B2:                                              Test Data

| Entering number into already filled cell. | Player inputs a 2 into an already filled cell. |
| :---- | :---- |
| Selecting a 0 or \-1 row/column index | Player enters a 0 or a \-1 into an open cell |
| Selecting a number already selected in the same 3x3 grid | Player enters a number already in the cell’s 3x3 grid. |

B3:                                                Test Data                          Expected Outcome

| Entering number into already filled cell. | Player inputs a 2 into an already filled cell. | Function checks if cell is filled and ends  |
| :---- | :---- | :---- |
| Selecting a 0 or \-1 row/column index | Player enters a 0 or a \-1 into an open cell | Function reads the invalid number and doesn’t continue the function |
| Selecting a number already selected in the same 3x3 grid | Player enters a number already in the cell’s 3x3 grid. | The cell rejects the number |

Logic Point C \- Puzzle Completion

C1:                                         Why is it a boundary?

| Grid filled except one cell | It is an edge case where win shouldn't trigger |
| :---- | :---- |
| Grid filled with a mistake | Almost right and may trigger the complete function because all of them were filled. |
| All cells are completed correctly | Correct case to make sure it works properly. |

C2:                                              Test Data

| One empty cell | Board complete except (1,1) empty |
| :---- | :---- |
| Full grid with mistake | Last cell filled with 5, when 5 is already correct in another cell in the same 3x3 grid |
| Full completion | Player fills last cell with correct number |

C3:                                                      Test Data                          Expected Outcome

| One empty cell | Board complete except (1,1) empty | No win occurs, game waits for the last one to be filled in correctly. |
| :---- | :---- | :---- |
| Full grid with mistake | Last cell filled with 5, when 5 is already correct in another cell in the same 3x3 grid | No win, but show the incorrect choice. |
| Full completion | Player fills last cell with correct number | Win screen appears and user gets sent back to main menu. |

### **Reflection**

**Which logic point is the most fragile?**  
Grid input and cell selection, because any logic errors or bad input could cause an issue if not checked properly.

**What will I need to watch out for when coding this?**  
I need to make sure that I validate the coordinates indexes before using them in functions.

**Which boundary case surprised me  the most?**  
Null inputs or non-number inputs surprised me because they could occur if I dont validate inputs property.