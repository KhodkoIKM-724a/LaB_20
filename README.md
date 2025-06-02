#include <iostream>
#include <vector>
#include <cmath>
#include <clocale> 
#include <cstdlib> 

using namespace std;

int main() {
    setlocale(LC_ALL, "");
    system("chcp 65001 > nul");

    int n;
    cout << "Введіть ціле число: ";
    cin >> n;

    vector<int> digits;
    int temp = abs(n); 

    if (temp == 0) {
        digits.push_back(0);
    }
    else {
        while (temp > 0) {
            digits.insert(digits.begin(), temp % 10);
            temp /= 10;
        }
    }

    cout << "Цифри числа: ";
    for (int d : digits) {
        cout << d << " ";
    }
    cout << endl;

    int evenCount = 0;
    for (int d : digits) {
        if (d % 2 == 0) evenCount++;
    }
    cout << "Кількість парних цифр: " << evenCount << endl;

    int maxIdx = 0, minIdx = 0;
    for (int i = 1; i < digits.size(); i++) {
        if (abs(digits[i]) > abs(digits[maxIdx])) maxIdx = i;
        if (abs(digits[i]) < abs(digits[minIdx])) minIdx = i;
    }

    int start = min(maxIdx, minIdx) + 1;
    int end = max(maxIdx, minIdx);
    int product = 1;
    bool found = false;
    for (int i = start; i < end; i++) {
        product *= digits[i];
        found = true;
    }

    if (found)
        cout << "Добуток елементів між максимальним і мінімальним за модулем: " << product << endl;
    else
        cout << "Між максимальним і мінімальним за модулем немає елементів." << endl;

    return 0;
}
