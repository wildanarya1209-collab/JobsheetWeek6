# JOBSHEET 7 - LOOPS 1

## Student Identity

- **Name:** Wildan Arya Indradiansyah
- **Student ID (NIM):** 264107020257
- **Class / Attendance No.:** TI-1I / 30

---

# 1. Objectives

The objectives of this practicum are:

1. Students can explain the syntax for writing loop programs (`for`, `while`, and `do-while`).
2. Students can implement loop flowcharts using the Java programming language.

---

# 2. Labs Activities

## 2.1 Experiment 1: Student Grades Case Study in SIAKAD - FOR Loop

In the Academic Information System (SIAKAD), a lecturer enters the quiz scores of 10 students in one class. The program reads the score of each student, then finds and shows the highest and lowest scores. Because the number of students is fixed (10), a `for` loop is used.

### 2.1.1 Java Program Code

```java
import java.util.Scanner;

public class SiakadForAttendance30 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Variable
        double score, highest = 0, lowest = 100;

        // Input and process
        for (int i = 1; i <= 10; i++) {
            System.out.print("Enter score for student " + i + ": ");
            score = sc.nextDouble();
            if (score > highest) {
                highest = score;
            }
            if (score < lowest) {
                lowest = score;
            }
        }

        // Output
        System.out.println("Highest score: " + highest);
        System.out.println("Lowest score: " + lowest);
        sc.close();
    }
}
```

### 2.1.2 Running Results / Output Screenshot

> **Insert the screenshot of the program output here.** *(To be completed - no screenshot has been provided yet.)*

Expected output (example only, taken from the job sheet; not yet confirmed by running the program):

```text
Enter score for student 1: 76.5
Enter score for student 2: 82.3
Enter score for student 3: 62.1
Enter score for student 4: 88.4
Enter score for student 5: 65.9
Enter score for student 6: 67.9
Enter score for student 7: 90.1
Enter score for student 8: 55.3
Enter score for student 9: 73.7
Enter score for student 10: 78.6
Highest score: 90.1
Lowest score: 55.3
```

### 2.1.3 Answers to Questions / Reflection Questions

**Question 1:** Identify and indicate each component of the FOR loop in the program code of Experiment 1.

**Answer:** The loop is `for (int i = 1; i <= 10; i++) { ... }`. Its components are:

| Component | Code | Meaning |
|---|---|---|
| Initialization | `int i = 1` | Creates the counter `i` and starts it at 1. It runs once. |
| Condition | `i <= 10` | The loop continues while this is true. It is checked before every round. |
| Update | `i++` | Adds 1 to `i` after every round. |
| Body | The code inside `{ }` | Reads the score and checks the highest and lowest values. |

**Question 2:** Why is the variable `highest` initialized to 0 and the variable `lowest` initialized to 100? What happens if `highest` is initialized to 100 and `lowest` is initialized to 0?

**Answer:** A score is between 0 and 100. If `highest` starts at 0, any score is bigger than or equal to 0, so the first score can replace it. If `lowest` starts at 100, any score is smaller than or equal to 100, so the first score can replace it.
If `highest = 100` and `lowest = 0`, then `score > highest` and `score < lowest` can never be true for scores from 0 to 100. The values never change, so the program always shows "Highest score: 100.0" and "Lowest score: 0.0", which is wrong.

**Question 3:** Explain the function and workflow of the following code snippet.

```java
if (score > highest) {
    highest = score;
}
if (score < lowest) {
    lowest = score;
}
```

**Answer:** This code finds the highest and lowest scores.

1. The first `if` compares the new `score` with `highest`. If the new score is bigger, it becomes the new `highest`.
2. The second `if` compares the new `score` with `lowest`. If the new score is smaller, it becomes the new `lowest`.
3. These are two separate `if` statements, so both checks are done for every score.
4. The code runs once in every round of the loop. After 10 rounds, `highest` and `lowest` hold the biggest and smallest scores.

**Question 4:** Modify the program to count how many students pass and how many students fail, based on the passing threshold (minimum score of 60). Display the number of students who pass and fail after displaying the highest and lowest scores.

**Answer:** Two new variables, `passCount` and `failCount`, are added. A student passes if the score is 60 or more. The changes are marked with comments.

```java
import java.util.Scanner;

public class SiakadForAttendance30 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        double score, highest = 0, lowest = 100;
        int passCount = 0;  // new: number of students who pass
        int failCount = 0;  // new: number of students who fail

        for (int i = 1; i <= 10; i++) {
            System.out.print("Enter score for student " + i + ": ");
            score = sc.nextDouble();
            if (score > highest) {
                highest = score;
            }
            if (score < lowest) {
                lowest = score;
            }
            // new: count pass and fail
            if (score >= 60) {
                passCount++;
            } else {
                failCount++;
            }
        }

        System.out.println("Highest score: " + highest);
        System.out.println("Lowest score: " + lowest);
        System.out.println("Number of students who pass: " + passCount);  // new
        System.out.println("Number of students who fail: " + failCount);  // new
        sc.close();
    }
}
```

