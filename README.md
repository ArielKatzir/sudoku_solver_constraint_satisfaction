Sudoku Solver Coursework

### <u>The Algorithm<u/>
The chosen algorithm is the course's recommended algorithm, __backtracking depth-first search with constraint satisfaction__. After an online search of different search algorithms for tasks such as sudoku solving, I found this to be one of the most commonly used algorithms. I chose this algorithm as I was already familiar with it and it yielded practical solving times and always had successful or unsuccessful outcomes.
To implement this algorithm I used the example code of the 8-Queen puzzle given via Moodle to better understand the approach I should take when completing this task. Before starting the work on the algorithm itself I wanted to create a few helper functions in order to have a simpler time writing the algorithm itself. For example, similarly to the example code, I made an _isValid()_ function to check if a row, column, box or the board as a whole are valid. I implemented those by iterating over the board every time the function is called. However, I believe that one of the main reasons for my relatively slow solving times is my _boxValid()_ function. It iterates over the whole board instead of the chosen box leading to redundant calculations and therefore, slower solving times. With more time in hand, I would have attempted to improve it.  

One approach I took when trying to simplify the method of picking the next cell to fill, was by creating a second 9x9 grid where cells contain the number of possible values they can take. Then, choosing the next value was simply a matter of picking the smallest one in the grid. 

An example of this can be seen below where the left image is a stage in the process of solving a hard sudoku, and on the right, is the 9x9 grid of the corresponding possible values where an already filled cell would have a 10 filled in since any number less than that has the chance to be picked for the next cell to fill.

![board vs values array](https://github.com/ArielKatzir/sudoku_solver_constraint_satisfaction/blob/master/images/example.PNG)

After doing that, making the main algorithm was made similarly to the one made in the 8-Queens' puzzle code. A new cell would be picked and its possible values would be calculated and the first one on the list would be filled in the cell. Then recursion is used on the next picked cell. If the validation function returns false, the current board state would backtrack and try a different and continue until the board is completely solved, or all of the possible values in one of the cells fail to be valid ones. In the case of failure, a 9x9 grid filled with -1's would be returned.

### <u>Improvements and different approaches<u/>

With more time in hand, solving time could be greatly reduced. One section in my implementation that I wasn't satisfied with was the functions I used to divide and retrieve values from the 3x3 boxes in the 9x9 grid. My method was to iterate over the grid with jumps of 3 and storing the values in the boxes in 9x1x9 arrays. Whenever values from the given box were needed to be retrieved to check the possible values domain of a single cell, the whole board was iterated over which dramatically increases soling time. A solution to that could be a global 9x9 board variable where every row can contain a box, and every time a new cell is filled, that board updates. This could have made values easily retrievable with a great reduction in the redundancy of computing power and time.

When looking for an algorithm to use for solving sudoku boards online, I came across an algorithm called algorithm X made by Donald Knuth which was said to perform better than constraint satisfaction. It was made to solve __exact cover__ problems which meant I had to convert data taken from the sudoku board to meet the exact cover form before applying the algorithm to it. As interesting as it sounded, I was more familiar with constraint satisfaction and therefore could do it with more ease and less worry from running out of time.

* Could make the sudoku solvable for n^2 x n^2 where n is an integer.
* Make avaliable to run on a website
* Make inputting a new sudoku possible
* Write a code to create new sudokus 
