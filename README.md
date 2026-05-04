[controller-smartphone.html](https://github.com/user-attachments/files/27378133/controller-smartphone.html)
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>🏓 Racket Controller</title>
  <script src="/socket.io/socket.io.js"></script>
  <style>
    :root {
      --bg: #0f172a;
      --primary: #3b82f6;
      --red: #ef4444;
      --blue: #3b82f6;
    }
    body {
      margin: 0;
      padding: 0;
      background: var(--bg);
      color: white;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      overflow: hidden;
      text-align: center;
    }
    .container {
      width: 90%;
      max-width: 400px;
    }
    h1 { font-size: 1.5rem; margin-bottom: 2rem; }
    .status {
      margin-bottom: 2rem;
      padding: 1rem;
      background: rgba(255, 255, 255, 0.05);
      border-radius: 12px;
      font-size: 0.9rem;
    }
    .controls {
      display: grid;
      gap: 1rem;
      width: 100%;
    }
    button {
      padding: 1.25rem;
      border: none;
      border-radius: 12px;
      font-size: 1.1rem;
      font-weight: 600;
      cursor: pointer;
      transition: transform 0.1s;
    }
    button:active { transform: scale(0.95); }
    #btn-start { background: var(--primary); color: white; }
    #btn-calibrate { background: rgba(255, 255, 255, 0.15); color: white; display: none; }
    .debug {
      margin-top: 2rem;
      font-family: monospace;
      font-size: 0.75rem;
      opacity: 0.5;
      text-align: left;
      width: 100%;
    }
    .hidden { display: none !important; }
    .role-indicator {
      width: 20px;
      height: 20px;
      border-radius: 50%;
      display: inline-block;
      margin-right: 8px;
      vertical-align: middle;
    }
    .role-red { background: var(--red); }
    .role-blue { background: var(--blue); }
  </style>
</head>
<body>

  <div class="container" id="setup-view">
    <h1>Connect Controller</h1>
    <div class="status" id="setup-status">Enter the 6-digit code from your computer</div>
    <div class="controls">
      <input type="text" id="input-code" placeholder="123456" 
             style="padding: 1rem; border-radius: 12px; border: none; font-size: 1.5rem; text-align: center; margin-bottom: 1rem;">
      <div style="display: flex; gap: 10px;">
        <button id="btn-join-red" style="flex: 1; background: var(--red);">Join RED</button>
        <button id="btn-join-blue" style="flex: 1; background: var(--blue);">Join BLUE</button>
      </div>
    </div>
  </div>

  <div class="container hidden" id="game-view">
    <h1><span id="role-badge" class="role-indicator"></span> Controller</h1>
    <div class="status" id="game-status">Connected to session: <span id="display-code"></span></div>
    
    <div class="controls">
      <button id="btn-start">ACTIVATE SENSORS</button>
      <button id="btn-calibrate">CALIBRATE</button>
    </div>

    <div class="debug" id="debug-info">
      Waiting for sensor data...
    </div>
  </div>

  <script src="/js/controller-smartphone.js"></script>
</body>
</html>
