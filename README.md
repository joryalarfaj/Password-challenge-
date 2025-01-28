# Password-challenge-

<!DOCTYPE html>
<html lang="ar">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>تحدي كلمة المرور</title>
    <style>
      @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600&display=swap');

      body {
        font-family: 'Cairo', sans-serif;
        text-align: center;
        margin: 0;
        padding: 0;
        background: #f7f9fc;
        color: #333;
        direction: rtl;
      }

      h1 {
        color: #34495e; /* اللون الكحلي */
        font-size: 4em;
        margin-top: 50px;
        font-weight: 800; /* زيادة السمك */
      }

      p {
        font-size: 1.3em;
        margin: 10px 0;
        font-weight: 400;
      }

      input,
      button {
        padding: 15px;
        font-size: 1.2em;
        margin: 15px 0;
        width: 80%;
        border-radius: 8px;
        border: 1px solid #ddd;
        outline: none;
        box-sizing: border-box;
      }

      input {
        width: 60%;
        border: 2px solid #3498db;
      }

      button {
        width: 40%;
        background-color: #2980b9;
        color: white;
        border: none;
        cursor: pointer;
        transition: background-color 0.3s;
      }

      button:hover {
        background-color: #2471a3;
      }

      .message {
        margin-top: 30px;
        font-size: 1.5em;
        color: #333;
      }

      .stars {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        z-index: 10;
        display: none;
      }

      .star {
        position: absolute;
        background-color: yellow;
        border-radius: 50%;
        animation: twinkle 1s infinite;
        opacity: 0.8;
        width: 5px; /* حجم صغير */
        height: 5px;
      }

      @keyframes twinkle {
        0% {
          transform: scale(1);
          opacity: 0.6;
        }
        50% {
          transform: scale(1.2);
          opacity: 1;
        }
        100% {
          transform: scale(1);
          opacity: 0.6;
        }
      }
    </style>
  </head>

  <body>
    <h1>تحدي كلمة المرور</h1>
    <p>حاول تخمين كلمة المرور الصحيحة بناءً على التلميحات التالية:</p>
    <ul style="list-style: none; padding: 0;">
      <li><b>الاسم:</b> Nora</li>
      <li><b>تاريخ الميلاد:</b> 6/12/2007</li>
      <li><b>عدد الرموز:</b> 12</li>
      <li><b>يحتوي على حرف كبير</b></li>
    </ul>
    <p><b>عدد المحاولات المسموحة:</b> 5</p>

    <input type="password" id="passwordInput" placeholder="أدخل كلمة المرور" />
    <button onclick="checkPassword()">إرسال</button>
    <div id="passwordMessage" class="message"></div>

    <div class="stars" id="stars"></div>

    <script>
      const correctPassword = "Nora06122007";
      let attempts = 5;

      function checkPassword() {
        const userInput = document.getElementById("passwordInput").value;
        const passwordMessage = document.getElementById("passwordMessage");

        if (userInput === correctPassword) {
          passwordMessage.style.color = "green";
          passwordMessage.innerHTML = `
            صحيح! لقد نجحت في تخمين كلمة المرور.<br>
            <b>ملاحظة:</b> من المهم استخدام كلمة مرور قوية وغير قابلة للتخمين.
          `;
          showStars();
        } else {
          attempts--;
          if (attempts > 0) {
            passwordMessage.style.color = "red";
            passwordMessage.textContent = `كلمة المرور غير صحيحة. لديك ${attempts} محاولات متبقية.`;
          } else {
            passwordMessage.style.color = "red";
            passwordMessage.textContent = "انتهت المحاولات! لقد خسرت التحدي.";
            document.getElementById("passwordInput").disabled = true;
          }
        }
      }

      function showStars() {
        const starsContainer = document.getElementById("stars");
        starsContainer.style.display = "block";
        starsContainer.innerHTML = ""; // تنظيف النجوم السابقة

        for (let i = 0; i < 30; i++) { // عدد النجوم: 30
          const star = document.createElement("div");
          star.classList.add("star");
          const size = Math.random() * 4 + 2; // حجم النجمة
          star.style.width = `${size}px`;
          star.style.height = `${size}px`;
          star.style.left = `${Math.random() * window.innerWidth}px`;
          star.style.top = `${Math.random() * window.innerHeight}px`;
          star.style.animationDuration = `${Math.random() * 0.8 + 0.5}s`;

          starsContainer.appendChild(star);
        }
      }
    </script>
  </body>
</html>
