<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Animations and Local Storage Example</title>
  <style>
    /* Default light theme */
    body {
      background-color: white;
      color: black;
      transition: background-color 0.5s ease, color 0.5s ease;
    }

    /* Dark theme */
    body.dark-theme {
      background-color: #2c3e50;
      color: white;
    }

    /* Button styling */
    .button {
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
      background-color: #3498db;
      color: white;
      border: none;
      border-radius: 5px;
      transition: transform 0.3s ease, background-color 0.3s ease;
    }

    /* Button hover effect */
    .button:hover {
      transform: scale(1.1);
      background-color: #2980b9;
    }
  </style>
</head>
<body>

  <button id="themeButton" class="button">Toggle Theme</button>
  <div id="themeContent">Welcome to my website!</div>

  <script>
    // Function to toggle between light and dark themes
    function toggleTheme() {
      const body = document.body;
      const currentTheme = localStorage.getItem('theme');

      if (currentTheme === 'dark') {
        body.classList.remove('dark-theme');
        localStorage.setItem('theme', 'light');
      } else {
        body.classList.add('dark-theme');
        localStorage.setItem('theme', 'dark');
      }
    }

    // Function to apply the stored theme on page load
    function applyStoredTheme() {
      const savedTheme = localStorage.getItem('theme');
      if (savedTheme === 'dark') {
        document.body.classList.add('dark-theme');
      }
    }

    // Apply stored theme when the page loads
    window.onload = applyStoredTheme;

    // Trigger the theme change on button click
    document.getElementById('themeButton').addEventListener('click', toggleTheme);
  </script>

</body>
</html>
