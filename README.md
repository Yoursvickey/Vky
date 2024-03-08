 <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Quiz Game</title>
<style>
   body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        background-image: url('background-image.jpg'); /* Replace 'background-image.jpg' with the path to your background image */
        background-size: cover;
        background-repeat: no-repeat;
    }
    .container {
        max-width: 600px;
        margin: 50px auto;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 5px;
        background-color: rgba(255, 255, 255, 0.8); /* Adding transparency to the background color */
    }
    h1, h2 {
        text-align: center;
    }
    .question {
        margin-bottom: 20px;
    }
    .options {
        display: grid;
        grid-template-columns: auto auto;
        gap: 10px;
    }
    button {
        padding: 10px 20px;
        border: none;
        border-radius: 5px;
        background-color: #007bff;
        color: #fff;
        cursor: pointer;
    }
    button:hover {
        background-color: #0056b3;
    }
</style>
</head>
<body>
<div class="container">
    <h1>Quiz Game</h1>
    <div id="quiz">
        <div class="question"></div>
        <div class="options"></div>
        <button id="submit">Submit</button>
    </div>
    <div id="result"></div>
</div>
<script>
    const quiz = [
        {
            question: "Which word does not belong to the others?",
            options: ["Inch", "Kilogram", "Centimetre", "Yard"],
            answer: "b"
        },
        {
            question: "If the code for LOTUS is 14983 and the code for TULIPS is 981543, then what is the code for SPOIL?",
            options: ["28729", "56738", "34451", "71892"],
            answer: "c"
        },
        {
            question: "How many Is are there in the given sequence which are immediately preceded by 7 and immediately followed by 6? 711451765198716765321678",
            options: ["3", "2", "1", "None of these"],
            answer: "b"
        },
        {
            question: "Which of the following Venn diagrams best represents the relationship between ink, paper, and stationery?",
            options: ["A diagram showing three circles partially overlapping.", "A diagram showing three circles completely separate.", "A diagram showing two circles completely overlapping and one separate.", "A diagram showing one circle completely overlapping the other two."],
            answer: "a"
        },
        {
            question: "Identify the odd one out of the following colors: yellow, blue, indigo, orange, violet, pink",
            options: ["Pink", "Indigo", "Yellow", "Orange"],
            answer: "a"
        },
        {
            question: "If Ear: Otolaryngologist, then Eye: ?",
            options: ["Dentist", "Ophthalmologist", "Cardiologist", "None of these"],
            answer: "b"
        },
        {
            question: "A family consists of six members A, B, C, H, I, and J. A and C are a married couple. B is the son of C but C is not the mother of B. I is the brother of C. H is the daughter of A. J is the brother of A. How many males are there in the family?",
            options: ["1", "2", "3", "4"],
            answer: "d"
        },
        {
            question: "If + means divide, * means multiply, - means subtract, and x means add, then which of the following equations is true?",
            options: ["5+20-10-6-1-20", "5-2+10×7+1=7", "5+20-10+6×1=5"],
            answer: "b"
        },
        {
            question: "Pick the odd one out.",
            options: ["BCEH", "RSUX", "JKNQ", "MNPS"],
            answer: "c"
        },
        {
            question: "My mother has two sisters. The youngest sister has two daughters and one son. The eldest one has one daughter and two sons and the remaining one has three daughters. If my mother has four nieces, how many cousins do I have?",
            options: ["6", "4", "7", "5"],
            answer: "b"
        }
    ];

    const quizContainer = document.getElementById('quiz');
    const questionContainer = document.querySelector('.question');
    const optionsContainer = document.querySelector('.options');
    const submitButton = document.getElementById('submit');
    const resultContainer = document.getElementById('result');

    let currentQuestion = 0;
    let score = 0;

    function loadQuestion() {
        const currentQuiz = quiz[currentQuestion];
        questionContainer.textContent = currentQuiz.question;
        optionsContainer.innerHTML = '';
        currentQuiz.options.forEach((option, index) => {
            const button = document.createElement('button');
            button.textContent = `${String.fromCharCode(97 + index)}. ${option}`;
            button.value = String.fromCharCode(97 + index);
            button.addEventListener('click', () => {
                checkAnswer(button.value);
            });
            optionsContainer.appendChild(button);
        });
    }

    function checkAnswer(answer) {
        const currentQuiz = quiz[currentQuestion];
        if (answer === currentQuiz.answer) {
            score++;
        }
        currentQuestion++;
        if (currentQuestion < quiz.length) {
            loadQuestion();
        } else {
            showResult();
        }
    }

    function showResult() {
        quizContainer.style.display = 'none';
        resultContainer.innerHTML = `<h2>Your Score: ${score}/${quiz.length}</h2>`;
    }

    loadQuestion();
</script>
</body>
</html>
