Name: Peter Bezgoubov
Date: 23/09/2025
Problem: Valid Sudoku

class Solution {
public:
   bool isValidSudoku(vector<vector<char>>& board) {
       unordered_map<int, unordered_set<char>> rows;
       unordered_map<int, unordered_set<char>> col;
       unordered_map<int, unordered_set<char>> squares;
       for (int i = 0; i < 9; i++) {
           for (int j = 0; j < 9; j++) {
               char c = board[i][j];
               if (c == '.') {
                   continue;
               }
               int b = ((i/3) * 3) + (j/3);
               if (rows[i].count(c) || col[j].count(c) || squares[b].count(c)) {
                   return false;
               }
               rows[i].insert(c);
               col[j].insert(c);
               squares[b].insert(c);
           }
       }
       return true;
   }
};


Writeup: This one was a bit hard. I didn’t think of 3 hashmaps at first so I struggled a bit. You basically just use 3 hashmaps for each condition of sudoku: Rows, Columns and Squares. As you pass through the board, you check if this value already exists in its corresponding column, row or square. If it does exist, you return false. If not, you store it in its corresponding place. 

The first value of each hashmap is either the row, column or square number and the values stored are the individual char’s. For example, when we check the very center value, we go into each hashmap and see, is there a ‘9’ in row 4, column 4, or square 4? If there is, we know it's invalid then return false, if not we add 9 to each corresponding place.

Complexity: Time = O(n^2), Space = O(n)
