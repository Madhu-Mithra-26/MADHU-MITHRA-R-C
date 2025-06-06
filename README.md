Project Description:

A simple console-based system where you can:

Add student records

View all students

Search for a student by ID

Delete a student

Save records to a file



---

🛠️ Technologies Used:

Java (Core)

No external libraries required

File I/O (optional but useful)



---

📂 Project Structure:

StudentManagement/
├── Student.java
├── StudentManager.java
└── Main.java


---

📄 1. Student.java

public class Student {
    int id;
    String name;
    int age;

    public Student(int id, String name, int age) {
        this.id = id;
        this.name = name;
        this.age = age;
    }

    public String toString() {
        return "ID: " + id + ", Name: " + name + ", Age: " + age;
    }
}


---

📄 2. StudentManager.java

import java.util.ArrayList;
import java.util.Scanner;

public class StudentManager {
    ArrayList<Student> students = new ArrayList<>();
    Scanner scanner = new Scanner(System.in);

    public void addStudent() {
        System.out.print("Enter ID: ");
        int id = scanner.nextInt();
        scanner.nextLine(); // consume newline

        System.out.print("Enter Name: ");
        String name = scanner.nextLine();

        System.out.print("Enter Age: ");
        int age = scanner.nextInt();

        students.add(new Student(id, name, age));
        System.out.println("Student added successfully.\n");
    }

    public void viewStudents() {
        if (students.isEmpty()) {
            System.out.println("No students found.\n");
        } else {
            for (Student s : students) {
                System.out.println(s);
            }
            System.out.println();
        }
    }

    public void searchStudent() {
        System.out.print("Enter ID to search: ");
        int id = scanner.nextInt();
        for (Student s : students) {
            if (s.id == id) {
                System.out.println("Student found: " + s + "\n");
                return;
            }
        }
        System.out.println("Student not found.\n");
    }

    public void deleteStudent() {
        System.out.print("Enter ID to delete: ");
        int id = scanner.nextInt();
        for (Student s : students) {
            if (s.id == id) {
                students.remove(s);
                System.out.println("Student deleted.\n");
                return;
            }
        }
        System.out.println("Student not found.\n");
    }
}


---

📄 3. Main.java

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        StudentManager manager = new StudentManager();
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("===== Student Management System =====");
            System.out.println("1. Add Student");
            System.out.println("2. View Students");
            System.out.println("3. Search Student");
            System.out.println("4. Delete Student");
            System.out.println("5. Exit");
            System.out.print("Enter choice: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1 -> manager.addStudent();
                case 2 -> manager.viewStudents();
                case 3 -> manager.searchStudent();
                case 4 -> manager.deleteStudent();
                case 5 -> System.out.println("Exiting...");
                default -> System.out.println("Invalid choice. Try again.\n");
            }
        } while (choice != 5);
    }
}
