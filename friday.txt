/*
 ID: dearxia1
 PROG: friday
 LANG: C++
 */

#include <iostream>
#include <fstream>
#include <string.h>
#include <stdio.h>

using namespace std;

const int month[12] = {31, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30};  //December ~ November

int leap(int num)
{
    if (num % 4)
        return 0;
    if ((num % 100 == 0) && (num % 400))
        return 0;
    return 1;
}

int main()
{
    ofstream fout ("friday.out");
    ifstream fin ("friday.in");
    int n, day[7] = {}, date;
    fin >> n;
    date = 2;    //first 13rd is Saturday, previous 13rd is Wednesday
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < 12; j++) {
            date += month[j] % 7;
            if (j ==2) date += leap(1900 + i);
            if (date > 6)
                date -= 7;
            day[date] ++;
        }
    }
    fout << day[5] << ' ' << day[6] << ' ' << day[0] << ' ' << day[1] << ' ' << day[2] << ' ' << day[3] << ' ' << day[4] << '\n';
    return 0;
}
