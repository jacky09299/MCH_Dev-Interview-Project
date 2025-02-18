<template>
  <div class="introduction">
    <header id="intro-header" class="intro-header">
      <!-- 內嵌 SVG 當作背景 -->
      <svg class="smile-bg" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 200" preserveAspectRatio="none">
        <rect width="800" height="200" fill="#6FB7B7"/>
        <circle cx="350" cy="80" r="20" fill="#00AEAE"/>
        <circle cx="450" cy="80" r="20" fill="#00AEAE"/>
        <!-- 初始狀態：平嘴巴 -->
        <path id="mouth" class="mouth" d="M330 150 Q400 150 470 150" stroke="#00AEAE" stroke-width="5" fill="none"/>
      </svg>
      <div class="header-content">
        <img src="./photo.jpg" alt="個人照片" class="intro-photo" />
        <div class="intro-content">
          <h2>自我介紹</h2>
          <p>
            我是李紘宇，目前就讀清華大學物理系大三，我很聰明，且喜歡嘗試有挑戰性的事物，以及學習不同領域的知識。我的自學能力強，程式幾乎都是自學來的。國中前，主要是學C++，後來高中因專題研究需要，有學一點Fortran，大學開始自學Python，目前Python是比較熟悉的語言。上學期跟著Chatgpt學習網站架設，因此基本的網站也會寫。
          </p>
        </div>
      </div>
    </header>
    <section class="about-section">
      <h3>個人資訊補充</h3>
      <ul>
        <li>國小、國中皆通過資賦優異鑑定</li>
        <li>國二錄取清大物理人才培育計畫，國中就在清大修完大學普物和普物實驗</li>
        <li>高中就讀建中科學班</li>
        <li>2023清華創業日優選，或2萬經費並代表清華比賽</li>
      </ul>
    </section>
  </div>
</template>

<style scoped>
.introduction {
  padding: 40px 20px;
  max-width: 1200px;
  margin: 0 auto;
}

.intro-header {
  position: relative;
  border-radius: 10px;
  padding: 30px;
  overflow: hidden;
}

/* 背景透明度 50% */
.smile-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  opacity: 0.5;
}

.header-content {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
}

.intro-photo {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  object-fit: cover;
  margin-right: 20px;
  border: 2px solid #656d73;
}

.intro-content {
  flex-grow: 1;
}

.intro-header h2 {
  font-size: 2rem;
  margin-bottom: 20px;
  color: #333;
}

.intro-header p {
  font-size: 1.2rem;
  line-height: 1.5;
  color: #555;
}

.about-section {
  margin-top: 40px;
  padding: 0 40px;
}

.about-section h3 {
  font-size: 1.6rem;
  margin-top: 20px;
  margin-bottom: 10px;
}

.about-section p {
  font-size: 1rem;
  line-height: 1.6;
}
</style>

<script>
// 請先確保已安裝 anime.js，例如：npm install animejs
import anime from 'animejs/lib/anime.es.js';

export default {
  mounted() {
    const header = document.getElementById('intro-header');
    const mouth = document.getElementById('mouth');
    let mouthAnimation;

    // 當滑鼠進入 header 時，啟動動畫：從直線變化成半圓形
    header.addEventListener('mouseenter', () => {
      if (!mouthAnimation) {
        mouthAnimation = anime({
          targets: mouth,
          d: [
            { value: "M330 150 Q400 150 470 150" },
            { value: "M330 140 Q400 199 470 140" }
          ],
          duration: 1000,
          easing: 'easeInOutSine'
        });
      }
    });

    // 當滑鼠離開 header 時，停止動畫並恢復直線
    header.addEventListener('mouseleave', () => {
      if (mouthAnimation) {
        mouthAnimation.pause();
        mouthAnimation = null;
      }
      mouth.setAttribute("d", "M330 150 Q400 150 470 150");
    });
  }
}
</script>
