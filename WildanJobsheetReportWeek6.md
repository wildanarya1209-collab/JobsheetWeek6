# JOBSHEET 6 - SELECTION STATEMENTS 2

## Student Identity

- **Name:** Wildan Arya Indradiansyah
- **Student ID (NIM):** 264107020257
- **Class / Attendance No.:** TI-1I / 30

---

# 1. Objectives

The objectives of this practicum are:

1. Students can solve problems and case studies using nested selection statements.
2. Students can apply nested selection statements in Java programs.
3. Students can apply the logical operators `&&`, `||`, and `!` in selection structures.

---

# 2. Labs Activities

## 2.1 Experiment 1: Nested IF to Check Thesis Exam Requirements

A student wants to register for the thesis exam. The system first checks that the student has no outstanding penalties. If this is met, it checks the guidance log: at least 8 sessions with Supervisor 1 and at least 4 sessions with Supervisor 2. If any requirement fails, the system shows the reason.

### 2.1.1 Java Program Code

```java
package Week5;
import java.util.Scanner;
public class NestedThesisExamAttendance30 {
    public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);

    //Variable
    String message;
    //input
    System.out.print("Has the student cleared all penalties? (Yes/No): ");
    String noPenalty = sc.nextLine().trim();
    System.out.print("Enter the number of guidance sessions with Supervisor 1: ");
    int guidanceCount1 = sc.nextInt();
    System.out.print("Enter the number of guidance sessions with Supervisor 1: ");
    int guidanceCount2 = sc.nextInt();

    //output and procces
    if (noPenalty.equalsIgnoreCase("Yes")) {
    if (guidanceCount1 >= 8 && guidanceCount2 >= 4) {
        message = "All requirements met. The student may register for the thesis exam";
 }  else if (guidanceCount1 < 8 && guidanceCount2 < 4) {
        message = "Failed! Guidance sessions with Supervisor 1 are below 8 and Supervisor 2 are below 4";
 }  else if (guidanceCount1 < 8) {
        message = "Failed! Guidance sessions with Supervisor 1 have not reached 8";
 }  else {
        message = "Failed! Guidance sessions with Supervisor 2 have not reached 4";
 }
 }   else {
        message = "Failed! The student still has an outstanding penalty";
 }
        System.out.println(message);
        sc.close();

    }
}
```

### 2.1.2 ### 2.1.3 Running Results / Output Screenshot

> **Insert the screenshot of the program output here.**
>
> `![Output Experiment 1](images/percobaan1-output.png)`

### 2.1.3 Answers to Questions / Reflection Questions

**Question 1:** What happens if the student answers "No" to the penalty-clearance question? Why?

**Answer:** The program prints "Failed! The student still has an outstanding penalty". The condition `noPenalty.equalsIgnoreCase("Yes")` is false, so the inner IF is skipped and the outer `else` runs. The guidance sessions are not checked because the penalty check is the first level and must be passed first.

**Question 2:** Explain the meaning of `if (guidanceCount1 >= 8 && guidanceCount2 >= 4) {`.

**Answer:** The condition is true only if the student has at least 8 sessions with Supervisor 1 **and** at least 4 sessions with Supervisor 2. The `&&` (AND) operator needs both sides to be true. If one side is false, the program moves to the next `else if`.

**Question 3:** Describe the full flow of checking the student's requirements from start to finish.

**Answer:**

1. The program reads the penalty status, then the two guidance counts.
2. If the penalty status is "Yes" (upper or lower case is fine), the program goes to the guidance check. If not, it prints the penalty message and finishes.
3. If Supervisor 1 is at least 8 and Supervisor 2 is at least 4, it prints that all requirements are met.
4. Otherwise, if Supervisor 1 is below 8 and Supervisor 2 is below 4, it prints that both are not enough.
5. Otherwise, if only Supervisor 1 is below 8, it prints that message.
6. Otherwise, only Supervisor 2 is below 4, so it prints that message.
7. The message is shown with `System.out.println(message)`.

---

## 2.2 Experiment 2: Logical Operators to Determine Campus WiFi Access

Campus WiFi may be used by students or lecturers whose accounts are not blocked. Access is granted if the user is a student or a lecturer, **and** the account is not blocked. This experiment practices the logical operators `&&` (AND), `||` (OR), and `!` (NOT).

### 2.2.1 Java Program Code

```java
package Week5;
import java.util.Scanner;

public class LogicalOperatorWifiAttendanceNo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        //Variable
        boolean isStudent;
        boolean isLecturer;
        boolean isBlocked;

        //Input
        System.out.print("Is the user a student? (true/false): ");
            isStudent = sc.nextBoolean();
        System.out.print("Is the user a lecturer? (true/false): ");
            isLecturer = sc.nextBoolean();
        System.out.print("Is the account currently blocked? (true/false): ");
            isBlocked = sc.nextBoolean();

        //output and process
       if ((isStudent && isLecturer) && !isBlocked) {
       System.out.println("WiFi access granted");
}        else {
       System.out.println("WiFi access denied");
       sc.close();
}
    }
}
```