Expected result (example only, not yet run): with the scores from the job sheet, only 55.3 is below 60, so the program should show 9 students pass and 1 student fails.

**Question 5:** Commit and push the program code to GitHub.

**Answer:** *(To be completed - add the GitHub repository link `programming-fundamentals-jobsheet7` here after the push.)*

---

## 2.2 Experiment 2: Student Grades Case Study in SIAKAD - WHILE Loop

A lecturer enters the scores of several students to find their letter grades. The number of students is typed by the user. If the score is invalid (negative or more than 100), the program ignores it and asks again. Valid scores are changed into letter grades: A (80 < score <= 100), B+ (73 < score <= 80), B (65 < score <= 73), C+ (60 < score <= 65), C (50 < score <= 60), D (39 < score <= 50), and E (score <= 39). A `while` loop is used because the number of rounds depends on the user's input.

### 2.2.1 Java Program Code

```java
import java.util.Scanner;

public class SiakadWhileAttendance30 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Variable
        int score, studentCount;
        int i = 0;

        // Input
        System.out.print("Enter the number of students: ");
        studentCount = sc.nextInt();

        // Process and output
        while (i < studentCount) {
            System.out.print("Enter score for student " + (i + 1) + ": ");
            score = sc.nextInt();

            if (score < 0 || score > 100) {
                System.out.println("Invalid score. Please enter a valid score!");
                continue;
            }

            if (score > 80 && score <= 100) {
                System.out.println("The grade of student " + (i + 1) + " is A");
            } else if (score > 73 && score <= 80) {
                System.out.println("The grade of student " + (i + 1) + " is B+");
            } else if (score > 65 && score <= 73) {
                System.out.println("The grade of student " + (i + 1) + " is B");
            } else if (score > 60 && score <= 65) {
                System.out.println("The grade of student " + (i + 1) + " is C+");
            } else if (score > 50 && score <= 60) {
                System.out.println("The grade of student " + (i + 1) + " is C");
            } else if (score > 39 && score <= 50) {
                System.out.println("The grade of student " + (i + 1) + " is D");
            } else {
                System.out.println("The grade of student " + (i + 1) + " is E");
            }
            i++;
        }
        sc.close();
    }
}
```

### 2.2.2 Running Results / Output Screenshot

> **Insert the screenshot of the program output here.** *(To be completed - no screenshot has been provided yet.)*

Expected output (example only, taken from the job sheet; not yet confirmed by running the program):

```text
Enter the number of students: 5
Enter score for student 1: 85
The grade of student 1 is A
Enter score for student 2: 63
The grade of student 2 is C+
Enter score for student 3: 101
Invalid score. Please enter a valid score!
Enter score for student 3: 23
The grade of student 3 is E
Enter score for student 4: -15
Invalid score. Please enter a valid score!
Enter score for student 4: 70
The grade of student 4 is B
Enter score for student 5: 55
The grade of student 5 is C
```

### 2.2.3 Answers to Questions / Reflection Questions

**Question 1:** In the code snippet `if (score < 0 || score > 100) { ... continue; }`, determine the meaning and purpose of: a. `score < 0 || score > 100`, and b. `continue`.

**Answer:**

- **a.** `score < 0 || score > 100` checks if the score is invalid. The `||` (OR) operator is true if at least one side is true. So the condition is true if the score is below 0 **or** above 100. Only scores from 0 to 100 are valid.
- **b.** `continue` skips the rest of the loop body and goes back to check the `while` condition. Here, it stops the program from giving a grade to an invalid score. Because `i++` is skipped, `i` does not change, so the program asks for the same student's score again.

**Question 2:** Why is the `i++` statement written at the end of the WHILE loop? What happens if it is written at the beginning of the WHILE loop?

**Answer:** `i++` is at the end so that `i` increases only after a valid score has been graded. When the score is invalid, `continue` skips `i++`, so the same student is asked again.
If `i++` is written at the beginning, `i` increases before the score is read. The student number shown with `(i + 1)` would be wrong (it would start from 2), and an invalid score would still use up one round of the loop. So some students would not get a grade.

**Question 3:** If the number of students entered is 19, how many times will the WHILE loop run?

**Answer:** If all the scores are valid, the loop runs 19 times, with `i` from 0 to 18. When `i` becomes 19, the condition `i < studentCount` is false and the loop stops. Each invalid score adds one extra round, because `continue` goes back to the start of the loop without increasing `i`.

