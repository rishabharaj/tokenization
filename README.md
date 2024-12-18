<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Explore Stocks - STOCK SAARTHI</title>
  <link rel="stylesheet" href="website.css">
</head>
<body> <style>
  /* Basic styling */
  body {
    margin: 0;
    font-family: Arial, sans-serif;
    transition: background-color 0.3s ease, color 0.3s ease;
  }

  /* Default Light Mode */
  body.light-mode {
    background-color: #ffffff;
    color: #000000;
  }

  /* Dark Mode */
  body.dark-mode {
    background-color: #0b0a0a;
    color: #ffffff;
  }

  /* Toggle button styles */
  #theme-toggle {
    position: absolute;
    bottom: 20px;
    right: 20px;
    padding: 10px 0px;
    cursor: pointer;
    border: none;
    border-radius: 20px;
    background-color: #f0f0f0;
    color: #000;
    font-size: 16px;
    transition: background-color 0.3s, color 0.3s;
  }

  #theme-toggle.dark {
    background-color: #ded5d5;
    color: #fff;
  }
</style>
</head>
<body class="light-mode">
<!-- Theme Toggle Button -->
<button id="theme-toggle">🌙 Dark Mode</button>

<!-- Example Content -->

<script>
  // Select the toggle button
  const themeToggle = document.getElementById('theme-toggle');

  // Check for saved theme in localStorage
  const savedTheme = localStorage.getItem('theme');
  if (savedTheme) {
    document.body.className = savedTheme;
    updateButtonText();
  }

  // Add click event listener to toggle button
  themeToggle.addEventListener('click', () => {
    document.body.classList.toggle('dark-mode');
    document.body.classList.toggle('light-mode');

    // Save the current theme in localStorage
    const currentTheme = document.body.className;
    localStorage.setItem('theme', currentTheme);

    updateButtonText();
  });

  // Update button text based on current theme
  function updateButtonText() {
    if (document.body.classList.contains('dark-mode')) {
      themeToggle.textContent = '☀️ Light Mode';
      themeToggle.classList.add('dark');
    } else {
      themeToggle.textContent = '🌙 Dark Mode';
      themeToggle.classList.remove('dark');
    }
  }
</script>
  <!-- Navigation Bar -->
  <header class="navbar">
    <div class="logo">STOCK SAARTHI</div>
    <ul>
      <li><a href="#">Home</a></li>
      <li><a href="#">Stocks</a></li>
      <li><a href="login.html" >Login</a>
      </li>
      <li><a href="#mutual-funds-section">Mutual Funds</a></li>
      <li><a href="profile.html" >wallet</a>
      </li>
    </ul>
  </header>

  <!-- Main Content -->
  <main>
    <h1>Explore Stocks</h1>
    <div class="stocks-container">
      <!-- Stock Cards -->
      <div class="stock-card">
        <h2>Apple Inc. (AAPL)</h2>
        <p>Price: $172.38</p>
        <p class="positive">+1.24%</p>
        <button class="buy-button">Buy</button>
      </div>
      <div class="stock-card">
        <h2>Tesla Inc. (TSLA)</h2>
        <p>Price: $674.23</p>
        <p class="negative">-2.16%</p>
        <button class="buy-button">Buy</button>
      </div>
      <div class="stock-card">
        <h2>Amazon.com (AMZN)</h2>
        <p>Price: $123.45</p>
        <p class="positive">+0.82%</p>
        <button class="buy-button">Buy</button>
      </div>
      <div class="stock-card">
        <h2>Tata Consultancy Services Limited</h2>
        <p>Price: $350</p>
        <p class="positive">+2.5%</p>
        <button class="buy-button">Buy</button>
      </div>
      <div class="stock-card">
        <h2>Reliance Industries Limited</h2>
        <p>Price: $240</p>
        <p class="negative">-1.2%</p>
        <button class="buy-button">Buy</button>
      </div>
      <div class="stock-card">
        <h2>Infosys Limited</h2>
        <p>Price: $1700 </p>
        <p class="positive">+3.1%</p>
        <button class="buy-button">Buy</button>
      </div>
      <div class="stock-card">
        <h2>Reliance Industries Limited</h2>
        <p>Price: $1450</p>
        <p class="negative">-0.5%</p>
        <button class="buy-button">Buy</button>
      </div>
      <script>
        
         <!-- Mutual Funds Section -->
  <main id="mutual-funds-section" class="section">
    <h1>Explore Mutual Funds</h1>
    <div class="funds-container">
     
      <div class="fund-card">
        <h2>Motilal Oswal Midcap Fund</h2>
        <p>Returns: 36.9% (3Y)</p>
      </div>
      <div class="fund-card">
        <h2>Quant Small Cap Fund</h2>
        <p>Returns: 27.4% (3Y)</p>
      </div>
      <div class="fund-card">
        <h2>Parag Parikh Flexi Cap Fund</h2>
        <p>Returns: 17.5% (3Y)</p>
      </div>
      <div class="fund-card">
        <h2>Nippon India Large Cap Fund</h2>
        <p>Returns: 22.5% (3Y)</p>
      </div>
    </div>
    <div class="investment-summary">
      <h2>Your Investments</h2>
      <p>Total Returns: +₹9</p>
      <p>Current Value: ₹109</p>
    </div>
  </main>

        async function fetchData(stockSymbol) {
          try {
            const response = await fetch(`http://localhost:5000/stock-data?symbol=${stockSymbol}`);
            const data = await response.json();
    
            if (data.error) {
              alert(`Error fetching data for ${stockSymbol}: ${data.error}`);
              return;
            }
    
            // Update stock price and chart
            document.getElementById(`${stockSymbol}-price`).textContent = `Price: $${data.current_price}`;
            const chartImg = document.getElementById(`${stockSymbol}-chart`);
            chartImg.src = `http://localhost:5000${data.chart_url}`;
            chartImg.style.display = 'block';
          } catch (error) {
            console.error(`Error fetching data for ${stockSymbol}:`, error);
          }
        }
      </script>
 <script src="server.js"></script>
  <script src="script.js"></script>
</body>
</html>
