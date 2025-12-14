# Project

https://www.youtube.com/watch?v=EReYJoxo9Jo

## Task 1

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
#include <string>

using namespace std;

vector<string> find_common_players(
    const vector<vector<string>>& sport1,
    const vector<vector<string>>& sport2
) {
    unordered_set<string> names;
    vector<string> result;

    // Store full names from the first sport
    for (const auto& player : sport1) {
        string full_name = player[0] + " " + player[1];
        names.insert(full_name);
    }

    // Check for matches in the second sport
    for (const auto& player : sport2) {
        string full_name = player[0] + " " + player[1];
        if (names.count(full_name)) {
            result.push_back(full_name);
        }
    }

    return result;
}

int main() {
    vector<vector<string>> basketball_players = {
        {"Jill", "Huang", "Gators"},
        {"Janko", "Barton", "Sharks"},
        {"Wanda", "Vakulskas", "Sharks"},
        {"Jill", "Moloney", "Gators"},
        {"Luuk", "Watkins", "Gators"}
    };

    vector<vector<string>> football_players = {
        {"Hanzla", "Radosti", "32ers"},
        {"Tina", "Watkins", "Barleycorns"},
        {"Alex", "Patel", "32ers"},
        {"Jill", "Huang", "Barleycorns"},
        {"Wanda", "Vakulskas", "Barleycorns"}
    };

    vector<string> common_players =
        find_common_players(basketball_players, football_players);

    for (const auto& name : common_players) {
        cout << name << endl;
    }

    return 0;
}
```

## Task 2

```cpp
#include <iostream>
#include <vector>

using namespace std;

int find_missing_number(const vector<int>& nums) {
    int n = nums.size();
    int expected = n * (n + 1) / 2;
    int actual = 0;

    for (int num : nums) {
        actual += num;
    }

    return expected - actual;
}

int main() {
    vector<int> nums1 = {2, 3, 0, 6, 1, 5};
    vector<int> nums2 = {8, 2, 3, 9, 4, 7, 5, 0, 6};

    cout << find_missing_number(nums1) << endl;
    cout << find_missing_number(nums2) << endl;

    return 0;
}
```

## Task 3

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int max_profit(const vector<int>& prices) {
    if (prices.size() < 2) return 0;

    int min_price = prices[0];
    int max_profit = 0;

    for (size_t i = 1; i < prices.size(); i++) {
        int profit = prices[i] - min_price;
        max_profit = max(max_profit, profit);
        min_price = min(min_price, prices[i]);
    }

    return max_profit;
}

int main() {
    vector<int> prices = {10, 7, 5, 8, 11, 2, 6};
    cout << max_profit(prices) << endl; // 6
    return 0;
}
```


## Task 4

```cpp
#include <iostream>
#include <vector>
#include <climits>

using namespace std;

int highest_product_of_two(const vector<int>& nums) {
    int max1 = INT_MIN, max2 = INT_MIN;
    int min1 = INT_MAX, min2 = INT_MAX;

    for (int n : nums) {
        // Update largest values
        if (n > max1) {
            max2 = max1;
            max1 = n;
        } else if (n > max2) {
            max2 = n;
        }

        // Update smallest values
        if (n < min1) {
            min2 = min1;
            min1 = n;
        } else if (n < min2) {
            min2 = n;
        }
    }

    return max(max1 * max2, min1 * min2);
}

int main() {
    vector<int> nums = {5, -10, -6, 9, 4};
    cout << highest_product_of_two(nums) << endl;
    return 0;
}
```

## Task 5

```cpp
#include <iostream>
#include <vector>

using namespace std;

void sort_temperatures(vector<double>& temps) {
    const int MIN_TEMP = 970;
    const int MAX_TEMP = 990;
    const int RANGE = MAX_TEMP - MIN_TEMP + 1;

    vector<int> count(RANGE, 0);

    // Count occurrences
    for (double temp : temps) {
        int index = static_cast<int>(temp * 10) - MIN_TEMP;
        count[index]++;
    }

    // Rebuild sorted array
    int idx = 0;
    for (int i = 0; i < RANGE; i++) {
        while (count[i] > 0) {
            temps[idx++] = (MIN_TEMP + i) / 10.0;
            count[i]--;
        }
    }
}

int main() {
    vector<double> temps = {
        98.6, 98.0, 97.1, 99.0, 98.9,
        97.8, 98.5, 98.2, 98.0, 97.1
    };

    sort_temperatures(temps);

    for (double t : temps) {
        cout << t << " ";
    }

    return 0;
}
```

## Task 6

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
#include <algorithm>

using namespace std;

int longest_consecutive_sequence(const vector<int>& nums) {
    unordered_set<int> s(nums.begin(), nums.end());
    int longest = 0;

    for (int num : nums) {
        // Only start counting if this is the beginning of a sequence
        if (s.find(num - 1) == s.end()) {
            int current = num;
            int length = 1;

            while (s.find(current + 1) != s.end()) {
                current++;
                length++;
            }

            longest = max(longest, length);
        }
    }

    return longest;
}

int main() {
    vector<int> nums1 = {10, 5, 12, 3, 55, 30, 4, 11, 2};
    vector<int> nums2 = {19, 13, 15, 12, 18, 14, 17, 11};

    cout << longest_consecutive_sequence(nums1) << endl;
    cout << longest_consecutive_sequence(nums2) << endl;

    return 0;
}
```