**Question 4:** Modify the program so that, if a student receives grade A, the program displays an additional message "Well done, keep up the good work!"

**Answer:** One extra `System.out.println` is added inside the grade A branch. The other parts of the program stay the same.

```java
if (score > 80 && score <= 100) {
    System.out.println("The grade of student " + (i + 1) + " is A");
    System.out.println("Well done, keep up the good work!");  // new
} else if (score > 73 && score <= 80) {
```

**Question 5:** Commit and push the program code to GitHub.

**Answer:** *(To be completed - add the GitHub repository link here after the push.)*

---

## 2.3 Experiment 3: Cafe Transaction Case Study - DO-WHILE Loop

At a cafe, a cashier processes the transactions of several customers. A customer can buy coffee (Rp 12,000), tea (Rp 7,000), and bread (Rp 20,000). The cashier keeps entering the quantities for each customer. When the cashier types "cancel" as the customer name, the program stops. A `do-while` loop is used because the program must ask for input at least once.

### 2.3.1 Java Program Code

```java
import java.util.Scanner;

public class CafeDoWhileAttendance30 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Variable
        int coffee, tea, bread, totalPrice;
        String customerName;
        int coffeePrice = 12000;
        int teaPrice = 7000;
        int breadPrice = 20000;

        // Input, process, and output
        do {
            System.out.print("Enter customer name (type 'cancel' to exit): ");
            customerName = sc.nextLine();
            if (customerName.equalsIgnoreCase("cancel")) {
                System.out.println("Transaction canceled.");
                break;
            }
            System.out.print("Coffee quantity: ");
            coffee = sc.nextInt();
            System.out.print("Tea quantity: ");
            tea = sc.nextInt();
            System.out.print("Bread quantity: ");
            bread = sc.nextInt();
            totalPrice = (coffee * coffeePrice) + (tea * teaPrice) + (bread * breadPrice);
            System.out.println("Total amount to pay: Rp " + totalPrice);
            sc.nextLine(); // clear the newline character from the input buffer
        } while (true);

        System.out.println("All transactions completed.");
        sc.close();
    }
}
```

### 2.3.2 Running Results / Output Screenshot

> **Insert the screenshot of the program output here.** *(To be completed - no screenshot has been provided yet.)*

Expected output (example only, taken from the job sheet; not yet confirmed by running the program):

```text
Enter customer name (type 'cancel' to exit): Rena
Coffee quantity: 3
Tea quantity: 0
Bread quantity: 1
Total amount to pay: Rp 56000
Enter customer name (type 'cancel' to exit): Yuni
Coffee quantity: 1
Tea quantity: 4
Bread quantity: 2
Total amount to pay: Rp 80000
Enter customer name (type 'cancel' to exit): CANCEL
Transaction canceled.
All transactions completed.
```

### 2.3.3 Answers to Questions / Reflection Questions

**Question 1:** In this DO-WHILE loop, if the first customer name entered is "cancel", how many times is the loop executed?

**Answer:** The loop body runs 1 time. A `do-while` loop always runs the body once before it checks anything. In that one round, the name "cancel" is read, the program prints "Transaction canceled.", and `break` ends the loop.

**Question 2:** State the stopping condition used in this DO-WHILE loop.

**Answer:** The loop stops when the user types "cancel" (upper or lower case is fine, because of `equalsIgnoreCase`). Then the `break` statement ends the loop. The `while` condition itself is always `true`.

**Question 3:** What is the function of using the value `true` in the DO-WHILE condition?

**Answer:** Using `true` makes the loop repeat forever, because the condition never becomes false. This is useful when the number of customers is not known. The loop only ends when `break` is run.

**Question 4:** Why does this DO-WHILE loop still run even though it has no initialization and update components?

**Answer:** A `do-while` loop only needs a condition. Initialization and update are used in a `for` loop to control a counter, but this program has no counter. The loop is controlled by the condition `true` and stopped by the user's input ("cancel") with `break`.

---

# 3. Assignment

**Time: 120 minutes**

## 3.1 Task 1: Cinema Ticket Sales

A cinema manager wants a program to calculate the total ticket sales in one day. A ticket costs Rp 50,000. The program calculates the total number of tickets sold and the total revenue, with these rules:

- If a customer buys more than 4 tickets, the customer gets a 10% discount.
- If a customer buys more than 10 tickets, the customer gets a 15% discount.
- If the ticket quantity is invalid (negative), the program ignores it and asks again.

The job sheet does not say how the program ends, so this program stops when the cashier enters 0 (this is an assumption).

### 3.1.1 Java Program Code

