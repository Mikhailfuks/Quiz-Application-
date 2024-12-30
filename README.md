import random

questions = {
    "What is the capital of France?": "Paris",
    "What is the highest mountain in the world?": "Mount Everest",
    "What is the largest ocean on Earth?": "Pacific Ocean",
    "What is the chemical symbol for water?": "H2O",
    "What is the name of Earth's only natural satellite?": "The Moon"
}

def ask_question(question, answer):
    """Asks a question and checks the user's answer."""
    user_answer = input(f"{question} ")
    return user_answer.lower() == answer.lower()


def run_quiz():
    """Runs the quiz and calculates the score."""
    score = 0
    random_questions = random.sample(list(questions.items()), len(questions)) #Shuffle questions
    for question, answer in random_questions:
        if ask_question(question, answer):
            print("Correct!")
            score += 1
        else:
            print(f"Incorrect. The answer is {answer}")
    print(f"\nYou got {score} out of {len(questions)} questions correct.")


if __name__ == "__main__":
    print("Welcome to the Quiz!")
    run_quiz()

import csv
import random

def load_questions_from_csv(filename="questions.csv"):
    """Loads questions from a CSV file."""
    questions = {}
    with open(filename, "r", encoding="utf-8") as csvfile:
        reader = csv.DictReader(csvfile)
        for row in reader:
            questions[row["question"]] = row["answer"]
    return questions


# ... rest of the code (ask_question, run_quiz) remains largely the same ...

if __name__ == "__main__":
    questions = load_questions_from_csv() #Load from CSV instead of hardcoded dictionary
    print("Welcome to the Quiz!")
    run_quiz()
