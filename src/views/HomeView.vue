<template>
  <main class="page-shell">
    <section class="welcome" aria-labelledby="page-title">
      <header class="welcome-header">
        <a class="wordmark" href="/" aria-label="gtwomin 首頁">gtwomin<span>.</span></a>
        <div class="status-pill">
          <span class="status-dot" aria-hidden="true"></span>
          BUILD SUCCESS
        </div>
      </header>

      <div class="welcome-content">
        <div class="checkmark" aria-hidden="true">
          <svg viewBox="0 0 24 24" fill="none">
            <path d="m6.5 12.5 3.7 3.7 7.8-8" />
          </svg>
        </div>

        <p class="eyebrow">你的個人網站專案</p>
        <h1 id="page-title">建置成功<span>。</span></h1>
        <p class="description">
          專案已經準備就緒。接下來，就從你的第一個個人頁面開始。
        </p>
      </div>

      <footer class="welcome-footer">
        <div class="stack-heading">
          <span class="footer-label">PROJECT STACK</span>
          <span class="footer-caption">已安裝並完成設定</span>
        </div>
        <ul class="stack-list" aria-label="已設定的技術">
          <li>Vue 3</li>
          <li>TypeScript</li>
          <li>Pinia</li>
          <li>Vue Router</li>
        </ul>
        <p class="next-step">
          下一步：從 <code>src/views/HomeView.vue</code> 開始編輯首頁。
        </p>
      </footer>
    </section>
    <p class="page-note">BUILT WITH VITE <span>·</span> READY FOR YOUR IDEAS</p>
  </main>
</template>

<style scoped>
.page-shell {
  position: relative;
  display: grid;
  min-height: 100svh;
  place-items: center;
  overflow: hidden;
  padding: 48px 24px 28px;
  background:
    radial-gradient(ellipse at 50% 0%, rgb(216 230 255 / 55%), transparent 48%),
    #f5f7fb;
  color: #13253e;
}

.welcome {
  width: min(100%, 720px);
  overflow: hidden;
  border: 1px solid #e3e9f1;
  border-radius: 24px;
  background: rgb(255 255 255 / 94%);
  box-shadow: 0 28px 80px rgb(31 57 91 / 10%);
}

.welcome-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 26px 32px;
  border-bottom: 1px solid #edf0f5;
}

.wordmark {
  color: #142740;
  font-size: 18px;
  font-weight: 750;
  letter-spacing: -0.06em;
  text-decoration: none;
}

.wordmark span,
.welcome-content h1 span {
  color: #5278d8;
}

.status-pill {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 11px;
  border: 1px solid #d8eee4;
  border-radius: 999px;
  background: #f1faf5;
  color: #27734f;
  font-size: 10px;
  font-weight: 750;
  letter-spacing: 0.1em;
}

.status-dot {
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: #42a877;
  box-shadow: 0 0 0 3px rgb(66 168 119 / 13%);
}

.welcome-content {
  padding: 58px 64px 54px;
}

.checkmark {
  display: grid;
  width: 52px;
  height: 52px;
  margin-bottom: 29px;
  place-items: center;
  border-radius: 16px;
  background: #edf3ff;
  color: #4770d0;
}

.checkmark svg {
  width: 25px;
  stroke: currentColor;
  stroke-linecap: round;
  stroke-linejoin: round;
  stroke-width: 2;
}

.eyebrow,
.footer-label {
  margin: 0;
  color: #718097;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.13em;
  text-transform: uppercase;
}

.welcome-content h1 {
  margin: 12px 0 16px;
  color: #142740;
  font-size: clamp(42px, 8vw, 66px);
  font-weight: 750;
  letter-spacing: -0.075em;
  line-height: 1.08;
}

.description {
  max-width: 440px;
  margin: 0;
  color: #66758a;
  font-size: 16px;
  line-height: 1.8;
}

.welcome-footer {
  padding: 24px 32px 28px;
  border-top: 1px solid #edf0f5;
  background: #fbfcfe;
}

.stack-heading {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  gap: 12px;
}

.footer-label {
  font-size: 10px;
}

.footer-caption {
  color: #8a97a9;
  font-size: 12px;
}

.stack-list {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin: 14px 0 21px;
  padding: 0;
  list-style: none;
}

.stack-list li {
  padding: 8px 11px;
  border: 1px solid #e4e9f0;
  border-radius: 8px;
  background: #fff;
  color: #43536a;
  font-size: 12px;
  font-weight: 600;
}

.next-step {
  margin: 0;
  color: #718097;
  font-size: 12px;
  line-height: 1.7;
}

.next-step code {
  color: #3e5f9d;
  font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
  font-size: 0.95em;
}

.page-note {
  position: absolute;
  right: 24px;
  bottom: 18px;
  left: 24px;
  margin: 0;
  color: #93a0b2;
  font-size: 9px;
  font-weight: 700;
  letter-spacing: 0.16em;
  text-align: center;
}

.page-note span {
  padding: 0 5px;
  color: #5278d8;
}

@media (max-width: 560px) {
  .page-shell {
    padding: 20px 16px 48px;
  }

  .welcome {
    border-radius: 18px;
  }

  .welcome-header {
    padding: 20px;
  }

  .welcome-content {
    padding: 42px 24px 40px;
  }

  .welcome-footer {
    padding: 21px 20px 23px;
  }

  .footer-caption {
    font-size: 11px;
  }
}
</style>
