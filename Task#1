import java.util.ArrayList;

import java.util.Scanner;

//1)GradeCalculator Class:

//ArrayList<Double> grades;: A private instance variable to store a list of grades.
//Constructor (GradeCalculator): Initializes the grades ArrayList when an object of GradeCalculator is created.
 class GradeCalculator {
     private ArrayList<Double> grades;
     public GradeCalculator() {
         this.grades = new ArrayList<>();}

    //2)addGrade Method:

    //addGrade(double grade): This method takes a grade as a parameter and adds it to the grades list.
     public void addGrade(double grade) {
         grades.add(grade);}

    //3)calculateAverage Method:

    //calculateAverage(): This method calculates and returns the average of all the grades in the grades list.
    //It first checks if the list is empty; if so, it returns 0 to avoid division by zero.
    //It then sums all the grades and divides the sum by the number of grades to get the average.
     public double calculateAverage() {

         if (grades.isEmpty()) {
             return 0;}
         double sum = 0;
         for (int i = 0; i < grades.size(); i++) {
             sum =sum+ grades.get(i);}
         return sum / grades.size();}

    //4)getHighestGrade Method:

    //getHighestGrade(): This method finds and returns the highest grade in the grades list.
    //It checks if the list is empty; if so, it returns 0.
    //It then iterates through the list, comparing each grade to the current highest grade and updating the highest grade when a larger grade is found.
     public double getHighestGrade() {

         if (grades.isEmpty()) {
             return 0;
         }
         double highest = 0;
         for (int i = 0; i < grades.size(); i++) {
             if (grades.get(i) > highest) {
                 highest = grades.get(i);
             }}
         return highest;}
    //5)getLowestGrade Method

    //getLowestGrade(): This method finds and returns the lowest grade in the grades list.
    //It checks if the list is empty; if so, it returns 0.
    //It initializes lowest to 100, then iterates through the list, updating lowest when a smaller grade is found.
     public double getLowestGrade() {
         if (grades.isEmpty()) {
             return 0;
         }
         double lowest = 100;
         for (int i = 0; i < grades.size(); i++) {
             if (grades.get(i) < lowest) {
                 lowest = grades.get(i);
             }}
         return lowest;
     }}
//6)Main Class and Method:

//Scanner scanner = new Scanner(System.in);: This creates a Scanner object to read user input.
//GradeCalculator gradeCalculator = new GradeCalculator();: This creates a GradeCalculator object to manage grades.
//while (true): This loop runs indefinitely until the user types "finish".
//Inside the loop, the program prompts the user to enter a grade. If the user types "finish", the loop breaks.
//The program attempts to parse the user input as a double and adds it to the grade list using gradeCalculator.addGrade(grade). If the input is not a valid number, it catches the NumberFormatException and prints an error message.

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        GradeCalculator gradeCalculator = new GradeCalculator();
        String input;
        while (true) {
            System.out.print("Enter a numeric grade/type 'finish' to close:");
            input = scanner.nextLine();
            if (input.equalsIgnoreCase("finish")) {
                break;}
            try {
                double grade = Double.parseDouble(input);
                gradeCalculator.addGrade(grade);
            } catch (NumberFormatException e) {
                System.out.println("Error!! please enter a numeric grade");
            }}

    //7)Calculating and Displaying Results:

        //calculateAverage(), getHighestGrade(), and getLowestGrade(): These methods are called to calculate the average, highest, and lowest grades, respectively.
        //If no grades were entered, the program prints "No grades entered". Otherwise, it prints the average, highest, and lowest grades.
        //scanner.close();: This closes the scanner to free up resources
        double average = gradeCalculator.calculateAverage();
        double highest = gradeCalculator.getHighestGrade();
        double lowest = gradeCalculator.getLowestGrade();
        if (gradeCalculator.calculateAverage() == 0) {
            System.out.println("No grades entered");
        } else {
            System.out.println("Average grade:" +average);
            System.out.println("Highest grade:" +highest);
            System.out.println("Lowest grade:" +lowest);
        }
        scanner.close();
    }}
