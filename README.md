# Solution
Solution to https://leetcode.com/problems/find-the-winner-of-an-array-game/ 
We create a new array arr1 where arr1[i] is the number of wins of the element at the ith position until the greatest element in the array reaches the first position. To fill the values in we keep a left pointer and traverse the array keeping track of the greatest element till that position and if the greatest element happens to be that element we update the number of wins of the element in the position of left pointer and change the left pointer to this new position and reset set number of wins to 1, and if this position does not hold the greatest element till now we just increment the number of wins by 1. In the end we also add the number of wins to the arr1[left pointer]. Now that we have the arr1, we simply traverse the arr1 until we get a value >=k and then break. If we don't get such a value we return the greatest element in arr. Thus we are doing it in O(n) time (traversing the array twice) and O(n) extra space (arr1).

class Solution {
public:
    int getWinner(vector<int>& arr, int k) {
        int arr1[200000],i,j,x,y,z;
        for (i=0;i<arr.size();i++)
        {
            arr1[i]=0;
        }
        x=0;y=arr[0];z=0;
        for (i=1;i<arr.size();i++)
        {
            if (arr[i]<y)
            {
                z++;
            }
            else
            {
                y=arr[i];
                arr1[x]=z;
                x=i;
                z=1;
            }
        }
        arr1[x]=z;
        z=-1;
        for (i=0;i<arr.size();i++)
        {
            if (arr1[i]>=k)
            {
                z=arr[i];
                break;
            }
        }
        if (z==-1)
        {
            z=y;
        }
        return z;
    }
};
  
