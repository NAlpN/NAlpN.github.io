<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <title>TEDx QR Okuyucu</title>
  <script src="https://unpkg.com/html5-qrcode" type="text/javascript"></script>
  <style>
    body {
      margin: 0;
      font-family: 'Arial', sans-serif;
      background-color: #000;
      color: #fff;
      text-align: center;
    }

    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;
    }

    h1 {
      margin-bottom: 20px;
      font-size: 24px;
      color: #ff2c2c;
    }

    .qr-wrapper {
      position: relative;
      width: 300px;
      height: 300px;
    }

    #reader {
      width: 100%;
      height: 100%;
      border: 2px solid #fff;
    }

    .qr-box-overlay {
      position: absolute;
      top: 25%;
      left: 25%;
      width: 50%;
      height: 50%;
      border: 2px dashed red;
      box-sizing: border-box;
      pointer-events: none;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>TEDx Atatürk Üniversitesi</h1>

    <div class="qr-wrapper">
      <div id="reader"></div>
      <div class="qr-box-overlay"></div>
    </div>
  </div>

  <script>
    function onScanSuccess(decodedText, decodedResult) {
      console.log(`QR Kod bulundu: ${decodedText}`);
      alert(`QR Kod: ${decodedText}`);
    }

    const html5QrCode = new Html5Qrcode("reader");
    html5QrCode.start(
      { facingMode: "environment" }, // Arka kamera
      {
        fps: 10,
        qrbox: { width: 250, height: 250 }
      },
      onScanSuccess
    );
  </script>

</body>
</html>
