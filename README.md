#include <iostream>
#include <string> // Include for string handling
using namespace std;

// Function to convert letter grade to grade points
double gradeToPoints(string grade) 
{
    if (grade == "A" || grade == "a") return 4.0;
    if (grade == "B+" || grade == "b+") return 3.5;
    if (grade == "B" || grade == "b") return 3.0;
    if (grade == "C+" || grade == "c+") return 2.5;
    if (grade == "C" || grade == "c") return 2.0;
    if (grade == "D+" || grade == "d+") return 1.5;
    if (grade == "D" || grade == "d") return 1.0;
    if (grade == "F" || grade == "f") return 0.0;

    cout << "Invalid grade. Please enter a grade between A and F." << endl;
    return -1; // Return -1 to indicate an invalid grade
}

int main() {
    int numberOfSemesters;
    cout << "Enter the number of semesters: ";
    cin >> numberOfSemesters;

    double totalGradePoints = 0;
    int totalCredits = 0;

    for (int semester = 1; semester <= numberOfSemesters; ++semester) {
        int numberOfCourses;
        cout << "Enter the number of courses for semester " << semester << ": ";
        cin >> numberOfCourses;

        double semesterGradePoints = 0;
        int semesterCredits = 0;

        for (int course = 1; course <= numberOfCourses; ++course) {
            string grade;  // Declare grade as a string
            int credits;
            
            cout << "Enter the letter grade for course " << course << " (A-F): ";
            cin >> grade;  // Read grade as a string

            double gradePoints = gradeToPoints(grade);
            if (gradePoints == -1) {
                --course; // Repeat current course input if invalid grade
                continue;
            }

            cout << "Enter the credits for course " << course << ": ";
            cin >> credits;

            semesterGradePoints += gradePoints * credits;
            semesterCredits += credits;
        }

        double semesterGPA = semesterGradePoints / semesterCredits;
        cout << "GPA for semester " << semester << ": " << semesterGPA << endl;

        totalGradePoints += semesterGradePoints;
        totalCredits += semesterCredits;
    }

    double cgpa = totalGradePoints / totalCredits;
    cout << "Overall CGPA: " << cgpa << endl;

    return 0;
}
