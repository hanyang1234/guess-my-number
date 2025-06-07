<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Code Breaker Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            min-height: 100vh;
        }
        header {
            background-color: #4CAF50;
            width: 100%;
            padding: 15px;
            text-align: center;
            color: white;
        }
        main {
            flex: 1;
            width: 90%;
            max-width: 400px;
            background-color: white;
            margin: 20px 0;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        .guess-display {
            font-size: 1.5em;
            text-align: center;
            margin: 15px 0;
        }
        .feedback-inputs {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
        }
        .feedback-inputs label {
            display: flex;
            flex-direction: column;
            align-items: center;
            font-size: 0.9em;
            flex: 1;
        }
        .feedback-inputs input {
            width: 60px;
            padding: 8px;
            margin-top: 5px;
            font-size: 1em;
            text-align: center;
        }
        button {
            width: 100%;
            padding: 12px;
            font-size: 1em;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            margin-top: 10px;
        }
        #restart-btn {
            background-color: #e74c3c;
            margin-top: 5px;
        }
        button:disabled {
            background-color: #888;
            cursor: not-allowed;
        }
        .status {
            margin: 15px 0;
            text-align: center;
        }
        .history-container {
            margin-top: 15px;
        }
        .history-container h3 {
            margin-bottom: 5px;
            font-size: 1.1em;
        }
        .history-container ul {
            list-style: none;
            padding-left: 0;
            max-height: 150px;
            overflow-y: auto;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        .history-container li {
            padding: 8px;
            border-bottom: 1px solid #eee;
            font-size: 0.9em;
        }
        .history-container li:last-child {
            border-bottom: none;
        }
        .footer {
            margin: 20px 0;
            text-align: center;
            font-size: 0.8em;
            color: #666;
        }
        @media (max-width: 480px) {
            .feedback-inputs {
                flex-direction: column;
            }
            .feedback-inputs label {
                margin-bottom: 10px;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Code Breaker Game</h1>
    </header>
    <main>
        <div id="instructions">
            <p>Think of a secret 4-digit code using digits 1–9 (no repeats).<br>
            The computer will guess your code. After each guess, enter:<br>
            1) Number of digits correct and in the correct position (Exact)<br>
            2) Number of digits correct but in the wrong position (Partial)</p>
            <button id="start-btn">Start Game</button>
        </div>
        <div id="game-area" style="display: none;">
            <div class="guess-display">
                <span>Computer's Guess:</span>
                <div id="current-guess" style="font-weight: bold; margin-top: 5px;">----</div>
            </div>
            <div class="feedback-inputs">
                <label>
                    Exact<br>
                    <input type="number" id="exact-input" min="0" max="4" value="0">
                </label>
                <label>
                    Partial<br>
                    <input type="number" id="partial-input" min="0" max="4" value="0">
                </label>
            </div>
            <button id="submit-feedback">Submit Feedback</button>
            <button id="restart-btn">Restart Game</button>
            <div class="status">
                <div>Turn: <span id="turn-count">0</span></div>
                <div>Possible Codes Remaining: <span id="remaining-count">0</span></div>
            </div>
            <div class="history-container">
                <h3>History</h3>
                <ul id="history-list"></ul>
            </div>
            <div id="result-message" style="text-align: center; margin-top: 15px; font-size: 1.2em;"></div>
        </div>
    </main>
    <div class="footer">
        &copy; Code Breaker Game Demo
    </div>
    <script>
        // Generate all possible codes: 4-digit permutations of digits 1-9
        function generateAllCodes() {
            const digits = ['1','2','3','4','5','6','7','8','9'];
            const results = [];
            function permute(arr, m = []) {
                if (m.length === 4) {
                    results.push(m.join(''));
                    return;
                }
                for (let i = 0; i < arr.length; i++) {
                    const curr = arr.slice();
                    const next = curr.splice(i, 1);
                    permute(curr.slice(), m.concat(next));
                }
            }
            permute(digits);
            return results;
        }

        // Calculate exact and partial feedback between secret and guess
        function getFeedback(secret, guess) {
            let exact = 0;
            for (let i = 0; i < 4; i++) {
                if (secret[i] === guess[i]) exact++;
            }
            const secretSet = new Set(secret);
            const guessSet = new Set(guess);
            const commonCount = [...secretSet].filter(d => guessSet.has(d)).length;
            const partial = commonCount - exact;
            return { exact, partial };
        }

        // Filter possible codes by feedback
        function filterPossibleCodes(possibleCodes, lastGuess, feedback) {
            return possibleCodes.filter(code => {
                const { exact, partial } = getFeedback(code, lastGuess);
                return exact === feedback.exact && partial === feedback.partial;
            });
        }

        // Game state
        let possibleCodes = [];
        let currentGuess = '';
        let turn = 0;
        const historyList = document.getElementById('history-list');

        // DOM Elements
        const startBtn = document.getElementById('start-btn');
        const restartBtn = document.getElementById('restart-btn');
        const instructionsDiv = document.getElementById('instructions');
        const gameAreaDiv = document.getElementById('game-area');
        const guessDisplay = document.getElementById('current-guess');
        const exactInput = document.getElementById('exact-input');
        const partialInput = document.getElementById('partial-input');
        const submitFeedbackBtn = document.getElementById('submit-feedback');
        const turnCountSpan = document.getElementById('turn-count');
        const remainingCountSpan = document.getElementById('remaining-count');
        const resultMessageDiv = document.getElementById('result-message');

        // Initialize and start the game
        function startGame() {
            possibleCodes = generateAllCodes();
            turn = 1;
            historyList.innerHTML = '';
            instructionsDiv.style.display = 'none';
            gameAreaDiv.style.display = 'block';
            resultMessageDiv.textContent = '';
            submitFeedbackBtn.disabled = false;
            makeNextGuess();
        }

        // Make the next guess and update UI
        function makeNextGuess() {
            if (possibleCodes.length === 0) {
                resultMessageDiv.textContent = 'No possible codes remain. Please restart and check feedback consistency.';
                submitFeedbackBtn.disabled = true;
                return;
            }
            currentGuess = possibleCodes[0];
            guessDisplay.textContent = currentGuess;
            turnCountSpan.textContent = turn;
            remainingCountSpan.textContent = possibleCodes.length;
            exactInput.value = 0;
            partialInput.value = 0;
            resultMessageDiv.textContent = '';
        }

        // Handle feedback submission
        submitFeedbackBtn.addEventListener('click', () => {
            const exact = parseInt(exactInput.value, 10);
            const partial = parseInt(partialInput.value, 10);
            if (isNaN(exact) || isNaN(partial) || exact < 0 || partial < 0 || exact + partial > 4) {
                alert('Invalid feedback. Ensure values are between 0-4 and exact + partial ≤ 4.');
                return;
            }
            // Append to history
            const li = document.createElement('li');
            li.textContent = `Turn ${turn}: Guess ${currentGuess} – Exact: ${exact}, Partial: ${partial}`;
            historyList.appendChild(li);

            if (exact === 4) {
                resultMessageDiv.textContent = `Hooray! The code is ${currentGuess}. Cracked in ${turn} turns!`;
                submitFeedbackBtn.disabled = true;
                return;
            }
            possibleCodes = filterPossibleCodes(possibleCodes, currentGuess, { exact, partial });
            turn++;
            makeNextGuess();
        });

        // Handle game restart
        restartBtn.addEventListener('click', () => {
            instructionsDiv.style.display = 'block';
            gameAreaDiv.style.display = 'none';
        });

        // Attach start button handler
        startBtn.addEventListener('click', startGame);
    </script>
</body>
</html>