```java
import java.util.Scanner;

public class Task1CinemaTicketAttendance30 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Variable
        int ticketPrice = 50000;
        int ticketCount;
        int discountPercent;
        int totalPrice, discountAmount, payment;
        int totalTickets = 0;
        int totalRevenue = 0;

        // Input, process, and output
        while (true) {
            System.out.print("Enter the number of tickets (0 to finish): ");
            ticketCount = sc.nextInt();

            if (ticketCount < 0) {
                System.out.println("Invalid quantity. Please enter again!");
                continue;
            }
            if (ticketCount == 0) {
                break;
            }

            if (ticketCount > 10) {
                discountPercent = 15;
            } else if (ticketCount > 4) {
                discountPercent = 10;
            } else {
                discountPercent = 0;
            }

            totalPrice = ticketCount * ticketPrice;
            discountAmount = totalPrice * discountPercent / 100;
            payment = totalPrice - discountAmount;

            System.out.println("Discount: " + discountPercent + "%");
            System.out.println("Amount to pay: Rp " + payment);

            totalTickets += ticketCount;
            totalRevenue += payment;
        }

        System.out.println("Total tickets sold: " + totalTickets);
        System.out.println("Total revenue: Rp " + totalRevenue);
        sc.close();
    }
}
```

**Explanation:**

- **Variables:** `ticketCount` is the input. `totalTickets` and `totalRevenue` keep the totals for the day.
- **Loop:** `while (true)` repeats until the cashier enters 0 (`break`).
- **Invalid input:** a negative quantity prints an error and `continue` asks again.
- **Discount:** more than 10 tickets gives 15%, more than 4 tickets gives 10%, otherwise no discount. The 15% check is first so that 11 or more tickets do not get 10%.

### 3.1.2 Running Results / Output Screenshot

> **Insert the screenshot of the program output here.** *(To be completed - the program has not been run yet.)*

Expected output (example only, calculated from the code; not yet confirmed by running the program):

```text
Enter the number of tickets (0 to finish): 3
Discount: 0%
Amount to pay: Rp 150000
Enter the number of tickets (0 to finish): -2
Invalid quantity. Please enter again!
Enter the number of tickets (0 to finish): 5
Discount: 10%
Amount to pay: Rp 225000
Enter the number of tickets (0 to finish): 12
Discount: 15%
Amount to pay: Rp 510000
Enter the number of tickets (0 to finish): 0
Total tickets sold: 20
Total revenue: Rp 885000
```

---

## 3.2 Task 2: Parking Fee Flowchart

A parking lot operator wants to calculate the total parking fee of several vehicles. The rate is Rp 3,000 per hour for cars and Rp 2,000 per hour for motorcycles. The program keeps asking for input as long as the vehicle type is not 0. The program follows the flowchart in the job sheet:

1. Start, then set `type`, `duration`, and `total = 0`.
2. Input the vehicle type (1 = Car, 2 = Motorcycle, 0 = Exit).
3. If `type == 1` or `type == 2`, input the duration. If `type == 1`, then `total += duration * 3000`, otherwise `total += duration * 2000`.
4. Repeat while `type != 0`.
5. Output the total, then End.

### 3.2.1 Java Program Code

```java
import java.util.Scanner;

public class Task2ParkingFeeAttendance30 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Variable
        int type, duration;
        int total = 0;

        // Input and process
        do {
            System.out.print("Enter vehicle type (1 = Car, 2 = Motorcycle, 0 = Exit): ");
            type = sc.nextInt();

            if (type == 1 || type == 2) {
                System.out.print("Enter parking duration (hours): ");
                duration = sc.nextInt();

                if (type == 1) {
                    total += duration * 3000;
                } else {
                    total += duration * 2000;
                }
            }
        } while (type != 0);

        // Output
        System.out.println("Total parking fee: Rp " + total);
        sc.close();
    }
}
```

**Explanation:**

- **Loop:** a `do-while` loop is used, as in the flowchart, because the vehicle type must be asked at least once.
- **Condition:** `type == 1 || type == 2` means only cars and motorcycles are processed. Other numbers (except 0) are ignored and the program asks again.
- **Fee:** a car adds `duration * 3000` and a motorcycle adds `duration * 2000` to `total`.
- **Stop:** the loop ends when `type` is 0, then the total is shown.

### 3.2.2 Running Results / Output Screenshot

> **Insert the screenshot of the program output here.** *(To be completed - the program has not been run yet.)*

Expected output (example only, calculated from the code; not yet confirmed by running the program):

```text
Enter vehicle type (1 = Car, 2 = Motorcycle, 0 = Exit): 1
Enter parking duration (hours): 2
Enter vehicle type (1 = Car, 2 = Motorcycle, 0 = Exit): 2
Enter parking duration (hours): 3
Enter vehicle type (1 = Car, 2 = Motorcycle, 0 = Exit): 0
Total parking fee: Rp 12000
```