### 2.2.2 Running Results / Output Screenshot

> **Insert the screenshots of the test results here.**
>
> `![Output Experiment 2 - Test 1](images/percobaan2-output-test1.png)`

### 2.2.3 Answers to Questions / Reflection Questions

**Question 1:** Explain the function of the `||`, `&&`, and `!` operators in the condition above.

**Answer:** `||` (OR) is true if at least one side is true, so the user only needs to be a student or a lecturer. `&&` (AND) is true only if both sides are true, so the user must be a student or lecturer **and** not blocked. `!` (NOT) reverses a boolean value, so `!isBlocked` is true when the account is not blocked.

**Question 2:** Why can a lecturer still get access when `isStudent = false`?

**Answer:** Because `isStudent || isLecturer` uses OR. If `isStudent` is false but `isLecturer` is true, the result is still true. If the account is not blocked, the whole condition is true (see Test 2).

**Question 3:** Change `||` to `&&`. Run the program again using test data 1 and 2. What happens, and why?

**Answer:** Both tests print "WiFi access denied". With `&&`, the user must be a student **and** a lecturer at the same time. In Test 1 and Test 2 only one of them is true, so the condition becomes false.

**Question 4:** In the expression `isStudent || isLecturer`, when does `isLecturer` not need to be evaluated?

**Answer:** When `isStudent` is true. With short-circuit evaluation, `||` stops when the left side is true, because the result is already true. `isLecturer` is only checked when `isStudent` is false.

**Question 5:** In the expression `(isStudent || isLecturer) && !isBlocked`, when does `!isBlocked` not need to be evaluated?

**Answer:** When `(isStudent || isLecturer)` is false, which means the user is not a student and not a lecturer. With short-circuit evaluation, `&&` stops when the left side is false, because the result is already false.

---

## 2.3 Experiment 3: Nested IF and Logical Operators to Determine Laboratory Access

A student may use the laboratory outside class hours if their status is active and they are not under sanction. If this is met, access is granted when the student has lecturer permission or is a lab assistant. This case combines nested selection with logical operators.

### 2.3.1 Java Program Code

```java
import java.util.Scanner;

public class NestedLabAccessAttendance30 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        boolean isActiveStudent;
        boolean isSanctioned;
        boolean hasLecturerPermit;
        boolean isLabAssistant;

        System.out.print("Is the student active? (true/false): ");
        isActiveStudent = sc.nextBoolean();

        System.out.print("Is the student under sanction? (true/false): ");
        isSanctioned = sc.nextBoolean();

        System.out.print("Does the student have lecturer permission? (true/false): ");
        hasLecturerPermit = sc.nextBoolean();

        System.out.print("Is the student a lab assistant? (true/false): ");
        isLabAssistant = sc.nextBoolean();

        if (isActiveStudent && !isSanctioned) {
            if (hasLecturerPermit || isLabAssistant) {
                System.out.println("Laboratory access granted");
            } else {
                System.out.println("Access denied: lecturer permission or lab assistant status required");
            }
        } else {
            System.out.println("Access denied: student status does not meet the requirement");
            sc.close();
        }
    }
}
```

### 2.3.2 Running Results / Output Screenshot

> **Insert the screenshots of the four required test results here.**
>
> `![Output Experiment 3 - Test 1](images/percobaan3-output-test1.png)`

### 2.3.3 Answers to Questions / Reflection Questions

**Question 1:** Why is the check `hasLecturerPermit || isLabAssistant` placed inside the first IF?

**Answer:** Because it only matters for students who already passed the first check (active and not sanctioned). If a student fails the first check, access is denied anyway, so the permission does not need to be checked.

**Question 2:** Explain the function of the `&&`, `||`, and `!` operators in this program.

**Answer:** `&&` joins two requirements in the first IF: the student must be active **and** not sanctioned. `!` reverses `isSanctioned`, so `!isSanctioned` is true when the student has no sanction. `||` in the second IF gives access if at least one of `hasLecturerPermit` or `isLabAssistant` is true.

**Question 3:** Can the access requirement be written as a single condition: `isActiveStudent && !isSanctioned && (hasLecturerPermit || isLabAssistant)`? Explain whether the final access decision stays the same.

**Answer:** Yes, the final decision stays the same, because access is granted only when all three parts are true. The difference is that a single IF has only one `else`, so it cannot show which requirement failed.

**Question 4:** What is the advantage of using Nested IF in this case, compared to a single IF, if the system needs to show different reasons for denial?

**Answer:** Each level in a Nested IF has its own `else`, so the program can print a specific reason for each level. With a single IF, there is only one `else`, so every denial gets the same message.

**Question 5:** Create one input combination that causes access to be denied at the first level, and one that causes it to be denied at the second level.

