![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=Chickenwng&show_icons=true&theme=dark) <img src="https://github-readme-stats.vercel.app/api/top-langs?username=Chickenwng&show_icons=true&locale=en&layout=compact&theme=chartreuse-dark" alt="ovi" />

[![trophy](https://github-profile-trophy.vercel.app/?username=Chickenwng&theme=onedark)](https://github.com/ryo-ma/github-profile-trophy)

<h1>🚀 Space Dodger Game</h1>
<p>Control the spaceship and avoid incoming asteroids! Use the arrow keys to move.</p>
<canvas id="gameCanvas" width="400" height="500" style="border:1px solid black;"></canvas>
<script>
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");
let spaceship = { x: 175, y: 450, width: 50, height: 50 };
let asteroids = [];
let gameOver = false;

function drawSpaceship() {
    ctx.fillStyle = "blue";
    ctx.fillRect(spaceship.x, spaceship.y, spaceship.width, spaceship.height);
}

function drawAsteroids() {
    ctx.fillStyle = "red";
    asteroids.forEach((asteroid, index) => {
        ctx.fillRect(asteroid.x, asteroid.y, asteroid.size, asteroid.size);
        asteroid.y += 4;
        if (asteroid.y > canvas.height) asteroids.splice(index, 1);
        if (collision(spaceship, asteroid)) gameOver = true;
    });
}

function collision(rect1, rect2) {
    return (
        rect1.x < rect2.x + rect2.size &&
        rect1.x + rect1.width > rect2.x &&
        rect1.y < rect2.y + rect2.size &&
        rect1.y + rect1.height > rect2.y
    );
}

function update() {
    if (gameOver) {
        ctx.fillStyle = "black";
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        ctx.fillStyle = "white";
        ctx.font = "30px Arial";
        ctx.fillText("Game Over", 120, 250);
        return;
    }
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    drawSpaceship();
    drawAsteroids();
    requestAnimationFrame(update);
}

function moveSpaceship(event) {
    if (event.key === "ArrowLeft" && spaceship.x > 0) spaceship.x -= 20;
    if (event.key === "ArrowRight" && spaceship.x < canvas.width - spaceship.width) spaceship.x += 20;
}

document.addEventListener("keydown", moveSpaceship);
setInterval(() => {
    asteroids.push({ x: Math.random() * 350, y: 0, size: 30 });
}, 1000);
update();
</script>

<!--
**Chickenwng/Chickenwng** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
