import java.util.ArrayList;
import java.util.Scanner;
public class StudentGradeProgram {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Integer> grades = new ArrayList<>();
        String input;
        while (true) {
            System.out.print("Enter a grade (or type 'done' to finish): ");
            input = scanner.nextLine();
            if (input.equalsIgnoreCase("done")) {
                break;
            }
            try {
                int grade = Integer.parseInt(input);
                if (grade < 0 || grade > 100) {
                    System.out.println("Please enter a grade between 0 and 100.");
                } else {
                    grades.add(grade);
                }
            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a numeric value.");
            }
        }
        if (grades.isEmpty()) {
            System.out.println("No grades entered.");
        } else {
            double average = calculateAverage(grades);
            int highest = findHighest(grades);
            int lowest = findLowest(grades);
            
            System.out.println("Average grade: " + average);
            System.out.println("Highest grade: " + highest);
            System.out.println("Lowest grade: " + lowest);
        }
        scanner.close();
    }
    private static double calculateAverage(ArrayList<Integer> grades) {
        int sum = 0;
        for (int grade : grades) {
            sum += grade;
        }
        return (double) sum / grades.size();
    }
    private static int findHighest(ArrayList<Integer> grades) {
        int highest = grades.get(0);
        for (int grade : grades) {
            if (grade > highest) {
                highest = grade;
            }
        }
        return highest;
    }
    private static int findLowest(ArrayList<Integer> grades) {
        int lowest = grades.get(0);
        for (int grade : grades) {
            if (grade < lowest) {
                lowest = grade;
            }
        }
        return lowest;
    }
}
