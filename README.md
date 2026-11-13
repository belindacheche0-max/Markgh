# Markgh
Health app

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>HealthTrack</title>

<style>
body {
  font-family: Arial, sans-serif;
  background: #f0f8f1;
  margin: 0;
  padding: 20px;
  text-align: center;
}

.container {
  max-width: 420px;
  margin: auto;
  background: white;
  padding: 25px;
  border-radius: 18px;
  box-shadow: 0 4px 15px #ccc;
}

h1 { color: #23945b; }

input, button {
  width: 90%;
  padding: 12px;
  margin: 10px 0;
  border-radius: 8px;
  border: 1px solid #ccc;
}

button {
  background: #23945b;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover { background: #176b40; }

.result {
  background: #e5f7e9;
  padding: 15px;
  border-radius: 10px;
  margin-top: 15px;
}
</style>
</head>

<body>

<div class="container">
  <h1>🌿 HealthTrack</h1>
  <p>Check the estimated calories in your food.</p>

  <input id="food" type="text"
    placeholder="Enter food (e.g. rice)">

  <input id="amount" type="number"
    placeholder="Amount in grams">

  <button onclick="checkCalories()">
    Check Calories
  </button>

  <div class="result" id="result">
    Your nutrition results will appear here.
  </div>
</div>

<script>
const foods = {
  rice: 130,
  egg: 155,
  banana: 89,
  apple: 52,
  chicken: 165,
  potato: 87,
  bread: 265,
  beans: 127,
  avocado: 160
};

function checkCalories() {
  const food = document.getElementById("food")
    .value.toLowerCase().trim();

  const amount = Number(
    document.getElementById("amount").value
  );

  const result = document.getElementById("result");

  if (!food || !amount || amount <= 0) {
    result.innerHTML = "Please enter a food and a valid amount.";
    return;
  }

  if (!foods[food]) {
    result.innerHTML =
      "Food not found. Try rice, egg, banana or chicken.";
    return;
  }

  const calories = (foods[food] * amount) / 100;

  result.innerHTML = `
    <h3>Nutrition Results</h3>
    <p>Food: ${food}</p>
    <p>Amount: ${amount} grams</p>
    <h2>${calories.toFixed(1)} kcal</h2>
    <p>Estimated calories</p>
  `;
}
</script>

</body>
</html>
