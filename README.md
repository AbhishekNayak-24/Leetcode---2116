# Leetcode---2116
Check If a Parentheses String Can Be Valid
//code in java
public class Solution {
    public boolean canBeValid(String s, String locked) {
        if (s.length() % 2 != 0) return false;

        int open = 0, close = 0, free = 0;
        for (int i = 0; i < s.length(); i++) {
            if (locked.charAt(i) == '0') {
                free++;
            } else if (s.charAt(i) == '(') {
                open++;
            } else {
                close++;
            }
            if (close > open + free) return false;
        }

        open = 0;
        close = 0;
        free = 0;
        for (int i = s.length() - 1; i >= 0; i--) {
            if (locked.charAt(i) == '0') {
                free++;
            } else if (s.charAt(i) == '(') {
                open++;
            } else {
                close++;
            }
            if (open > close + free) return false;
        }

        return true;
    }
}


