<!DOCTYPE html>
<html>
<head>
  <title>Miss You 💙</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      text-align: center;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to bottom, #ffe6f0, #ffffff);
      padding-top: 60px;
    }

    h1 {
      color: #ff4d6d;
    }

    button {
      padding: 15px 35px;
      font-size: 18px;
      border: none;
      border-radius: 12px;
      background-color: #ff4d6d;
      color: white;
      cursor: pointer;
      transition: transform 0.2s ease, background 0.3s ease;
    }

    button:hover {
      background-color: #e60039;
      transform: scale(1.05);
    }

    #message {
      margin-top: 30px;
      font-size: 22px;
      color: #444;
      min-height: 30px;
    }
  </style>
</head>

<body>

<h1>Click when you miss me 💕</h1>

<button onclick="missYou()">I Miss You</button>

<div id="message"></div>

<script>
const messages = [
  "I'm always thinking about you 💭",
  "You're my favorite human ❤️",
  "Even miles can't change us 🌍",
  "I miss you more than coffee ☕",
  "You’re my safe place 💙",
  "Come here. Virtual hug 🤗"
];

function missYou() {
  const randomMessage = messages[Math.floor(Math.random() * messages.length)];
  document.getElementById("message").innerText = randomMessage;

  fetch("https://cindyjo9.github.io/cinvin/", {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify({ message: randomMessage })
  })
  .then(response => {
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    return response.json();
  })
  .then(data => {
    console.log('Notification sent successfully:', data);
  })
  .catch(error => {
    console.error('Error sending notification:', error);
  });
}
</script>

</body>
</html>
