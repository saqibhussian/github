<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Elite QR Live Tool</title>
<style>
body { background-color: #000; color: #0f0; font-family: 'Courier New', monospace; text-align: center; padding: 50px;}
h1 { text-shadow: 0 0 10px #0f0; }
.container { max-width: 600px; margin: auto; padding: 30px; border: 2px solid #0f0; border-radius: 10px; box-shadow: 0 0 20px #0f0; background-color: #111; }
input { padding: 10px; width: 60%; max-width: 300px; border: 2px solid #0f0; border-radius: 5px; background-color: #000; color: #0f0; }
button { padding: 10px 20px; margin-left: 10px; border: none; border-radius: 5px; background: #0f0; color: #000; font-weight: bold; cursor: pointer; box-shadow: 0 0 10px #0f0; }
img { margin-top: 20px; border: 2px solid #0f0; border-radius: 5px; }
#console { background-color: #000; color: #0f0; font-family: monospace; text-align: left; margin-top: 20px; padding: 15px; border: 1px solid #0f0; border-radius: 5px; height: 100px; overflow-y: auto; }
</style>
</head>
<body>
<div class="container">
<h1>Elite QR Live Tool</h1>
<input type="text" id="text" placeholder="Enter text or link">
<button onclick="generateQR()">Generate</button>
<br>
<img id="qr" alt="QR Code">
<div id="console"></div>
</div>
<script>
function generateQR() {
    let text = document.getElementById("text").value;
    if(text.trim() === "") return;
    document.getElementById("qr").src =
    "https://api.qrserver.com/v1/create-qr-code/?size=250x250&data=" + encodeURIComponent(text);
    let consoleDiv = document.getElementById("console");
    consoleDiv.innerHTML = "";
    let message = `Generating QR for: ${text}\nStatus: SUCCESS`;
    let i = 0;
    let interval = setInterval(() => {
        if(i < message.length){
            consoleDiv.innerHTML += message[i];
            i++;
        } else clearInterval(interval);
        consoleDiv.scrollTop = consoleDiv.scrollHeight;
    }, 30);
}
</script>
</body>
</html>
