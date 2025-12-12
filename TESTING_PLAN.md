Testing Plan — Hello Kitty Sudoku

1\. Overview  
This document outlines the testing strategy for Hello Kitty Sudoku. It consists of User Stories, their acceptance criteria, and the boundary and edge cast testing. It describes the functional test cases, boundary tests, expended behaviour, and opportunities for automation. The goal is to make sure that every major feature works reliably under all circumstances.

\---

2\. User Stories and Acceptance Criteria

User Story 1:    
As a new sudoku player, I want to have a tutorial, so I can learn how to play the game.  
\- Acceptance Criterion 1   
    \- Requirement(s):   
A tutorial must be accessible from the main menu through an easily accessible button.  
    \- Purpose:   
To ensure new players can locate and activate the tutorial, so they can learn the game.  
    \- Test Case:  
        a) Feature: Tutorial Activation  
        b) Test: User selects the “Tutorial” button from the main menu.  
        c) Expected Result / Behavior: Tutorial screen loads successfully.  
        d) Automation Candidate:  Yes, it is just ui navigation so it should be automated.

\- Acceptance Criterion 2   
    \- Requirement(s):   
The Tutorial must include basic sudoku rules and how to play  
    \- Purpose:   
Verification that the tutorial explains the gameplay correctly.  
    \- Test Case:  
        a) Feature: Tutorial content  
        b) Test: User views the tutorial, then examples and explanations appear.  
        c) Expected Result / Behavior: Text and visual examples are visible, clear, and   concise.  
        d) Automation Candidate: No, this feature requires visual verification, so it is not suitable for automation. 

User Story 2:  
  As a casual player, I want to choose a harder difficulty so that I can have a more difficult challenge.  
\- Acceptance Criterion 1   
    \- Requirement(s): User must be able to select Normal or Hard mode.  
    \- Purpose: Ensure difficulty selection works as intended  
    \- Test Case:  
        a) Feature: Difficulty selection  
        b) Test: Player presses “Normal” or “Hard” on the difficulty screen.  
        c) Expected Result / Behavior: Game starts with chosen difficulty  
        d) Automation Candidate: Yes, it is a rule-based UI button.

\- Acceptance Criterion 2   
    \- Requirement(s): Hard mode contains less pre-filled cells than Normal mode.  
    \- Purpose:  Validate that difficulty settings change puzzle generation.  
    \- Setup:  Generate the puzzle based on the mode you picked.  
    \- Test Case:  
        a) Feature: Puzzle generation based on difficulty  
        b) Test: Compare count of pre-filled cells in normal vs hard mode.  
        c) Expected Result / Behavior: Hard Mode has less numbers filled in initially.  
        d) Automation Candidate: Yes, it is repeated every time the game runs.

User Story 3:  
As a competitive player, I want to see my completion time, so I can try and beat my previous times.    
\- Acceptance Criterion 1   
    \- Requirement(s): Completion time must appear after solving the puzzle.  
    \- Purpose: Ensure speed-focused players can view their time.  
    \- Test Case:  
        a) Feature: Completion timer  
        b) Test:  Fill puzzle correctly and complete the puzzle  
        c) Expected Result / Behavior: Completion time is displayed accurately.  
        d) Automation Candidate: No, it needs the whole puzzle to be completed.

\- Acceptance Criterion 2   
    \- Requirement(s): Completion screen includes the completion time, hello kitty graphic, and buttons for restart and main menu.  
    \- Purpose:  Ensure the full win screen shows when the puzzle is completed.  
    \- Setup:  Trigger win state sing a valid final board.  
    \- Test Case:  
        a) Feature: Win Screen.  
        b) Test:  Complete puzzle, and then look at the screen for the win menu.  
        c) Expected Result / Behavior: The completion time, graphic, and buttons all appear after completion.  
        d) Automation Candidate:  Partial automation, the button logic can be automated but not the graphic.

\---

3\. Boundary and Edge Testing

Boundary / Edge 1:  Selecting the Cell  
    \- Requirement(s): Player may only select valid coordinates in the 9x9 grid; selection of filled or invalid cells have to be rejected.  
    \- Purpose: Ensure grid navigation is bug-free and out-of-range input does not interfere with the intended behavior.

    \- Test Case 1: Upper Boundary  
        a) Upper Boundary: Index values 0 and 8 (edges of the valid range)  
        b) Testing data used: \< \- 1 , 0, 1 \> and \< 7 ,8, 9 \>  
        c) Expected Result / Behavior: Valid indexes select properly, and the invalid ones do not select.  
        d) Automation Candidate:  Yes, this is rule-based bounds testing.

    \- Test Case 2: Lower Boundary  
        a) Lower Boundary:  Selecting already-filled coordinates  
        b) Testing data used: A filled cell with two empty cells around it.  
        c) Expected Result / Behavior:  Filled cells do not accept selection or do not allow number input.  
        d) Automation Candidate: Yes, rule-based cell state check. 

Boundary / Edge 2:  Inputting the Number

    \- Purpose: 

    \- Test Case 1:  
        a) Upper Boundary: Entering a number already present in the same 3x3 grid  
        b) Testing data used: \< 1,2, INPUT(1) \>  
        c) Expected Result / Behavior:  Duplicate number is rejected and the selection input does not go through  
        d) Automation Candidate:  Yes, rule-based check.

    \- Test Case 2:  
        a) Lower Boundary: Entering numbers outside of the valid range  
        b) Testing data used: \< 0 or \-1 \>  
        c) Expected Result / Behavior: Input rejected, grid is unchanged.  
        d) Automation Candidate:  Yes, rule-based check.

Boundary / Edge 3:  Puzzle Completion  
    \- Requirement(s):   
Puzzle may only trigger a “win”  when all cells are filled with correct values.  
    \- Purpose:   
Ensure the game does not falsely trigger completion nor not trigger when the win screen was properly completed.

    \- Test Case 1:  
        a) Upper Boundary:  Board full except one cell.  
        b) Testing data used: \< one-missing, full-correct other than  the one \>  
        c) Expected Result / Behavior: Win screen does not trigger until the last cell is correct.  
        d) Automation Candidate: No. It’s a complex state validation.

    \- Test Case 2:  
        a) Lower Boundary: Puzzle filled completely but contains an error as the last one.  
        b) Testing data used: Full correct board except one error.  
        c) Expected Result / Behavior: Game does not trigger win and highlights the mistake.  
        d) Automation Candidate:  The UI response to the wrong cell is automated but the rest is not.

\---

4\. Automated Test List  
Which tests were candidates for Automation?  

The features that were good candidates for automation are the tutorial button loading the tutorial screen, difficulty selection, mode based puzzle creation, cell selection, input validation, and preventing numbers to be put in filled cells.

For each candidate, which kind of automated testing is recommended:    
repetitive, rule-based, or high-volume?

High-Volume:

- Generating the puzzle’s grids  
- Verifying sudoku rules across all cells.

Repetitive:

- Tutorial button loading loading screen  
- Difficulty selection  
- Hard mode vs. Normal mode puzzle comparison.  
- Validation of cell selection  
- Validation of range indexes and numbers,  
- Preventing number input into filled cells.

Not Recommended for Automation:

- Tutorial content  
- Visual Graphics  
- Puzzle Completion screen.  
- UI Layout  
  