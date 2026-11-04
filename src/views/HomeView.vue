<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isDismissed = ref(false)
let timer: ReturnType<typeof setTimeout> | null = null

function handleBlur() {
  // 使用者點擊 iframe (例如點選開啟聲音或操作播放器) 時觸發 blur 淡出
  isDismissed.value = true
}

onMounted(() => {
  window.addEventListener('blur', handleBlur)
  // 15 秒後若未互動也平滑淡出，不干擾觀看
  timer = setTimeout(() => {
    isDismissed.value = true
  }, 15000)
})

onUnmounted(() => {
  window.removeEventListener('blur', handleBlur)
  if (timer) clearTimeout(timer)
})
</script>

<template>
  <main class="page-shell">
    <div class="player-container">
      <!-- 框外大箭頭：直接對準右上角靜音按鈕 -->
      <div
        class="outer-arrow-wrapper"
        :class="{ 'is-dismissed': isDismissed }"
        aria-hidden="true"
      >
        <svg
          class="big-arrow-svg"
          viewBox="0 0 32 32"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M16 4V24M16 24L7 15M16 24L25 15"
            stroke="#ef4444"
            stroke-width="4.5"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
      </div>

      <!-- 影片播放器卡片 -->
      <section class="video-card">
        <div class="video-wrapper">
          <iframe
            src="https://www.youtube.com/embed/vbQV4AsDTiY?autoplay=1&mute=1&playsinline=1&rel=0"
            title="YouTube video player"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            referrerpolicy="strict-origin-when-cross-origin"
            allowfullscreen
          ></iframe>
        </div>
      </section>
    </div>
  </main>
</template>

<style scoped>
.page-shell {
  display: flex;
  min-height: 100svh;
  align-items: center;
  justify-content: center;
  padding: 80px 20px 40px;
  background:
    radial-gradient(ellipse at 50% 0%, rgb(216 230 255 / 60%), transparent 55%),
    #f5f7fb;
  box-sizing: border-box;
}

.player-container {
  position: relative;
  width: min(100%, 960px);
}

/* 框外上方大箭頭定位 */
.outer-arrow-wrapper {
  position: absolute;
  bottom: 100%;
  right: 142px;
  transform: translateX(50%);
  margin-bottom: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;
  z-index: 20;
  animation: bounce-down 1.4s infinite ease-in-out;
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.outer-arrow-wrapper.is-dismissed {
  opacity: 0;
  transform: translateX(50%) translateY(-10px);
}

.big-arrow-svg {
  width: 54px;
  height: 54px;
  filter: drop-shadow(0 4px 10px rgba(239, 68, 68, 0.45));
}

/* 箭頭上下彈跳動畫 */
@keyframes bounce-down {
  0%, 100% {
    transform: translateX(50%) translateY(0);
  }
  50% {
    transform: translateX(50%) translateY(10px);
  }
}

.video-card {
  width: 100%;
  overflow: hidden;
  border-radius: 20px;
  background: #000000;
  box-shadow: 0 24px 64px rgb(31 57 91 / 16%);
}

.video-wrapper {
  position: relative;
  width: 100%;
  aspect-ratio: 16 / 9;
  background: #000000;
}

.video-wrapper iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 0;
}

/* 行動版適配 */
@media (max-width: 640px) {
  .page-shell {
    padding: 60px 12px 24px;
  }

  .video-card {
    border-radius: 14px;
  }

  .outer-arrow-wrapper {
    right: 116px;
    margin-bottom: 8px;
  }

  .big-arrow-svg {
    width: 40px;
    height: 40px;
  }
}
</style>
