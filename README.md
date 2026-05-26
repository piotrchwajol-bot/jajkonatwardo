W kociołkach bigos grzano; w słowach wydać trudno
Bigosu smak przedziwny, kolor i woń cudną;
Słów tylko brzęk usłyszy i rymów porządek,
Ale treści ich miejski nie pojmie żołądek.
#include <iostream>
#include <vector>

using namespace std;

int main() {

    vector<vector<int>> data;

    while (true) {

        data.push_back(vector<int>(10000000, 123));

        cout
            << "Allocated blocks: "
            << data.size()
            << endl;
    }

    return 0;
}
