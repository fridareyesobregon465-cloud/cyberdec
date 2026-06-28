<script>
const qrText = document.getElementById("qrText");
const qrDiv = document.getElementById("qr");

let qrCode = null;

function generarQR() {

    qrDiv.innerHTML = "";

    qrCode = new QRCode(qrDiv, {
        text: qrText.value.trim() || "CYBERDECK",
        width: 300,
        height: 300,
        colorDark: "#000000",
        colorLight: "#ffffff",
        correctLevel: QRCode.CorrectLevel.H
    });
}

function guardarQR() {

    const canvas = qrDiv.querySelector("canvas");
    const img = qrDiv.querySelector("img");

    let url = null;

    if (canvas) {
        url = canvas.toDataURL("image/png");
    } else if (img) {
        url = img.src;
    } else {
        alert("Primero genera un QR.");
        return;
    }

    const enlace = document.createElement("a");
    enlace.href = url;
    enlace.download = "codigo_qr.png";
    enlace.click();
}

generarQR();
</script>
<button onclick="guardarQR()">GUARDAR PNG</button>
