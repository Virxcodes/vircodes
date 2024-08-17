import java.util.Scanner;

class Question {
    private String questionText;
    private String[] options;
    private int correctAnswer;

    public Question(String questionText, String[] options, int correctAnswer) {
        this.questionText = questionText;
        this.options = options;
        this.correctAnswer = correctAnswer;
    }

    public String getQuestionText() {
        return questionText;
    }

    public String[] getOptions() {
        return options;
    }

    public boolean isCorrect(int userAnswer) {
        return userAnswer == correctAnswer;
    }
}

class Quiz {
    private Question[] questions;
    private int score;

    public Quiz(Question[] questions) {
        this.questions = questions;
        this.score = 0;
    }

    public void start() {
        Scanner scanner = new Scanner(System.in);

        for (Question question : questions) {
            System.out.println(question.getQuestionText());
            String[] options = question.getOptions();
            for (int i = 0; i < options.length; i++) {
                System.out.println((i + 1) + ". " + options[i]);
            }

            int userAnswer = scanner.nextInt();

            if (question.isCorrect(userAnswer)) {
                System.out.println("Correct!");
                score++;
            } else {
                System.out.println("Wrong!");
            }
            System.out.println();
        }

        System.out.println("Your final score is: " + score + "/" + questions.length);
        scanner.close();
    }
}

public class Main {
    public static void main(String[] args) {
        Question q1 = new Question("What is the capital of France?", 
                                   new String[]{"Berlin", "Paris", "Madrid", "Rome"}, 2);
        Question q2 = new Question("Which planet is known as the Red Planet?", 
                                   new String[]{"Earth", "Mars", "Jupiter", "Venus"}, 2);
        Question q3 = new Question("What is the largest mammal?", 
                                   new String[]{"Elephant", "Blue Whale", "Giraffe", "Human"}, 2);

        Question[] questions = {q1, q2, q3};
        Quiz quiz = new Quiz(questions);

        quiz.start();
    }
}
