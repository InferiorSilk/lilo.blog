+++
title = "Test"
date = "2024-05-06"
draft = false
pinned = false
+++
<!--StartFragment-->

<!DOCTYPE html>

<html>

<head>

  <meta charset="UTF-8">

  <title>Functional Analog Clock</title>

  <style>

    body {

      font-family: Arial, Helvetica, sans-serif;

      background-color: black;

      color: white;

      display: flex;

      flex-direction: column;

      align-items: center;

      justify-content: center;

      height: 100vh;

      margin: 0;

    }

    .clock-container {

      text-align: center;

      margin-top: 20px;

    }

    canvas {

      border: 2px solid white;

    }

    .link-container {

      text-align: center;

      margin-top: 20px;

    }

    .black-link a {

      color: black;

    }

  </style>

</head>

<body>

  <h1>This is a clock</h1>

  <p>If you do not know what a clock is, look <a href="https://de.wikipedia.org/wiki/Uhr">here</a>.</p>

  <ul>

    <li>This clock is dependent on your location.</li>

    <li>This is because time is not the same everywhere.</li>

  </ul>

  <p>Somewhere on this page is a link hidden. Good luck.</p>

  <p>No I obviously didnt program that (the clock) by myself</p>

  <div class="clock-container">

    <canvas id="clockCanvas" width="200" height="200"></canvas>

  </div>

  <div class="link-container black-link">

    <p><a href="hidden.html">Link</a></p>

  </div>



  <script>

    function drawClock() {

      const canvas = document.getElementById('clockCanvas');

      const context = canvas.getContext('2d');

      const centerX = canvas.width / 2;

      const centerY = canvas.height / 2;

      const radius = 80;



      context.clearRect(0, 0, canvas.width, canvas.height);



      // Draw clock face

      context.beginPath();

      context.arc(centerX, centerY, radius, 0, 2 * Math.PI);

      context.fillStyle = 'white';

      context.fill();



      // Draw clock outline

      context.beginPath();

      context.arc(centerX, centerY, radius, 0, 2 * Math.PI);

      context.strokeStyle = 'black';

      context.lineWidth = 2;

      context.stroke();



      // Draw hour markers

      for (let i = 0; i < 12; i++) {

        const angle = i * (360 / 12);

        const radians = (angle - 90) * (Math.PI / 180);

        const x = centerX + (radius - 10) * Math.cos(radians);

        const y = centerY + (radius - 10) * Math.sin(radians);



        context.beginPath();

        context.arc(x, y, 3, 0, 2 * Math.PI);

        context.fillStyle = 'black';

        context.fill();

      }



      // Get current time and draw clock hands

      const now = new Date();

      const hours = now.getHours() % 12;

      const minutes = now.getMinutes();

      const seconds = now.getSeconds();



      drawHand(context, centerX, centerY, hours * 30 + (minutes / 2), radius - 20, 6); // Hour hand

      drawHand(context, centerX, centerY, minutes * 6, radius - 10, 4); // Minute hand

      drawHand(context, centerX, centerY, seconds * 6, radius - 5, 2); // Second hand



      requestAnimationFrame(drawClock);

    }



    function drawHand(context, x, y, angle, length, width) {

      const radians = (angle - 90) * (Math.PI / 180);

      const endX = x + length * Math.cos(radians);

      const endY = y + length * Math.sin(radians);



      context.beginPath();

      context.moveTo(x, y);

      context.lineTo(endX, endY);

      context.lineWidth = width;

      context.strokeStyle = 'black';

      context.stroke();

    }



    // Start the clock

    drawClock();

  </script>

</body>

</html>



<!--EndFragment-->