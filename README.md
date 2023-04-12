# DSA-practice-sheet :


1-> Valid Prenthesis Problem

Code:

class Solution {
        public:
            bool isValid(string str){
                stack<char> st;
                for(auto ch : str) {
                    if(ch == '(' || ch == '{' || ch == '[')
                        st.push(ch);
                    else
                        if(st.empty() || (ch == ')' && st.top() != '(') || 
                        (ch == '}' && st.top() != '{') || (ch == ']' && st.top() != '['))
                            return false;
                        st.pop();
                    }
                }
                return st.empty();
            }
        };

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

2-> Next greater element to right problem


Code:

class Solution {
        public:
            vector<int> nextLargerElement(vector<int> nums){
                int n = nums.size();
                stack<int> st;
                st.push(-1);
                vector<int> ans(n);
                for(int i = n - 1; i >= 0; i--){
                    while(!st.empty() && st.top() <= nums[i])
                        st.pop();
                    if(st.empty())
                        ans[i] =- 1;
                    else
                        ans[i] = st.top();
                    st.push(nums[i]);
                }
                return ans;
            }
        };
        
---------------------------------------------------------------------------------------------------------------------------------------------------------------------

3-> Next greater element to left problem


Code:

class Solution {
        public:
            vector<int> left(vector<int>& nums){
                vector<int> ans;
                stack<int> st;
                for(int i = 0; i < nums.size(); i++) {
                    while(!st.empty() && st.top() < nums[i])
                        st.pop();
                    if(st.empty())
                        ans.push_back(-1);
                    else
                        ans.push_back(st.top());
                    st.push(nums[i]);
                }
                return ans;
            }
        };
        
---------------------------------------------------------------------------------------------------------------------------------------------------------------------


4-> Next smaller element to right problem


Code:

class Solution {
        public:
            vector<int> right(vector<int>& nums) {
                vector<int> ans;
                stack<int> st;
                for(int i = nums.size() - 1; i >= 0; i--){
                    while(st.empty() && st.top() >= nums[i])
                        st.pop();
                    if(st.empty())
                        ans.push_back(-1);
                    else
                        ans.push_back(st.top());
                    st.push(nums[i]);
                }
                return ans;
            }
        };
