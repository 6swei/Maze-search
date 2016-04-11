![GitHub Logo](http://i.stack.imgur.com/xEprB.png)

###BFS
###Introduction: 


Breadth-first search (BFS) is an algorithm that finds not just any path to the exit in a maze, but actually finds the shortest path from the start to the finish.It traverses or searches tree or graph data structures. It starts at the tree root (or some arbitrary node of a graph, sometimes referred to as a 'search key’) and explores the neighbor nodes first, before moving to the next level neighbors.

BFS was invented in the late 1950s by E. F. Moore, who used it to find the shortest path out of a maze, and discovered independently by C. Y. Lee as a wire routing algorithm (published 1961).

In this BFS maze-search game, the program would first need to receive standard input from a file where the first line should contain two integers that represents the rows and columns of the maze the program is going to walk through. And then after the first line would comes the maze in a format - a period . stands for a space in the maze, a # stands for a wall in the maze, and a S indicating the starting location and a F stands for the final destination of the maze.

A sample would look like: 
				4 4
				..#.
				..#S
				F.#.
				....
				
Lastly, when the program find the destination in the maze, there will be asterisks * walking back through the path to indicate a path from start location to destination.

A sample would look like:
				4 4
				..#.
				..#S
				F*#*
				.***


###Methods:


char** read maze(int *rows, int *cols) - Allocate a two dimensional array when cin read in numbers for rows and columns of the maze.

void print_maze(char** maze, int rows, int cols) - prints out the maze in two dimensional format

maze_search(char **maze, int rows, int cols) - Performs the BFS search for a valid path. 

add_to_back - for adding the newest discovered location a queue waiting for explore.

remove_from_front - for removing the already explored location from the queue.


###Classes:


queue.cpp/queue.h - define location struct and queue class

mazeio.cpp/mazeio.h - read in files and output files(in and cout)

maze.cpp - main program that utilizes classes above to perform BFS and return corresponding result for different mazes.
 
maze1, maze2, maze3 and maze 4 are sample mazes. For starting a game, type in $ ./maze < maze1.in under Linux Virtual Machine.


###Reference:

“Recall: breadth-first search, step by step” 
 - http://www-bcf.usc.edu/~skoenig/icaps/icaps04/icapspapers/ICAPS04ZhouR.pdf

“C++ for Everyone”, 2nd Ed. by Cay Horstmann

“Breadth-first search” - https://en.wikipedia.org/wiki/Breadth-first_search

“Graph Theory” - An Introduction! - https://www.youtube.com/watch?v=HmQR8Xy9DeM



