<!DOCTYPE html>
<html lang="zh-Hant">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hydra Juice</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link
    href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;700&family=Playfair+Display:wght@700&display=swap"
    rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">

  <style>
    /* --- 整體頁面樣式 --- */
    body {
      margin: 0;
      font-family: 'Noto Sans TC', sans-serif;
      background-color: #4A5443;
      /* 主要背景色 */
      display: flex;
      justify-content: center;
      align-items: flex-start;
      /* 從頂部對齊 */
      min-height: 100vh;
      padding: 40px 20px;
      /* 增加左右邊距 */
      box-sizing: border-box;
      /* 確保 padding 不會影響寬度計算 */
    }

    /* --- 主要容器 --- */
    .container {
      width: 100%;
      max-width: 680px;
      text-align: center;
      color: #EFEFEF;
      /* 主要文字顏色 */
    }

    /* --- 頁首區塊 --- */
    header {
      margin-bottom: 30px;
    }

    .profile-pic {
      width: 96px;
      height: 96px;
      border-radius: 50%;
    }

    .title {
      font-family: 'Playfair Display', serif;
      font-style: italic;
      font-size: 28px;
      margin: 20px 0 10px 0;
      color: #FFFFFF;
      /* 標題白色 */
    }

    .description {
      font-size: 16px;
      margin: 0;
      color: #D3D3D3;
      /* 描述文字顏色 */
    }

    /* --- 連結按鈕 --- */
    .links {
      display: flex;
      flex-direction: column;
      gap: 16px;
      /* 按鈕間的距離 */
    }

    .link-button {
      background-color: #CACAAE;
      /* 按鈕背景色 */
      color: #333333;
      /* 按鈕文字顏色 */
      text-decoration: none;
      padding: 18px 20px;
      border-radius: 40px;
      /* 圓角 */
      font-size: 16px;
      font-weight: 700;
      transition: transform 0.2s ease, background-color 0.2s ease;
    }

    .link-button:hover {
      background-color: #B9B99E;
      /* 滑鼠懸停時的顏色 */
      transform: scale(1.03);
      /* 輕微放大效果 */
    }

    /* --- 頁尾 --- */
    footer {
      margin-top: 40px;
    }

    .social-icons {
      margin-bottom: 20px;
    }

    .social-icons a {
      color: #CACAAE;
      /* 圖示顏色 */
      font-size: 24px;
      margin: 0 15px;
      text-decoration: none;
      transition: color 0.2s ease;
    }

    .social-icons a:hover {
      color: #FFFFFF;
      /* 滑鼠懸停時的顏色 */
    }

    .footer-text {
      font-family: 'Playfair Display', serif;
      font-size: 22px;
      color: #FFFFFF;
      margin-top: 40px;
      margin-bottom: 40px;
    }
  </style>
</head>

<body>

  <div class="container">
    <header>
      <img src="logo.png" alt="Hydra Logo" class="profile-pic">
      <h1 class="title">Hydra Juice</h1>
      <p class="description">Your daily dose of vitamin C</p>
    </header>

    {% comment %} --- Jekyll 邏輯開始 --- {% endcomment %}
    {% assign pages_to_show = site.pages | where_exp: "p", "p.title" | where_exp: "p", "p.url != page.url" %}

    <main class="links">
      {% for item in pages_to_show %}
        <a href="{{ site.baseurl }}{{ item.url }}" class="link-button">{{ item.title }}</a>
      {% endfor %}
    </main>
    
    {% comment %} --- Jekyll 邏輯結束 --- {% endcomment %}

    <footer>
      <div class="social-icons">
        <a href="#"><i class="fab fa-tiktok"></i></a>
        <a href="#"><i class="fab fa-spotify"></i></a>
        <a href="#"><i class="fab fa-youtube"></i></a>
      </div>
      <p class="footer-text">Artemis</p>
    </footer>
  </div>

</body>

</html>
