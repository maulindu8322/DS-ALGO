### Given an integer number n, return the difference between the product of its digits and the sum of its digits.

    class Solution {
    public:
        int subtractProductAndSum(int n) {
            string s = to_string(n);
            int sum = 0;
            int product = 1;
            int integer = 0;
            for(int i=0;i<s.size();i++)
            {
                char p = s[i];
                if ('0' <= p && p <= '9')
                    integer = p - '0';
                sum += integer;
                product *= integer;
            }
            return product - sum;
        }
    };
    
 ### Technique
  
  - Convert int to string
  - For each char in string, this code will convert char to int
  
          if ('0' <= p && p <= '9')
            integer = p - '0';
