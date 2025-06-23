# Number-game-
import java.util.Scanner;

public class Main {

    // Method to get marks input
    public static int[] collectMarks(int subjectCount, Scanner scanner) {
        int[] scores = new int[subjectCount];

        for (int i = 0; i < subjectCount; i++) {
            System.out.print("🔹 Enter marks for Subject " + (i + 1) + ": ");
            int mark = scanner.nextInt();

            // Validate input
            while (mark < 0 || mark > 100) {
                System.out.print("❌ Invalid! Marks should be between 0 and 100. Try again: ");
                mark = scanner.nextInt();
            }

            scores[i] = mark;
        }
        return scores;
    }

    // Method to calculate grade based on average
    public static String evaluateGrade(double avg) {
        if (avg >= 90) return "🌟 A+";
        else if (avg >= 80) return "🎖 A";
        else if (avg >= 70) return "🏅 B";
        else if (avg >= 60) return "📘 C";
        else if (avg >= 50) return "📗 D";
        else return "❌ F (Fail)";
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("🎓 Welcome to the Student Marks Analyzer");

        System.out.print("📚 Enter number of subjects: ");
        int subjectCount = scanner.nextInt();

        int[] marks = collectMarks(subjectCount, scanner);

        int total = 0;
        for (int mark : marks) {
            total += mark;
        }

        double average = (double) total / subjectCount;
        String finalGrade = evaluateGrade(average);

        // Displaying final results
        System.out.println("\n📊 -------- REPORT CARD --------");
        System.out.println("🧮 Total Marks: " + total + " / " + (subjectCount * 100));
        System.out.printf("📈 Average Percentage: %.2f%%\n", average);
        System.out.println("🎯 Grade Achieved: " + finalGrade);
        System.out.println("👍 Keep up the good work!");

        scanner.close();
    }
}
