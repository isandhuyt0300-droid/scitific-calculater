<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Free Scientific Calculator</title>
  <style>
    body {
      font-family: "Segoe UI", sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(135deg, #2b5876, #4e4376);
      margin: 0;
      color: #fff;
    }

    .calculator {
      background: #1c1c1c;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.3);
      width: 320px;
    }

    .display {
      background: #000;
      color: #0f0;
      font-size: 1.6em;
      text-align: right;
      padding: 15px;
      border-radius: 8px;
      margin-bottom: 15px;
      word-wrap: break-word;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 10px;
    }

    button {
      background: #333;
      color: #fff;
      border: none;
      border-radius: 8px;
      padding: 15px;
      font-size: 1em;
      cursor: pointer;
      transition: background 0.2s;
    }

    button:hover {
      background: #555;
    }

    .operator {
      background: #f57c00;
    }

    .equals {
      background: #43a047;
      grid-column: span 2;
    }

    .clear {
      background: #e53935;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div id="display" class="display">0</div>
    <div class="buttons">
      <button onclick="clearDisplay()" class="clear">C</button>
      <button onclick="deleteChar()">DEL</button>
      <button onclick="append('(')">(</button>
      <button onclick="append(')')">)</button>
      <button onclick="append('/')">÷</button>

      <button onclick="append('7')">7</button>
      <button onclick="append('8')">8</button>
      <button onclick="append('9')">9</button>
      <button onclick="append('*')">×</button>
      <button onclick="append('Math.sin(')">sin</button>

      <button onclick="append('4')">4</button>
      <button onclick="append('5')">5</button>
      <button onclick="append('6')">6</button>
      <button onclick="append('-')">−</button>
      <button onclick="append('Math.cos(')">cos</button>

      <button onclick="append('1')">1</button>
      <button onclick="append('2')">2</button>
      <button onclick="append('3')">3</button>
      <button onclick="append('+')">+</button>
      <button onclick="append('Math.tan(')">tan</button>

      <button onclick="append('0')">0</button>
      <button onclick="append('.')">.</button>
      <button onclick="calculate()" class="equals">=</button>
      <button onclick="append('Math.sqrt(')">√</button>
      <button onclick="append('Math.pow(')">xʸ</button>
    </div>
  </div>

  <script>
    let display = document.getElementById('display');

    function append(value) {
      if (display.innerText === "0") display.innerText = "";
      display.innerText += value;
    }

    function clearDisplay() {
      display.innerText = "0";
    }

    function deleteChar() {
      display.innerText = display.innerText.slice(0, -1) || "0";
    }

    function calculate() {
      try {
        const expression = display.innerText.replace(/÷/g, '/').replace(/×/g, '*');
        const result = eval(expression);
        display.innerText = result !== undefined ? result : "Error";
      } catch {
        display.innerText = "Error";
      }
    }
  </script>
</body>
</html>
