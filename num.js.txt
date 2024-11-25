
let secretNumber;
let attemptsLeft;

function start() {
    secretNumber = Math.floor(Math.random() * 100) + 1;
    attemptsLeft = 10;
    document.getElementById("message").innerText = "Game started. You have 10 attempts.";
    document.getElementById("estim").value = "";
    document.getElementById("estim").disabled = false;
    document.getElementById("guess").disabled = false;
}

function guess() {
    let guess = parseInt(document.getElementById("estim").value);
    if (isNaN(guess) || guess < 1 || guess > 100) {
        alert("Please enter a valid number between 1 and 100.");
        return;
    }

    attemptsLeft--;
    if (guess === secretNumber) {
        document.getElementById("message").innerText = `Congratulations! You guessed the number ${secretNumber} in ${10 - attemptsLeft} attempts.`;
        document.getElementById("estim").disabled = true;
        document.getElementById("estim").value = ""
        document.getElementById("guess").disabled = true;
    } else if (attemptsLeft === 0) {
        document.getElementById("message").innerText = `Out of attempts. The number was ${secretNumber}.`;
        document.getElementById("estim").disabled = true;
        document.getElementById("estim").value = ""
        document.getElementById("guess").disabled = true;
    } else {
        let hint = guess < secretNumber ? "higher" : "lower";
        document.getElementById("message").innerText = `Incorrect. Try a ${hint} number. Attempts left: ${attemptsLeft}.`;
    }
}
