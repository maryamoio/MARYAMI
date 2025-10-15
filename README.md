<!DOCTYPE html>
<html lang="fa">
<head>
<meta charset="UTF-8">
<title>Zoom Image on Click</title>
<style>
  body {
    font-family: Arial, sans-serif;
  }

  /* سبک تصویر کوچک */
  .thumbnail {
    width: 300px;
    cursor: pointer;
    transition: 0.3s;
  }

  .thumbnail:hover {
    opacity: 0.8;
  }

  /* لایه پس‌زمینه زوم */
  .overlay {
    position: fixed;
    display: none;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.8);
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  /* تصویر بزرگ زوم */
  .overlay img {
    max-width: 90%;
    max-height: 90%;
    border-radius: 10px;
    box-shadow: 0 0 20px #000;
  }

  /* دکمه بستن */
  .close-btn {
    position: fixed;
    top: 20px;
    right: 30px;
    font-size: 40px;
    color: #fff;
    cursor: pointer;
    z-index: 1001;
  }
</style>
</head>
<body>

<h2>روی عکس کلیک کن تا زوم شود</h2>
<img src="image.jpg" alt="عکس نمونه" class="thumbnail" id="myImg">

<!-- لایه زوم -->
<div class="overlay" id="overlay">
  <span class="close-btn" id="closeBtn">&times;</span>
  <img id="zoomedImg" src="">
</div>

<script>
  const thumbnail = document.getElementById('myImg');
  const overlay = document.getElementById('overlay');
  const zoomedImg = document.getElementById('zoomedImg');
  const closeBtn = document.getElementById('closeBtn');

  // وقتی روی عکس کوچک کلیک شد
  thumbnail.addEventListener('click', function() {
    zoomedImg.src = this.src;  // عکس بزرگ همان عکس کوچک
    overlay.style.display = 'flex';
  });

  // وقتی روی دکمه × کلیک شد، زوم بسته شود
  closeBtn.addEventListener('click', function() {
    overlay.style.display = 'none';
  });

  // اگر روی پس‌زمینه زوم کلیک شد، هم بسته شود
  overlay.addEventListener('click', function(e) {
    if(e.target === overlay) {
      overlay.style.display = 'none';
    }
  });
</script>

</body>
</html>