**Answer:** **First level:** `isActiveStudent = true, isSanctioned = true, hasLecturerPermit = true, isLabAssistant = true` gives "Access denied: student status does not meet the requirement". **Second level:** `isActiveStudent = true, isSanctioned = false, hasLecturerPermit = false, isLabAssistant = false` gives "Access denied: lecturer permission or lab assistant status required".

---

# 3. Assignment

**Time: 120 minutes**

## 3.1 Task 1: Bookstore Discount System

### Exercise 2

- Every Wednesday, a bookstore gives discounts to its customers depending on the type of book purchased.
- A 10% discount is given if the book purchased is a dictionary; an additional 2% discount is given if more than 2 books are purchased.
- A 7% discount is given if the book purchased is a novel; an additional 2% discount is given if more than 3 novels are purchased, while if 3 or fewer novels are purchased, an additional 1% discount is given.
- Customers get a 5% discount on books other than dictionaries and novels if more than 3 books are purchased.
- Create a flowchart (use logical operators) to determine the total amount to be paid if the input is the type and number of books, and the output is the discount amount.

### Task 1

Implement the flowchart you created in Exercise 2 of Week 6 for the bookstore discount system as a Java program. The program must use nested selection statements (Nested IF). Use logical operators where needed.

### 3.1.1 Java Program Code

```java
import java.util.Scanner;

public class Task1BookstoreDiscountAttendance30 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the type of book (dictionary/novel/other): ");
        String bookType = sc.nextLine();

        System.out.print("Enter the number of books: ");
        int bookCount = sc.nextInt();

        System.out.print("Enter the price of one book: ");
        double pricePerBook = sc.nextDouble();

        double discountRate;
        double totalPrice;
        double discountAmount;
        double totalPayment;

        totalPrice = bookCount * pricePerBook;

        if (bookType.equalsIgnoreCase("dictionary")) {
            if (bookCount > 2) {
                discountRate = 0.12;
            } else {
                discountRate = 0.10;
            }
        } else if (bookType.equalsIgnoreCase("novel")) {
            if (bookCount > 3) {
                discountRate = 0.09;
            } else {
                discountRate = 0.08;
            }
        } else {
            if (bookCount > 3) {
                discountRate = 0.05;
            } else {
                discountRate = 0.00;
            }
        }

        discountAmount = totalPrice * discountRate;
        totalPayment = totalPrice - discountAmount;

        System.out.println();
        System.out.println("===== BOOKSTORE DISCOUNT =====");
        System.out.println("Book type       : " + bookType);
        System.out.println("Number of books : " + bookCount);
        System.out.println("Total price     : " + totalPrice);
        System.out.println("Discount rate   : " + (discountRate * 100) + "%");
        System.out.println("Discount amount : " + discountAmount);
        System.out.println("Total payment   : " + totalPayment);
        sc.close();
    }
}
```

### 3.1.2 Running Results / Output Screenshot

> **Insert one screenshot of the program output here.**
>
> `![Output Task 1](images/percobaan4-output.png)`

---

## 3.2 Task 2: Lab-Assistant Candidate Selection System

Write a Java program for a lab-assistant candidate selection system based on the following rules:

a. A student may take part in the selection if their status is active and they are not currently under academic sanction.

b. If this requirement is met, the student must also meet the next requirement: a minimum grade of 80 in Basic Programming, or a programming competency certificate.

c. If both requirements are met, the student will be called for an interview. The student is accepted as an assistant if the interview score is at least 75.

d. The program must show the reason if the student fails at any stage of the selection.

e. Use nested selection and logical operators. Save the file as `Task2AssistantSelectionAttendanceNo.java`.

### 3.2.1 Java Program Code

```java
import java.util.Scanner;

public class Task2AssistantSelectionAttendance30 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Is the student active? (true/false): ");
        boolean isActive = sc.nextBoolean();

        System.out.print("Is the student under academic sanction? (true/false): ");
        boolean isSanctioned = sc.nextBoolean();

        System.out.print("Enter the Basic Programming grade: ");
        int grade = sc.nextInt();

        System.out.print("Does the student have a programming certificate? (true/false): ");
        boolean hasCertificate = sc.nextBoolean();

        if (isActive && !isSanctioned) {
            if (grade >= 80 || hasCertificate) {
                System.out.print("Enter the interview score: ");
                int interviewScore = sc.nextInt();

                if (interviewScore >= 75) {
                    System.out.println("Accepted as an assistant");
                } else {
                    System.out.println("Failed! The interview score is below 75");
                }
            } else {
                System.out.println("Failed! Grade is below 80 and no programming certificate");
            }
        } else {
            System.out.println("Failed! The student is not active or is under academic sanction");
            sc.close();
        }
    }
}
```

### 3.2.2 Running Results / Output Screenshot

> **Insert the screenshot of the program output here.**
>
> `![Output Task 2](images/task2-output.png)`
