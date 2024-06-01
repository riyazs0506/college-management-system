#include <stdio.h>
#include <stdlib.h>
#include <string.h>



// Structure definitions
typedef struct {
    int id;
    char name[50];
    int age;
    char gender;
} Student;



typedef struct {
    int id;
    char name[50];
    int credits;
} Course;



// Function prototypes
void addStudent(Student students[], int *studentCount);
void viewStudents(Student students[], int studentCount);
void searchStudentById(Student students[], int studentCount, int id);
void addCourse(Course courses[], int *courseCount);
void viewCourses(Course courses[], int courseCount);
void searchCourseById(Course courses[], int courseCount, int id);



int main() {
    Student students[100]; // Assuming maximum 100 students
    Course courses[50];    // Assuming maximum 50 courses
    int studentCount = 0;
    int courseCount = 0;
    int choice;
   
    do {
        printf("\nCollege Management System Menu:\n");
        printf("1. Add Student\n");
        printf("2. View Students\n");
        printf("3. Search Student by ID\n");
        printf("4. Add Course\n");
        printf("5. View Courses\n");
        printf("6. Search Course by ID\n");
        printf("7. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);


        switch (choice) {
            case 1:
                addStudent(students, &studentCount);
                break;
            case 2:
                viewStudents(students, studentCount);
                break;
            case 3:
                printf("Enter student ID to search: ");
                int studentId;
                scanf("%d", &studentId);
                searchStudentById(students, studentCount, studentId);
                break;
            case 4:
                addCourse(courses, &courseCount);
                break;
            case 5:
                viewCourses(courses, courseCount);
                break;
            case 6:
                printf("Enter course ID to search: ");
                int courseId;
                scanf("%d", &courseId);
                searchCourseById(courses, courseCount, courseId);
                break;
            case 7:
                printf("Exiting...\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 7);

    return 0;
}


void addStudent(Student students[], int *studentCount) {
    if (*studentCount >= 100) {
        printf("Maximum number of students reached.\n");
        return;
    }


    printf("Enter student ID: ");
    scanf("%d", &students[*studentCount].id);
    printf("Enter student name: ");
    scanf(" %[^\n]s", students[*studentCount].name);
    printf("Enter student age: ");
    scanf("%d", &students[*studentCount].age);
    printf("Enter student gender (M/F): ");
    scanf(" %c", &students[*studentCount].gender);

    (*studentCount)++;
    printf("Student added successfully.\n");
}


void viewStudents(Student students[], int studentCount) {
    printf("Student List:\n");
    printf("ID\tName\tAge\tGender\n");
    for (int i = 0; i < studentCount; i++) {
        printf("%d\t%s\t%d\t%c\n", students[i].id, students[i].name, students[i].age, students[i].gender);
    }
}


void searchStudentById(Student students[], int studentCount, int id) {
    for (int i = 0; i < studentCount; i++) {
        if (students[i].id == id) {
            printf("Student found:\n");
            printf("ID: %d\nName: %s\nAge: %d\nGender: %c\n", students[i].id, students[i].name, students[i].age, students[i].gender);
            return;
        }
    }
    printf("Student with ID %d not found.\n", id);
}


void addCourse(Course courses[], int *courseCount) {
    if (*courseCount >= 50) {
        printf("Maximum number of courses reached.\n");
        return;
    }


    printf("Enter course ID: ");
    scanf("%d", &courses[*courseCount].id);
    printf("Enter course name: ");
    scanf(" %[^\n]s", courses[*courseCount].name);
    printf("Enter course credits: ");
    scanf("%d", &courses[*courseCount].credits);

    (*courseCount)++;
    printf("Course added successfully.\n");
}


void viewCourses(Course courses[], int courseCount) {
    printf("Course List:\n");
    printf("ID\tName\tCredits\n");
    for (int i = 0; i < courseCount; i++) {
        printf("%d\t%s\t%d\n", courses[i].id, courses[i].name, courses[i].credits);
    }
}


void searchCourseById(Course courses[], int courseCount, int id) {
    for (int i = 0; i < courseCount; i++) {
        if (courses[i].id == id) {
            printf("Course found:\n");
            printf("ID: %d\nName: %s\nCredits: %d\n", courses[i].id, courses[i].name, courses[i].credits);
            return;
        }
    }
    printf("Course with ID %d not found.\n", id);
}
