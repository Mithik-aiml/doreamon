Html File:

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Doraemon Walking Around</title>
  <style>
    body {
      margin: 0;
      background: #f0f0f0;
      overflow: hidden;
    }

    #doremon {
      position: absolute;
      width: 100px;
      top: 0;
      left: 0;
      transition: transform 0.2s;
    }

    .flipX {
      transform: scaleX(-1); /* face left */
    }

    .flipY {
      transform: scaleY(-1); /* face up */
    }
  </style>
</head>
<body>
  <img id="doremon" src="d.gif" alt="Doraemon">

  <script>
    const doremon = document.getElementById("doremon");
    let x = 0, y = 0;
    let speed = 2;
    let direction = "right"; // right → down → left → up

    function walk() {
      const maxX = window.innerWidth - doremon.offsetWidth;
      const maxY = window.innerHeight - doremon.offsetHeight;

      if (direction === "right") {
        x += speed;
        if (x >= maxX) {
          x = maxX;
          direction = "down";
        }
        doremon.className = "";
      } 
      else if (direction === "down") {
        y += speed;
        if (y >= maxY) {
          y = maxY;
          direction = "left";
        }
        doremon.className = "flipY"; // face down
      } 
      else if (direction === "left") {
        x -= speed;
        if (x <= 0) {
          x = 0;
          direction = "up";
        }
        doremon.className = "flipX"; // face left
      } 
      else if (direction === "up") {
        y -= speed;
        if (y <= 0) {
          y = 0;
          direction = "right";
        }
        doremon.className = ""; // face right again
      }

      doremon.style.left = x + "px";
      doremon.style.top = y + "px";

      requestAnimationFrame(walk);
    }

    walk();
  </script>
</body>
</html>

```
