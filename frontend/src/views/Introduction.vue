<template>
  <div class="introduction">
    <header id="intro-header" class="intro-header">
      <!-- 內嵌 SVG 當作背景：動態水流效果 -->
      <svg class="water-bg" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 200" preserveAspectRatio="none">
        <defs>
          <!-- 利用 clipPath 限制波浪只在區域內呈現 -->
          <clipPath id="clip">
            <rect width="800" height="200" />
          </clipPath>
        </defs>
        <!-- 背景色 -->
        <rect width="800" height="200" fill="#6FB7B7"/>
        <!-- 波浪群組 -->
        <g id="water-waves" clip-path="url(#clip)">
          <path id="wave1" fill="#00AEAE" opacity="0.6"></path>
          <path id="wave2" fill="#00BFBF" opacity="0.5"></path>
          <path id="wave3" fill="#00FFFF" opacity="0.4"></path>
        </g>
      </svg>
      <div class="header-content">
        <img src="./photo.jpg" alt="個人照片" class="intro-photo" />
        <div class="intro-content">
          <h2>自我介紹</h2>
          <div class="text-mask">
            <strong style="font-size: 20px;">
              我是李紘宇，目前就讀清華大學物理系大三，我很聰明，且喜歡嘗試有挑戰性的事物，以及學習不同領域的知識。我的自學能力強，程式幾乎都是自學來的。國中前，主要是學C++，後來高中因專題研究需要，有學一點Fortran，大學開始自學Python，目前Python是比較熟悉的語言。上學期跟著Chatgpt學習網站架設，因此基本的網站也會寫。
            </strong>
          </div>
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
        <li>目前在超導量子電路實驗室做專題研究</li>
      </ul>
    </section>
  </div>
</template>

<style scoped>
.introduction {
  padding: 40px 20px;
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
}

.intro-header {
  position: relative;
  border-radius: 10px;
  padding: 30px;
  overflow: hidden;
}

/* 讓 SVG 背景覆蓋整個 header */
.water-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  opacity: 0.7;
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

.text-mask {
    font-size: 12px;
    font-weight: bold;
    text-align: left;
    color: transparent; /* 文字顏色設為透明 */
    background: url('boat.jfif') no-repeat center;
    background-size: 300%; /* 縮小背景圖案的大小 */
    -webkit-background-clip: text; /* 將背景限制在文字內 */
    background-clip: text; /* 現代瀏覽器的標準屬性 */
}

</style>

<script>
import anime from 'animejs/lib/anime.es.js';

export default {
  mounted() {
    const header = document.getElementById('intro-header');
    const wave1 = document.getElementById('wave1');
    const wave2 = document.getElementById('wave2');
    const wave3 = document.getElementById('wave3');
    const svgWidth = 800;
    const svgHeight = 200;
    const margin = 50; // 左右各延伸 50px，確保波浪延伸至畫面外

    // 用於持續累加的變數，保留當前 phase 值
    const dummy = { t: 0 };
    let waveAnimation = null;

    // 根據參數產生波浪的 path，x 從 -margin 到 svgWidth + margin
    function generateWavePath(amplitude, wavelength, phase, baseHeight) {
      const startX = -margin;
      const endX = svgWidth + margin;
      let path = `M${startX} ${svgHeight}`; // 從左下角開始
      path += ` L${startX} ${baseHeight}`;
      const step = 10;
      for (let x = startX; x <= endX; x += step) {
        let y = amplitude * Math.sin((2 * Math.PI / wavelength) * x + phase) + baseHeight;
        path += ` L${x} ${y}`;
      }
      path += ` L${endX} ${svgHeight} Z`;
      return path;
    }

    // 啟動動畫（或從暫停狀態繼續）
    function startAnimation() {
      if (waveAnimation) {
        waveAnimation.play();
      } else {
        waveAnimation = anime({
          targets: dummy,
          t: dummy.t + 2 * Math.PI * 10000000, // 從當前 t 值持續累加
          duration: 2000 * 10000000,
          easing: 'linear',
          loop: true,
          update: function() {
            const t = dummy.t;
            // 利用不同參數產生三條波浪，以不同相位偏移營造層次
            wave1.setAttribute('d', generateWavePath(10, 200, t, 150));
            wave2.setAttribute('d', generateWavePath(8, 180, t * 1.2, 160));
            wave3.setAttribute('d', generateWavePath(6, 160, t * 0.8, 170));
          }
        });
      }
    }
    // 設定靜止的初始波浪狀態
    wave1.setAttribute('d', generateWavePath(10, 200, 0, 150));
    wave2.setAttribute('d', generateWavePath(8, 180, 0, 160));
    wave3.setAttribute('d', generateWavePath(6, 160, 0, 170));
    // 滑鼠移入時啟動或繼續動畫
    header.addEventListener('mouseenter', startAnimation);

    // 滑鼠移出時僅暫停動畫，保留當前波浪狀態
    header.addEventListener('mouseleave', () => {
      if (waveAnimation) {
        waveAnimation.pause();
      }
    });
  }
}
</script>
