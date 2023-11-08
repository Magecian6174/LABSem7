#include <bits/stdc++.h>
#include <vector>
using namespace std;

bool compare(pair<int, int> p1, pair<int, int> p2) {
    double v1 = (double)p1.first / p1.second;
    double v2 = (double)p2.first / p2.second;

    return v1 > v2;
}

int knapsack_01(vector<pair<int, int>> items, int capacity) {
    sort(items.begin(), items.end(), compare);
    int n = items.size();
    int maxProfit = 0;

    for (int i = 0; i < n; i++) {
        if (capacity >= items[i].second) {
            maxProfit += items[i].first;
            capacity -= items[i].second;
        } else {
            break;
        }
    }

    return maxProfit;
}

int main() {
    int n;
    cin >> n;
    vector<pair<int, int>> items(n);

    for (int i = 0; i < n; i++) {
        cin >> items[i].first >> items[i].second;
    }

    int capacity;
    cin >> capacity;

    int maxProfit = knapsack_01(items, capacity);

    cout << "Maximum Profit Earned: " << maxProfit << endl;
    return 0;
}
/*Input: N = 3, W = 4, profit[] = {1, 2, 3}, weight[] = {4, 5, 1}
Output: 3
*/
/*
0/1 Knapsack :
Time Complexity: O(N*W). 
where ‘N’ is the number of weight element and ‘W’ is capacity. As for every weight element we traverse through all weight capacities 1<=w<=W.
Auxiliary Space: O(N*W). 
The use of 2-D array of size ‘N*W’.
*/