# IPA Guide 交接文件

## 專案基本資訊

| 項目 | 內容 |
|------|------|
| 名稱 | 美式英語 IPA 國際音標指南 |
| GitHub | `jinshuanyu/ipa-guide` |
| 線上網址 | https://jinshuanyu.github.io/ipa-guide/ |
| 部署方式 | GitHub Pages（master branch） |
| 本機位置 | `D:\Projects\ipa-guide\` |

## 檔案結構

```
ipa-guide/
├── index.html              ← 整個頁面（HTML + CSS + JS 全內嵌）
├── audio/
│   ├── phonemes/            ← IPA 獨立音（母音 + 子音）
│   │   ├── e_long.mp3       ← /i/ 的音
│   │   ├── i_short.mp3      ← /ɪ/ 的音
│   │   ├── c1.mp3 ~ c24.mp3 ← 24 個子音
│   │   └── ...
│   └── words/               ← 例字發音
│       ├── beet.mp3 ~ yet.mp3
│       └── ...（共 40 個）
└── HANDOFF.md               ← 本文件
```

## 音檔來源

### Phonemes（獨立音）
- 來自 `word-mapper/audio/phonemes/`，直接複製過來
- 用 Azure TTS 生成

### Words（例字）
- **27 個**來自 word-mapper 各資料夾（bit, bat, cat, boat 等）
- **13 個**是為 IPA Guide 新生成的（用 `D:\工作\工具\audio_helper\gen_pro.py`）

新生成的 13 個字：beet, bet, boot, bot, burt, bait, bout, pat, thing, beige, joke, wine, lean

## IPA 音標 → 音檔對照表

### 17 母音

| 音標 | phonemes 檔名 | 例字 | words 檔名 |
|------|---------------|------|------------|
| /i/ | e_long.mp3 | beet | beet.mp3 |
| /ɪ/ | i_short.mp3 | bit | bit.mp3 |
| /ɛ/ | e_short.mp3 | bet | bet.mp3 |
| /æ/ | a_short.mp3 | bat | bat.mp3 |
| /u/ | u_long.mp3 | boot | boot.mp3 |
| /ʊ/ | oo.mp3 | book | book.mp3 |
| /ɔ/ | aw.mp3 | bought | bought.mp3 |
| /ɑ/ | o_short.mp3 | bot | bot.mp3 |
| /ʌ/ | u_short.mp3 | but | but.mp3 |
| /ə/ | schwa.mp3 | about | about.mp3 |
| /ɝ/ | er_stressed.mp3 | Burt | burt.mp3 |
| /ɚ/ | er_unstressed.mp3 | bitter | bitter.mp3 |
| /eɪ/ | a_long.mp3 | bait | bait.mp3 |
| /aɪ/ | i_long.mp3 | bite | bite.mp3 |
| /oʊ/ | o_long.mp3 | boat | boat.mp3 |
| /ɔɪ/ | oi.mp3 | boy | boy.mp3 |
| /aʊ/ | ow.mp3 | bout | bout.mp3 |

### 24 子音

| 音標 | phonemes 檔名 | 例字 | words 檔名 |
|------|---------------|------|------------|
| /p/ | c1.mp3 | pat | pat.mp3 |
| /b/ | c2.mp3 | bat | bat.mp3 |
| /t/ | c3.mp3 | toe | toe.mp3 |
| /d/ | c4.mp3 | dead | dead.mp3 |
| /k/ | c5.mp3 | cat | cat.mp3 |
| /g/ | c6.mp3 | got | got.mp3 |
| /f/ | c7.mp3 | face | face.mp3 |
| /v/ | c8.mp3 | vet | vet.mp3 |
| /θ/ | c9.mp3 | thing | thing.mp3 |
| /ð/ | c10.mp3 | this | this.mp3 |
| /s/ | c11.mp3 | sell | sell.mp3 |
| /z/ | c12.mp3 | zebra | zebra.mp3 |
| /ʃ/ | c13.mp3 | ship | ship.mp3 |
| /ʒ/ | c14.mp3 | beige | beige.mp3 |
| /tʃ/ | c15.mp3 | chair | chair.mp3 |
| /dʒ/ | c16.mp3 | joke | joke.mp3 |
| /h/ | c17.mp3 | happy | happy.mp3 |
| /m/ | c18.mp3 | mom | mom.mp3 |
| /n/ | c19.mp3 | need | need.mp3 |
| /ŋ/ | c20.mp3 | sing | sing.mp3 |
| /l/ | c21.mp3 | lean | lean.mp3 |
| /r/ | c22.mp3 | red | red.mp3 |
| /w/ | c23.mp3 | wine | wine.mp3 |
| /j/ | c24.mp3 | yet | yet.mp3 |

## 播放設定

- 播放速度：`playbackRate = 0.75`（在 `<script>` 區塊中設定）
- 如需調整速度，搜尋 `playbackRate` 即可找到

## 生成新音檔

使用 `D:\工作\工具\audio_helper\gen_pro.py`：

1. 在 `D:\工作\工具\audio_helper\` 建立 JSON 檔：
   ```json
   {
     "items": [
       {"word": "新單字1"},
       {"word": "新單字2"}
     ]
   }
   ```
2. 執行：`PYTHONIOENCODING=utf-8 python gen_pro.py`
3. 音檔會生成在同名資料夾裡
4. 把 mp3 複製到 `ipa-guide/audio/words/`

## 互連 Footer

以下工具的 footer 已加入 IPA Guide 連結：

| 工具 | 檔案位置 | 語法 |
|------|---------|------|
| word-mapper | `index.html` | 純 HTML |
| vowel-detective | `src/App.jsx` | JSX（className） |
| englishplaylistsforkids | `index.html` | 純 HTML |
| grow-a-sentence | `index.html` | 純 HTML |
| ipa-guide | `index.html` | 純 HTML（SVG icon） |

**注意：** Dolch-List-by-spelling-patterns 目前沒有互連 footer。

### 新增工具時的互連更新步驟

1. 在新工具的 footer 加上所有其他工具的連結（不含自己）
2. 到上面每個工具的 footer 加上新工具的連結
3. 各自 commit + push

## 部署流程

```bash
cd D:\Projects\ipa-guide
git add .
git commit -m "描述修改內容"
git push
```

Push 後 GitHub Pages 會自動部署，約 1-2 分鐘生效。
