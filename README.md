<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<title>QR — ПланТехСтрой</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<style>
  body { margin: 0; background: #fff; display: flex; flex-direction: column; align-items: center; justify-content: center; min-height: 100vh; font-family: Arial, sans-serif; }
  #qr { margin: 20px; }
  #qr canvas, #qr img { display: block; }
  p { color: #555; font-size: 14px; margin: 0 0 16px; }
  button { padding: 14px 32px; background: #4caf7d; color: #fff; border: none; border-radius: 8px; font-size: 15px; font-weight: 700; cursor: pointer; }
  button:hover { background: #3a9e6a; }
</style>
</head>
<body>
<p>QR-код ПланТехСтрой → все соцсети</p>
<div id="qr"></div>
<button id="btn">⬇ Скачать PNG</button>

<script>
  // Create QR
  var qr = new QRCode(document.getElementById("qr"), {
    text: "https://artemw997-max.github.io/planteh-links/",
    width: 500,
    height: 500,
    colorDark: "#1a5c35",
    colorLight: "#ffffff",
    correctLevel: QRCode.CorrectLevel.H
  });

  // Wait for QR to render then enable download
  document.getElementById("btn").addEventListener("click", function() {
    var canvas = document.querySelector("#qr canvas");
    if (canvas) {
      var a = document.createElement("a");
      a.href = canvas.toDataURL("image/png");
      a.download = "planteh-qr.png";
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    } else {
      // Fallback: img tag
      var img = document.querySelector("#qr img");
      if (img) {
        var a = document.createElement("a");
        a.href = img.src;
        a.download = "planteh-qr.png";
        document.body.appendChild(a);
        a.click();
        document.body.removeChild(a);
      }
    }
  });

  // Auto-trigger after 2 seconds
  setTimeout(function() {
    document.getElementById("btn").click();
  }, 2000);
</script>
</body>
</html>
