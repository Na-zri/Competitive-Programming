Longest Palindrome

Problem description:
Given a string s which consists of lowercase or uppercase letters, return the length of the longest palindrome that can be built with those letters.

Letters are case sensitive, for example, "Aa" is not considered a palindrome here.

Example test cases:

Example 1:
Input: s = "abccccdd"
Output: 7
Explanation:
One longest palindrome that can be built is "dccaccd", whose length is 7.

Example 2:

Input: s = "a"
Output: 1
Explanation:
Since there is only 1 letter the only palindrome is "a" of length 1.

Constraints:

1 <= s.length <= 2000
s consits of lower-case and/or upper-case English letters only.

Solution using Python:

        def longestPalSubstr(string): 
    maxLength = 1
  
    start = 0
    length = len(string) 
  
    low = 0
    high = 0
  
    # One by one consider every character as center point of  
    # even and length palindromes 
    for i in xrange(1, length): 
        # Find the longest even length palindrome with center 
    # points as i-1 and i. 
        low = i - 1
        high = i 
        while low >= 0 and high < length and string[low] == string[high]: 
            if high - low + 1 > maxLength: 
                start = low 
                maxLength = high - low + 1
            low -= 1
            high += 1
  
        # Find the longest odd length palindrome with center  
        # point as i 
        low = i - 1
        high = i + 1
        while low >= 0 and high < length and string[low] == string[high]: 
            if high - low + 1 > maxLength: 
                start = low 
                maxLength = high - low + 1
            low -= 1
            high += 1
  
    print "Longest palindrome substring is:", 
    print string[start:start + maxLength] 
  
    return maxLength 
  
# Driver program to test above functions 
string = "malayalam"
print "Length is: " + str(longestPalSubstr(string)) 


Explanation of code:
The task is to find a symmetry with maximum possible characters in the string.
For this, we first find the counts of each character in the string and if it is even we add it to the result and if not, add count-1. 
Finally, if we encountered atleat one odd count character, we need to increment the result by 1.
