#include <iostream>
#include <ctime>
#include <vector>

using namespace std;

class number{
private:
    int targetnum;
    int takes;

public:
    number(){
        srand(time(0));
        int lo = 100, hi = 999;
        targetnum = lo + (rand() % (hi - lo + 1));
        takes = 0;
    }

    bool compare(int temp){
        takes++;
        cout << targetnum;
        if(temp == targetnum){
            cout << "You have guessed the correct number." << endl;
            cout << "Number of takes " << takes << endl;
            return true;
        }
        else if(abs(targetnum - temp) >= 300){
            cout << "Frozen" << endl;
        }
        else if(abs(targetnum - temp) <= 300 && abs(targetnum - temp) >= 150){
            cout << "Cold" << endl;
        }
        else if(abs(targetnum - temp) <= 150 && abs(targetnum - temp) >= 50){
            cout << "Warm" << endl;
        }
        else if(abs(targetnum - temp) <= 50 && abs(targetnum - temp) >= 10){
            cout << "Hot" << endl;
        }
        else if(abs(targetnum - temp) <= 10){
            cout << "BURNING" << endl;
        }
        else{
            return false;
        }
        cout << "Number of takes " << takes << endl;
        return false;
    }
};

int main(){
    
    cout << "Hello Player " << endl;
    cout << "Welcome to NUMBER GUESSING GAME" << endl;
    cout << "I(computer) have selected a randome number from 100 to 999" << endl;
    cout << "All you need to do is to guess the number as the game name indicates and I'll help in the following way" << endl;
    cout << "If the guessed number is in certain range I'll call out for it" << endl;
    cout << "Greater than 300 Frozen" << endl << "+-300 Cold" << endl << "+-150 Warm" << endl << "+-50 Hot" << endl << "+-10 Burning" << endl;
    cout << "If while gussing if you press 0 the game will end" << endl;

    string choice;
    int guess;
    while(1){
        cout << "Shall we continue with the game" << endl << "YES or NO(all caps or all small plz):  ";
        cin >> choice;
        if(choice == "YES" || choice == "yes"){
            number *n = new number;
            cout << "Please start guessing: ";
            while(guess != 0){
                cin >> guess;
                if(guess == 0) continue;
                bool found = n->compare(guess);
                if(found) break;
                cout << "Guess again: ";
            }
        }
        else if(choice == "NO" || choice == "no"){
            cout << "Thank You" << endl;
            return 0;
        }
        else{
            cout << "Enter valid option:"
        }
    }
    return 0;
}
