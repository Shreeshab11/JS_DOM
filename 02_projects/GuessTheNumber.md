# PROJECT 4 GUESS THE NUMBER

## HTML 
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Number Guessing Game</title>
    <link rel="stylesheet" href="style.css">
    <link rel="stylesheet" href="../styles.css">
</head>
<body style="background-color:#212121; color:#fff;">
  <nav>
    <a href="/" aria-current="page">Home</a>
    <a target="_blank" href="https://www.youtube.com/@chaiaurcode"
      >Youtube channel</a
    >
  </nav>
    
    <div id="wrapper">
      <h1>Number guessing game</h1>
    <p>Try and guess a random number between 1 and 100.</p>
    <p>You have 10 attempts to guess the right number.</p>
    </br>
        <form class="form">
            <label2 for="guessField" id="guess">Guess a number</label>
            <input type="text" id="guessField" class="guessField">
            <input type="submit" id="subt" value="Submit guess" class="guessSubmit">
        </form>

        <div class="resultParas">
            <p >Previous Guesses: <span class="guesses"></span></p>
            <p >Guesses Remaining: <span class="lastResult">10</span></p>
            <p class="lowOrHi"></p>
        </div>
    </div>
    <script src="chaiaurcode.js"></script>
</body>
</html>
```

## JavaScript
```javascript
const userInput = document.getElementById('guessField');
const randomNum = parseInt(Math.random() * 100 + 1);
const submit = document.getElementById('subt');

const guessSlot = document.querySelector('.guesses');
const lastResult = document.querySelector('.lastResult');
const lowOrHi = document.querySelector('.lowOrHi');
const startOver = document.querySelector('.resultParas');

const p = document.createElement('p');

let prevGuess = [];
let numGuess = 1;
let playGame = true;

if (playGame) {
  submit.addEventListener('click', (e) => {
    e.preventDefault();
    const guess = parseInt(userInput.value);
    console.log(guess);
    validateGuess(guess);
  });
}
const validateGuess = (guess) => {
  if (isNaN(guess)) {
    alert(`Entered value ${guess} is Not a Number`);
  } else if (guess > 100) {
    alert(`Entered Number ${guess} is greater than 100`);
  } else if (guess < 1) {
    alert(`Entered Number ${guess} is smaller than 1`);
  } else {
    prevGuess.push(guess);
    if (numGuess === 11) {
      displayGuess(guess);
      displayMessage(`Game Over Random Number was ${randomNum}`);
      endGame();
    } else {
      displayGuess(guess);
      checkGuess(guess);
    }
  }
};
const checkGuess = (guess) => {
  if (guess === randomNum) {
    displayMessage(`You guessed it right`);
    endGame();
  } else if (guess < randomNum) {
    displayMessage(`Number is Low`);
  } else {
    displayMessage(`Number is High`);
  }
};
const displayMessage = (message) => {
  lowOrHi.innerHTML = `${message}`;
};
const displayGuess = (guess) => {
  userInput.value = '';
  guessSlot.innerHTML += `${guess} `;
  numGuess++;
  lastResult.innerHTML = `${11 - numGuess}`;
};
const newGame = () => {};
const endGame = () => {};

```