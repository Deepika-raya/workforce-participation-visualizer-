#include <iostream>
#include <fstream>
#include <sstream>
#include <vector>
#include <iomanip>

using namespace std;

// ANSI Color Codes
#define BLUE "\033[34m"
#define PINK "\033[35m"
#define GREEN "\033[32m"
#define RED "\033[31m"
#define RESET "\033[0m"

struct WorkforceData {
    string sector;
    int male;
    int female;
};

void drawChart(string label, int value, string color) {
    cout << color << setw(15) << left << label << " : ";

    for (int i = 0; i < value / 2; i++) {
        cout << "█";
    }

    cout << " (" << value << "%)" << RESET << endl;
}

int main() {
    vector<WorkforceData> data;
    ifstream file("workforce.csv");

    if (!file) {
        cout << RED << "Error opening CSV file!" << RESET << endl;
        return 1;
    }

    string line;

    // Skip header
    getline(file, line);

    while (getline(file, line)) {
        stringstream ss(line);

        WorkforceData wd;
        string maleStr, femaleStr;

        getline(ss, wd.sector, ',');
        getline(ss, maleStr, ',');
        getline(ss, femaleStr, ',');

        wd.male = stoi(maleStr);
        wd.female = stoi(femaleStr);

        data.push_back(wd);
    }

    cout << GREEN;
    cout << "\n========================================\n";
    cout << "   WORKFORCE PARTICIPATION VISUALIZER   \n";
    cout << "========================================\n";
    cout << RESET;

    for (auto &d : data) {
        cout << "\nSector: " << d.sector << endl;

        drawChart("Male", d.male, BLUE);
        drawChart("Female", d.female, PINK);

        int gap = abs(d.male - d.female);

        cout << GREEN << "Gender Gap : " << gap << "%" << RESET << endl;
        cout << "----------------------------------------" << endl;
    }

    file.close();

    return 0;
}
