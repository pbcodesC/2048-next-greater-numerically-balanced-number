# 2048-next-greater-numerically-balanced-number
class Solution {
public:
    bool isBalanced(int num) {
        vector<int> count(10, 0);
        int x = num;
        while (x > 0) {
            int d = x % 10;
            if (d == 0) return false;         // 0 cannot appear
            count[d]++;
            x /= 10;
        }
        for (int d = 1; d <= 9; d++) {
            if (count[d] > 0 && count[d] != d) {
                return false;
            }
        }
        return true;
    }

    int nextBeautifulNumber(int n) {
        int x = n + 1;
        while (true) {
            if (isBalanced(x)) {
                return x;
            }
            x++;
        }
    }
};
