<template>
  <main class="page-shell">
    <section class="video-card">
      <header class="video-header">
        <a class="wordmark" href="/" aria-label="gtwomin 首頁">gtwomin<span>.</span></a>
        <div class="status-pill">
          <span class="status-dot" aria-hidden="true"></span>
          AUTOPLAY
        </div>
      </header>

      <div class="video-wrapper">
        <iframe
          src="https://www.youtube.com/embed/vbQV4AsDTiY?autoplay=1&mute=1&playsinline=1&rel=0"
          title="YouTube video player"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          referrerpolicy="strict-origin-when-cross-origin"
          allowfullscreen
        ></iframe>
      </div>

      <footer class="video-footer">
        <div class="sound-tip">
          <svg class="tip-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M11 5L6 9H2v6h4l5 4V5z" />
            <path d="M15.54 8.46a5 5 0 0 1 0 7.07" />
            <path d="M19.07 4.93a10 10 0 0 1 0 14.14" />
          </svg>
          <p class="tip-text">
            <strong>瀏覽器播放限制說明：</strong>
            根據 Chrome / Safari / Edge 等現代瀏覽器的自動播放政策，網頁進場自動播放<strong>必須預設靜音 (Mute)</strong>；如需聲音，請直接點擊影片播放列上的喇叭按鈕解除靜音。
          </p>
        </div>
      </footer>
    </section>
  </main>
</template>

<style scoped>
.page-shell {
  display: grid;
  min-height: 100svh;
  place-items: center;
  padding: 32px 20px;
  background:
    radial-gradient(ellipse at 50% 0%, rgb(216 230 255 / 60%), transparent 55%),
    #f5f7fb;
  color: #13253e;
  box-sizing: border-box;
}

.video-card {
  width: min(100%, 960px);
  overflow: hidden;
  border: 1px solid #e3e9f1;
  border-radius: 20px;
  background: #ffffff;
  box-shadow: 0 24px 64px rgb(31 57 91 / 10%);
}

.video-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 18px 24px;
  border-bottom: 1px solid #edf0f5;
}

.wordmark {
  color: #142740;
  font-size: 18px;
  font-weight: 750;
  letter-spacing: -0.06em;
  text-decoration: none;
}

.wordmark span {
  color: #5278d8;
}

.status-pill {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 12px;
  border: 1px solid #d8eee4;
  border-radius: 999px;
  background: #f1faf5;
  color: #27734f;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.08em;
}

.status-dot {
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: #42a877;
  box-shadow: 0 0 0 3px rgb(66 168 119 / 18%);
}

.video-wrapper {
  position: relative;
  width: 100%;
  aspect-ratio: 16 / 9;
  background: #000;
}

.video-wrapper iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border: 0;
}

.video-footer {
  padding: 16px 24px;
  border-top: 1px solid #edf0f5;
  background: #fbfcfe;
}

.sound-tip {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  color: #5a6a80;
  font-size: 13px;
  line-height: 1.6;
}

.tip-icon {
  width: 20px;
  height: 20px;
  flex-shrink: 0;
  margin-top: 2px;
  stroke: #5278d8;
}

.tip-text {
  margin: 0;
}

.tip-text strong {
  color: #1f3350;
}

@media (max-width: 640px) {
  .page-shell {
    padding: 16px 12px;
  }

  .video-card {
    border-radius: 14px;
  }

  .video-header {
    padding: 14px 18px;
  }

  .video-footer {
    padding: 14px 18px;
  }

  .sound-tip {
    font-size: 12px;
  }
}
</style>
