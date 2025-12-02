class Solution {
public:
    void reverse(int i,int j, vector<int>& v){
        while(i<j){
            int temp=v[i];
            v[i]=v[j];
            v[j]=temp;
            i++;
            j--;
        }
    }
    
    void nextPermutation(vector<int>& nums) {
        int pivot=-1;
        int n=nums.size();
        for(int i=n-1;i>0;i--){
            if(nums[i]>nums[i-1]){
                pivot=i-1;
                break;
            }
        }
        if(pivot==-1){
            reverse(0,n-1,nums);
        }
        else{
            reverse(pivot+1,n-1,nums);
            //next largest..
            for(int i=pivot+1;i<n;i++){
                if(nums[pivot]< nums[i]){
                    int temp=nums[pivot];
                    nums[pivot]=nums[i];
                    nums[i]=temp;
                    break;
                }
            }
        }
    }
};