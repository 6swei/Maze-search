/* 
maze.cpp

Author:Jingwei Luo

Short description of this file: It contains the main function 
and maze_search function that uses BFS to search the shortest 
path for a maze. 
*/

#include <iostream>
#include "mazeio.h"
#include "queue.h"

using namespace std;

// Prototype for maze_search, which you will fill in below.
int maze_search(char**, int, int);

// main function to read, solve maze, and print result
int main() {
   int rows, cols, result;
   char** mymaze;
   cin >> rows >> cols;
   mymaze = read_maze(&rows, &cols); 
   
   for(int i=0; i<rows; i++){
      for(int j=0; j<cols; j++){
         cin >> mymaze[i][j];
      }
   }
   
   if (mymaze == NULL) {
      cout << "Error, input format incorrect" << endl;
      return 1;
   }
   
   // when working on Checkpoint 3, you will call maze_search here.
   // here. but for Checkpoint 1, just assume we found the path.
   //result = 1; // TO BE CHANGED

   // examine value returned by maze_search and print appropriate output
   result = maze_search(mymaze, rows, cols);
   
   if (result == 1) { // path found!
      cout << rows <<" "<< cols << endl;
      print_maze(mymaze, rows, cols);
   }
   else if (result == 0) { // no path :(
      cout << "No path could be found!" << endl;
   }
   else { // result == -1
      cout << "Invalid maze." << endl;
   }

   // ADD CODE HERE to delete all memory 
   // that read_maze allocated
   for(int i=0; i<rows; i++){
      delete [] mymaze[i];
   }
   delete [] mymaze;
   
   return 0;
}

/**************************************************
 * Attempt to find shortest path and return:
 *  1 if successful
 *  0 if no path exists
 * -1 if invalid maze (not exactly one S and one F)
 *
 * If path is found fill it in with '*' characters
 *  but don't overwrite the 'S' and 'F' cells
 *************************************************/
int maze_search(char** maze, int rows, int cols) {
   
   //Creating the visited grid
   int** visited = new int*[rows];
   for(int i=0; i<rows; i++){
      visited[i] = new int[cols];
         for(int j=0; j<cols; j++){
            visited[i][j] = 0; //initilze all to 0
         }  
   }
   //Creating the predecessor grid
   Location** predecessor = new Location*[rows];
   for(int i=0; i<rows; i++){
      predecessor[i] = new Location[cols];         
   }
   //Creating a queue
   Queue q(rows*cols);
   
   // Check if there is start and end point
   int start = 0;
   int end = 0;
   Location startpoint;
   
   for(int i=0; i<rows; i++){
      for(int j=0; j<cols; j++){
         if(maze[i][j] == 'S'){
            start++;
            startpoint.row = i;
            startpoint.col = j;
            q.add_to_back(startpoint);
         }
         if(maze[i][j] == 'F'){
            end++;
         }
      }
   }
   
   //Check if it is a valid maze
   if(start != 1 || end !=1){
      for(int i=0; i<rows; i++){ 
         delete [] visited[i];
      }
      delete[] visited;
   
      for(int i=0; i<rows; i++){
         delete [] predecessor[i];
      }
      delete [] predecessor;
   
      return -1;
   }
   
   Location curr; // current location
   // initialize north, west, south and east
   Location north, west, south, east; 
   //TO check if path is found
   bool found = false;
   
   while(!(q.is_empty())){
      curr = q.remove_from_front();
      visited[curr.row][curr.col] = 1; 
      
      //For searching north 
      north.row = curr.row - 1;
      north.col = curr.col;
      //make sure inside the maze
      if(north.row>=0 && north.row<rows && 
         north.col>=0 && north.col<cols){
         if(maze[north.row][north.col] == 'F'){
            found = true;
            break;
         }
         //check if it is a valid path
         else if(maze[north.row][north.col] == '.' &&
                visited[north.row][north.col] != 1){
                
                q.add_to_back(north);
                visited[north.row][north.col] = 1;
                predecessor[north.row][north.col] = curr;
         }
      }
      
      //For searching west
      west.row = curr.row;
      west.col = curr.col - 1;
      //make sure inside the maze
      if(west.row>=0 && west.row<rows && 
         west.col>=0 && west.col<cols){
         if(maze[west.row][west.col] == 'F'){
            found = true;
            break;
         }
         //check if it is a valid path
         else if(maze[west.row][west.col] == '.' && 
                visited[west.row][west.col] != 1){
                
                q.add_to_back(west);
                visited[west.row][west.col] = 1;
                predecessor[west.row][west.col] = curr;
         }
      }
      //For searching south
      south.row = curr.row + 1;
      south.col = curr.col;
      //make sure inside the maze
      if(south.row>=0 && south.row<rows && south.col>=0 &&
         south.col<cols){
         if(maze[south.row][south.col] == 'F'){
            found = true;
            break;
         }
         //check if it is a valid path
         else if(maze[south.row][south.col] == '.' && 
                 visited[south.row][south.col] != 1){
                 
                 q.add_to_back(south);
                 visited[south.row][south.col] = 1;
                 predecessor[south.row][south.col] = curr;
         }
      }
      //For searching east
      east.row = curr.row;
      east.col = curr.col + 1;
      //make sure inside the maze
      if(east.row>=0 && east.row<rows && east.col>=0 && 
         east.col<cols){
         if(maze[east.row][east.col] == 'F'){
            found = true;
            break;
         }
         //check if it is a valid path
         else if(maze[east.row][east.col] == '.' && 
                 visited[east.row][east.col] != 1){
                 
                 q.add_to_back(east);
                 visited[east.row][east.col] = 1;
                 predecessor[east.row][east.col] = curr;
         }
      }   
    }
   //delete the visited array allocation since it is no longer used 
   for(int i=0; i<rows; i++){ 
      delete [] visited[i];
   }
   delete[] visited;
   
   //situation when no path exist
   if(!found){
   //delete the predecessor array that have been allocated   
   for(int i=0; i<rows; i++){
      delete [] predecessor[i];
   }
   delete [] predecessor;
      
      return 0;
   }  
         
   // situation when path find    
   else{        
     
      while(maze[curr.row][curr.col] != 'S'){
          maze[curr.row][curr.col] = '*';   
          curr = predecessor[curr.row][curr.col];
      }
         
      for(int i=0; i<rows; i++){
         delete [] predecessor[i];
      }
         delete [] predecessor;
           
      return 1;
   }
   

}

