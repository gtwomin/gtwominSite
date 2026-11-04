<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isDismissed = ref(false)
let timer: ReturnType<typeof setTimeout> | null = null

function handleBlur() {
  // 當使用者點擊 iframe (例如操作影片、開聲音、暫停等)，焦點切換到 iframe 觸發 blur
  isDismissed.value = true
}

onMounted(() => {
  window.addEventListener('blur', handleBlur)
  // 若 12 秒後未互動也平滑淡出，避免遮擋影片
  timer = setTimeout(() => {
    isDismissed.value = true
  }, 12000)
})

onUnmounted(() => {
  window.removeEventListener('blur', handleBlur)
  if (timer) clearTimeout(timer)
})
</script>

<template>
  <main class="page-shell">
    <section class="video-card">
      <div class="video-wrapper">
        <iframe
          src="https://www.youtube.com/embed/vbQV4AsDTiY?autoplay=1&mute=1&playsinline=1&rel=0"
          title="YouTube video player"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          referrerpolicy="strict-origin-when-cross-origin"
          allowfullscreen
        ></iframe>

        <!-- 箭頭與開聲音提示 -->
        <div class="sound-hint" :class="{ 'is-dismissed': isDismissed }">
          <div class="hint-arrow" aria-hidden="true">
            <svg
              viewBox="0 0 24 24"
              class="arrow-svg"
              fill="none"
              stroke="currentColor"
              stroke-width="3"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <line x1="12" y1="19" x2="12" y2="5" />
              <polyline points="5 12 12 5 19 12" />
            </svg>
          </div>
          <div class="hint-bubble">
            <span>開聲音</span>
            <span class="speaker-emoji">🔊</span>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.page-shell {
  display: grid;
  min-height: 100svh;
  place-items: center;
  padding: 24px 16px;
  background:
    radial-gradient(ellipse at 50% 0%, rgb(216 230 255 / 60%), transparent 55%),
    #f5f7fb;
  box-sizing: border-box;
}

.video-card {
  width: min(100%, 960px);
  overflow: hidden;
  border-radius: 20px;
  background: #000000;
  box-shadow: 0 24px 64px rgb(31 57 91 / 15%);
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

/* 提示開聲音箭頭與氣泡樣式 */
.sound-hint {
  position: absolute;
  top: 52px;
  right: 64px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  pointer-events: none;
  z-index: 10;
  animation: float-pulse 1.8s infinite ease-in-out;
  transition: opacity 0.5s ease, transform 0.5s ease;
}

.sound-hint.is-dismissed {
  opacity: 0;
  transform: translateY(8px);
  pointer-events: none;
}

.hint-arrow {
  display: flex;
  align-items: center;
  justify-content: center;
  color: #ef4444;
  filter: drop-shadow(0 2px 6px rgba(0, 0, 0, 0.7));
}

.arrow-svg {
  width: 24px;
  height: 24px;
}

.hint-bubble {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 6px 14px;
  border-radius: 999px;
  background: linear-gradient(135deg, #ef4444, #dc2626);
  color: #ffffff;
  font-size: 13px;
  font-weight: 700;
  letter-spacing: 0.05em;
  box-shadow: 0 4px 16px rgba(239, 68, 68, 0.5);
  white-space: nowrap;
  user-select: none;
}

.speaker-emoji {
  font-size: 14px;
}

@keyframes float-pulse {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-8px);
  }
}

@media (max-width: 640px) {
  .page-shell {
    padding: 12px;
  }

  .video-card {
    border-radius: 14px;
  }

  .sound-hint {
    top: 42px;
    right: 48px;
    gap: 2px;
  }

  .arrow-svg {
    width: 20px;
    height: 20px;
  }

  .hint-bubble {
    padding: 4px 10px;
    font-size: 11px;
  }

  .speaker-emoji {
    font-size: 12px;
  }
}
</style>
