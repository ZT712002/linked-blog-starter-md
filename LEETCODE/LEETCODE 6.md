zigzag conversion 
#string 
The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)
**Example 1:**

**Input:** s = "PAYPALISHIRING", numRows = 3
**Output:** "PAHNAPLSIIGYIR"


First and last row,

formula is just (numRows-1)  times 2

the inbetween rows will be the same, however for the edge cases like 
L and I, or A and R in the 3rd row that are not captured.

![](_attachments/Pasted%20image%2020240522123353.png)
The formula will be 2* (NumRows -1) - 2* ( current row that is not first or last row)


answer in c++ here
```
class Solution {

public:

    string convert(string s, int numRows) {

        if(numRows==1) return s; <-- If only 1 row no zigzag

        string ans; <-- this will be the final answer as we will be concatenating the rest

        for(int r = 0; r < numRows;r++){

            int increment = 2*(numRows-1);

            for(int i =r;i<s.length();){

                ans = ans+s[i];

                if(r>0 && r<numRows-1){

                    int temp =i+increment-2*r;

                    if(temp<s.length()){

                        ans += s[temp];

                    }

                }

                i = i+increment;

            }

        }

        return ans;

    }

};
```


edit 123