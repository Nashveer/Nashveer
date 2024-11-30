# Quiz Game

def check_answer(user_answer, correct_answer):
    if user_answer.lower() == correct_answer.lower():
        return True
    else:
        return False

def ask_question(question, options, correct_answer):
    print(question)
    for i, option in enumerate(options, 1):
        print(f"{i}. {option}")
    user_choice = input("Choose the correct option (1-4): ")

    try:
        user_choice = int(user_choice)
        if user_choice < 1 or user_choice > 4:
            print("Please choose a number between 1 and 4.")
            return False
        return check_answer(options[user_choice - 1], correct_answer)
    except ValueError:
        print("Please enter a valid number.")
        return False

def main():
    score = 0
    questions = [
        {
            "question": "What is the capital of France?",
            "options": ["Berlin", "Madrid", "Paris", "Rome"],
            "answer": "Paris"
        },
        {
            "question": "Who wrote 'Hamlet'?",
            "options": ["Shakespeare", "Dickens", "Hemingway", "Austen"],
            "answer": "Shakespeare"
        },
        {
            "question": "What is 5 + 7?",
            "options": ["10", "11", "12", "13"],
            "answer": "12"
        },
        {
            "question": "Which planet is known as the Red Planet?",
            "options": ["Earth", "Mars", "Venus", "Jupiter"],
            "answer": "Mars"
        }
    ]

    print("Welcome to the Quiz Game!")
    print("Try to answer all questions correctly.\n")

    for q in questions:
        if ask_question(q["question"], q["options"], q["answer"]):
            print("Correct!\n")
            score += 1
        else:
            print(f"Wrong! The correct answer was {q['answer']}.\n")

    print(f"Your final score is {score}/{len(questions)}.")
    if score == len(questions):
        print("Congratulations, you got a perfect score!")
    else:
        print("Better luck next time!")

if __name__ == "__main__":
    main()
