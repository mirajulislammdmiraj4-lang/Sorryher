<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>I am so Sorry Juthii!</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }

    body {
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #a1c4fd 0%, #c2e9fb 100%);
      overflow: hidden;
      position: relative;
    }

    /* Main Container Card */
    .container {
      background: rgba(255, 255, 255, 0.85);
      padding: 35px 25px;
      border-radius: 20px;
      box-shadow: 0 15px 35px rgba(0,0,0,0.1);
      text-align: center;
      max-width: 400px;
      width: 85%;
      backdrop-filter: blur(8px);
      position: relative;
      z-index: 100;
      border: 1px solid rgba(255, 255, 255, 0.5);
    }

    .heart-icon {
      font-size: 55px;
      animation: beat 1.2s infinite alternate;
      display: inline-block;
    }

    @keyframes beat {
      0% { transform: scale(1); }
      100% { transform: scale(1.15); }
    }

    h1 {
      color: #334155;
      margin: 10px 0;
      font-size: 26px;
    }

    p {
      color: #64748b;
      font-size: 15px;
      line-height: 1.5;
      margin-bottom: 20px;
    }

    .btn-group {
      display: flex;
      justify-content: center;
      gap: 15px;
    }

    button {
      padding: 10px 22px;
      font-size: 15px;
      font-weight: bold;
      border: none;
      border-radius: 25px;
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .yes-btn {
      background: #7c3aed;
      color: white;
      box-shadow: 0 4px 15px rgba(124, 58, 237, 0.3);
    }

    .yes-btn:hover {
      transform: scale(1.05);
      background: #6d28d9;
    }

    .no-btn {
      background: #e2e8f0;
      color: #475569;
    }

    .no-btn:hover {
      background: #cbd5e1;
    }

    /* Floating Sorry Animation */
    .floating-sorry {
      position: absolute;
      color: rgba(255, 255, 255, 0.9);
      font-weight: bold;
      pointer-events: none;
      user-select: none;
      animation: floatUp 6s linear forwards;
      white-space: nowrap;
      text-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
      z-index: 1;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(0.8) rotate(0deg);
        opacity: 0;
      }
      10% { opacity: 0.9; }
      90% { opacity: 0.9; }
      100% {
        transform: translateY(-105vh) scale(1.3) rotate(15deg);
        opacity: 0;
      }
    }

    /* Popup Modal Styling */
    .modal-overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 0, 0.3);
      backdrop-filter: blur(4px);
      z-index: 200;
      justify-content: center;
      align-items: center;
    }

    .modal-box {
      background: #ffffff;
      padding: 25px 20px;
      border-radius: 18px;
      text-align: center;
      max-width: 320px;
      width: 80%;
      box-shadow: 0 10px 25px rgba(0,0,0,0.15);
      animation: popIn 0.3s ease-out;
    }

    @keyframes popIn {
      0% { transform: scale(0.7); opacity: 0; }
      100% { transform: scale(1); opacity: 1; }
    }

    .modal-box p {
      color: #334155;
      font-size: 16px;
      font-weight: 600;
      margin-bottom: 15px;
    }

    .close-btn {
      background: #7c3aed;
      color: white;
      padding: 8px 20px;
      font-size: 14px;
      border: none;
      border-radius: 20px;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <!-- Soft Piano Music -->
  <audio id="bgMusic" loop preload="auto">
    <source src="https://cdn.pixabay.com/download/audio/2022/05/27/audio_1808fbf07a.mp3?filename=soft-piano-108740.mp3" type="audio/mpeg">
  </audio>

  <!-- Main Card -->
  <div class="container" id="mainCard">
    <div class="heart-icon">🥺🤍</div>
    <h1>I am So Sorry Juthii!</h1>
    <p>It was my mistake Juthii, please don't be mad at me. Can you please forgive me?</p>
    
    <div class="btn-group">
      <button class="yes-btn" onclick="forgive()">Forgive Me</button>
      <button class="no-btn" onclick="showPopup()">No</button>
    </div>
  </div>

  <!-- Request Popup -->
  <div class="modal-overlay" id="popupModal">
    <div class="modal-box">
      <div style="font-size: 40px; margin-bottom: 8px;">🥺🤍</div>
      <p>Please accept my sorry Juthii! Please give me one more chance!</p>
      <button class="close-btn" onclick="closePopup()">Okay 🤍</button>
    </div>
  </div>

  <script>
    // Play music on first interaction
    document.body.addEventListener('click', function() {
      const music = document.getElementById('bgMusic');
      if (music.paused) {
        music.play();
      }
    }, { once: true });

    // Show Request Modal when clicking 'No'
    function showPopup() {
      document.getElementById('popupModal').style.display = 'flex';
    }

    // Close Request Modal
    function closePopup() {
      document.getElementById('popupModal').style.display = 'none';
    }

    // Message after clicking 'Forgive Me'
    function forgive() {
      const card = document.getElementById('mainCard');
      card.innerHTML = `
        <div class="heart-icon">✨🤍</div>
        <h1>Yay! Thank You Juthii!</h1>
        <p>You are the best! I promise I won't repeat this mistake again! 😊</p>
      `;
    }

    // Floating 'Sorry Juthii' animation logic
    function createFloatingSorry() {
      const sorryText = document.createElement('div');
      sorryText.classList.add('floating-sorry');

      const texts = ["Sorry Juthii 🤍", "I'm So Sorry Juthii", "Please Forgive Me Juthii 🤍", "Sorry Juthii..."];
      const randomText = texts[Math.floor(Math.random() * texts.length)];
      
      sorryText.innerText = randomText;
      sorryText.style.left = Math.random() * 90 + 'vw';
      sorryText.style.fontSize = (Math.random() * 20 + 18) + 'px';
      sorryText.style.bottom = '-50px';
      sorryText.style.animationDuration = (Math.random() * 3 + 4) + 's';

      document.body.appendChild(sorryText);

      setTimeout(() => {
        sorryText.remove();
      }, 7000);
    }

    setInterval(createFloatingSorry, 200);
  </script>
</body>
</html>
