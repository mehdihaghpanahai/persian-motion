# persian-motion

اسکیل رایگان Claude Code برای ساخت **موشن‌گرافیک فارسی** (متن راست‌به‌چپ) برای ریلز و شورتس.
A free Claude Code skill for building **Persian (RTL) text-motion videos** for Reels / Shorts.

[فارسی](#فارسی) · [English](#english)

---

## فارسی

### این اسکیل چیه؟

وقتی از Claude موشن فارسی می‌خوای، معمولا همین مشکل‌ها پیش میاد:

- کلمه‌ها برعکس می‌شن (مخصوصا وقتی وسط جمله کلمه‌ی انگلیسی هست)
- علامت درصد کنار عدد جابه‌جا می‌شه
- حروف از هم باز می‌شن و چسبیده نیستن

این اسکیل قاعده‌های درست کار با متن فارسی رو به Claude یاد می‌ده و یه قالب آماده‌ی انیمیشن، رندر و ساخت صدا هم همراهش هست. خروجی یه ویدیوی MP4 عمودی (۱۰۸۰×۱۹۲۰) است.

### داخل پوشه چی هست؟

```
persian-motion/
├─ SKILL.md                      دستورالعمل اصلی (مراحل کار)
├─ references/
│  ├─ rtl-rules.md               ۱۴ قاعده‌ی متن فارسی و راست‌به‌چپ
│  └─ style-text-motion.md       راهنمای سبک بصری (کرم و نارنجی)
├─ assets/template.html          قالب صحنه‌ها (کلمه‌به‌کلمه، تایتل قدم‌ها)
├─ scripts/
│  ├─ preview.js                 پیش‌نمایش و گزارش سرریز متن
│  ├─ render.js                  رندر به MP4
│  ├─ audio.py                   ساخت افکت صوتی
│  └─ mux.sh                     چسباندن صدا به ویدیو
└─ examples/                     مثال درخواست، HTML و ویدیوی نمونه
```

### پیش‌نیازها

- [Claude Code](https://docs.claude.com/en/docs/claude-code)
- Node.js و پکیج `playwright` (به‌همراه Chromium: `npx playwright install chromium`)
- `ffmpeg`
- پایتون ۳ با `numpy` و `scipy` (فقط برای ساخت افکت صوتی)
- یه فونت فارسی. پیشنهاد: **Vazirmatn** (مجوز آزاد). فونت همراه این پروژه نیست.

اگه چیزی نصب نیست، همین رو به Claude Code بگو: «پیش‌نیازهای اسکیل persian-motion رو برام نصب کن».

### نصب

۱. این ریپو رو دانلود کن (Code ← Download ZIP) و باز کن.
۲. پوشه‌ی `persian-motion` رو توی مسیر زیر کپی کن:

- مک و لینوکس: `~/.claude/skills/`
- ویندوز: `%USERPROFILE%\.claude\skills\`

۳. Claude Code رو دوباره باز کن.

### استفاده

توی Claude Code بنویس:

> یه ریل ۲۰ ثانیه‌ای تکست‌موشن درباره‌ی ۳ اشتباه رایج توی پرامپت‌نویسی بساز. بدون زیرنویس، مراحل با تایتل.

Claude صحنه‌ها رو می‌نویسه، پیش‌نمایش می‌گیره، سرریزها رو درست می‌کنه و ویدیو رو رندر می‌کنه. مثال کامل داخل `examples/` هست.

### محدودیت‌ها و نکته‌ها

- اسکیل فقط با رندررِ خودش (Playwright و ffmpeg) تست شده. استفاده از قاعده‌هاش با فریم‌ورک‌های دیگه (مثل HyperFrames) تست نشده.
- رندر فریم‌به‌فریم انجام می‌شه، پس برای ویدیوی ۳۰ ثانیه‌ای چند دقیقه طول می‌کشه.
- صدا فقط افکت و پد ساده است. صدای گوینده یا موزیک رو خودت اضافه کن.
- هندل و رنگ‌ها داخل `assets/template.html` هستن؛ قبل از استفاده عوضشون کن.

### نکته‌ی امنیتی

اسکیل‌ها روی سیستم خودت اجرا می‌شن و می‌تونن اسکریپت داشته باشن. قبل از نصب هر اسکیل (از جمله این یکی)، فایل‌هاش رو بخون.

### مجوز

MIT. جزئیات توی فایل [LICENSE](LICENSE).

### ارتباط

مهدی حق‌پناه · اینستاگرام [@mehdihaghpanah](https://instagram.com/mehdihaghpanah) · [mehdihaghpanah.com](https://mehdihaghpanah.com)

---

## English

### What is this?

Asking an AI to build Persian motion graphics usually breaks in the same ways: reversed word order (especially with Latin words inside a Persian sentence), a misplaced percent sign, and disconnected letters.

This skill teaches Claude the correct handling of Persian/RTL text and ships a ready template, a frame-by-frame renderer and a simple sound generator. Output is a vertical MP4 (1080×1920).

### Contents

`SKILL.md` (workflow) · `references/` (14 RTL rules, style guide) · `assets/template.html` (scene template) · `scripts/` (preview with overflow check, render, audio, mux) · `examples/`.

### Requirements

- [Claude Code](https://docs.claude.com/en/docs/claude-code)
- Node.js + `playwright` with Chromium (`npx playwright install chromium`)
- `ffmpeg`
- Python 3 with `numpy` and `scipy` (sound effects only)
- A Persian font. Recommended: **Vazirmatn** (open license). No font is bundled.

### Install

1. Download this repo (Code → Download ZIP) and unzip it.
2. Copy the `persian-motion` folder into `~/.claude/skills/` (macOS/Linux) or `%USERPROFILE%\.claude\skills\` (Windows).
3. Restart Claude Code.

### Usage

Ask Claude Code, for example:

> Make a 20-second Persian text-motion reel about 3 common prompt-writing mistakes. No subtitles, steps shown as titles.

### Limitations

- Tested only with the renderer included here (Playwright + ffmpeg). Use with other HTML-video frameworks is untested.
- Rendering is frame by frame; a 30 s video takes a few minutes.
- Audio is limited to simple effects and a pad; add voice-over and music yourself.
- Handle and colors live in `assets/template.html`; change them before use.

### Security

Skills run on your machine and may include scripts. Read any skill's files before installing it, including this one.

### License

MIT, see [LICENSE](LICENSE).
