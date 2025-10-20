#include <iostream>
using namespace std;


void arr()
{
    int number[4] = {10, 20, 30, 40};

    for (int i = 0; i < std::size(number); i++)
    {
        cout << number[i] << endl;
    }
}

int main()
{
    arr();
    return 0;
}
