#include <iostream>
#include <iomanip>
#include <windows.h>

using namespace std;

class DigitalClock {
private:
    int hour, min, sec;

public:
    DigitalClock() : hour(0), min(0), sec(0) {}

    void getUserInput() {
        cout << setw(70) << "*Enter Current time*\n";
        cout << "HH- "; cin >> hour;
        while (hour < 0 || hour >= 24) {
            cout << "Invalid input for hours. Please enter a value between 0 and 23: ";
            cin >> hour;
        }

        cout << "MM- "; cin >> min;
        while (min < 0 || min >= 60) {
            cout << "Invalid input for minutes. Please enter a value between 0 and 59: ";
            cin >> min;
        }

        cout << "SS- "; cin >> sec;
        while (sec < 0 || sec >= 60) {
            cout << "Invalid input for seconds. Please enter a value between 0 and 59: ";
            cin >> sec;
        }
    }

    void displayClock() {
        while (true) {
            // Clear the screen
            system("cls");

            // Display the current time
            cout << "\n\n\n\n~~~~~~~~~" << "~~~~~~~~~~~~~~~~~~~~~" << "~~~~~~~~~~~~~~~~~~"
                 << "Current Time = " << setw(2) << setfill('0') << hour << ":"
                 << setw(2) << setfill('0') << min << ":"
                 << setw(2) << setfill('0') << sec << " Hrs~~~~~~~~~~~~~~~~~~"
                 << "~~~~~~~~~~~~~~~~~~~~~" << "~~~~~~~~~";
            // Sleep for 1 second
            Sleep(1000);

            // Update the time
            sec++;
            if (sec == 60) {
                sec = 0;
                min++;
                if (min == 60) {
                    min = 0;
                    hour++;
                    if (hour == 24) {
                        hour = 0;
                    }
                }
            }
        }
    }
};

int main() {
    DigitalClock clock;
    clock.getUserInput();
    clock.displayClock();
    return 0;
}
