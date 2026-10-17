# u6vu06Ou

> 這裡的所有專案都圍繞同一個主題：變省。故事得從想省 token 說起。

## 一切從想省 token 開始

我很早就發現，Claude Code、Codex 這些外殼（harness）本身就非常強。同樣一個模型，用不出名的模型 API 很便宜，做出來的東西卻差強人意；但只要把它放進這些外殼裡跑，非主流模型也像開了竅，做事順得多。於是我做了第一件東西：[claude-team-router](https://github.com/u6vu06Ou/claude-team-router)——一層路由，把便宜的模型 API 接進這些外殼，當成主力來用。這類工具外面早有現成的（claude-code-router、LiteLLM 之類），這個只是我自己用順手的版本。

外殼接好了，下一個麻煩是視窗。Claude Code 開一堆、Codex 開一堆，桌面亂得自己看了都難受，所以我寫了自己的終端機 [coterm](https://github.com/u6vu06Ou/coterm)，專門對付「同時開著好幾個 AI 在跑」的日子。

而非主流模型出錯率高：一個模型鑽進死胡同，後面全跟著歪。乾脆把幾個模型串成一場會議，互相提案、互相審查、再決議——這就是 [llm-council](https://github.com/u6vu06Ou/llm-council)。

這下可以安心開很多視窗了，輪到電腦運作不良：記憶體、CPU 經常被吃滿。[parallel-guard](https://github.com/u6vu06Ou/parallel-guard) 讓 AI 在派生子代理之前先看一眼這台機器的狀況（同一台電腦所有視窗合計一個上限），資源不夠就緩一緩；用完的 git 工作副本也能一鍵安全收掉。

## 最爽的玩法：讓最聰明的模型當隊長

用了一陣子還是不過癮——花費少、用得開心，但畢竟不是最聰明的模型在帶領。於是我用 claude-team-router 做出等同原生 agent team 的多工派工：一線主流模型當隊長，其他便宜模型當隊員。

![claude team 模式的視窗徽章](assets/claude-team-badge.png)

終端機頂上這個徽章，標示「這個視窗是 claude team 模式」。前提是大家穿的都是 Claude Code（或 Codex）這套外殼，才能互相呼叫、用 @名字 精簡地傳話。因為監督的是主力模型，成果品質很高；而且看著終端機裡的用量條跑了一整個早上才增加幾個百分點，說不出的舒服。隊長還可以一直待命：你不用一次把計畫想完、寫死嚴格的 prompt，想到什麼講什麼，它都接收並派工，比以前從容太多。Codex 那邊也有同樣一套，即將開源。

## 把價格打下來之後，才敢放開手玩

終端機本來有「自動續快取」——快取到期前用極短的一句話延續，享受較低的快取價。但我發現自己很少真的用到，不如把錢花在刀口上。剛好 Claude Code 推出 mods，就寫了一個 auto-compact（即將開源）：55 分鐘自動壓縮對話，視窗底部顯示倒數。從此幾乎不再付快取以外的原價，終於可以用語音一直 vibe coding，很 chill。

## 一些小插曲

[time-sense](https://github.com/u6vu06Ou/time-sense)：讓 AI 知道現在幾點、你離開了多久、它自己做事情實際花了多久，不再用人類工作天估時間。
[chrome-md](https://github.com/u6vu06Ou/chrome-md)：把瀏覽器裡看的網頁存成給 AI 讀的 Markdown 的小擴充。
[learned-rules](https://github.com/u6vu06Ou/learned-rules)：讓 AI 從自己踩過的坑裡學習，開場只給標題目錄、需要的時候才展開，越用越聰明，還附帶到期提醒。

這些都只是過程中順手做的小東西，喜歡的話也可以叫你的 AI 幫你做一個。

## 專案一覽

| 專案 | 一句話 | 連結 |
|---|---|---|
| claude-team-router | 把便宜的模型 API 接進 Claude Code／Codex 外殼的路由 | [github.com/u6vu06Ou/claude-team-router](https://github.com/u6vu06Ou/claude-team-router) |
| coterm | 為「同時開好幾個 AI」而寫的終端機 | [github.com/u6vu06Ou/coterm](https://github.com/u6vu06Ou/coterm) |
| llm-council | 讓幾個模型開會、互相審查並決議 | [github.com/u6vu06Ou/llm-council](https://github.com/u6vu06Ou/llm-council) |
| parallel-guard | AI 派生子代理前先檢查機器資源，防止電腦被吃爆 | [github.com/u6vu06Ou/parallel-guard](https://github.com/u6vu06Ou/parallel-guard) |
| time-sense | 讓 AI 有時間感：現在幾點、離開多久、實際花了多久 | [github.com/u6vu06Ou/time-sense](https://github.com/u6vu06Ou/time-sense) |
| chrome-md | 把網頁存成給 AI 讀的 Markdown 的 Chrome 擴充 | [github.com/u6vu06Ou/chrome-md](https://github.com/u6vu06Ou/chrome-md) |
| learned-rules | 讓 AI 從自己踩過的坑學習，開場只給標題目錄 | [github.com/u6vu06Ou/learned-rules](https://github.com/u6vu06Ou/learned-rules) |
| Codex 版 team 派工 | team 機制的 Codex 對應版 | 即將開源 |
| auto-compact | 55 分鐘自動壓縮對話、視窗底部倒數的 mod | 即將開源 |

## English

Everything here started with wanting to spend fewer tokens. I found that lesser-known, cheap models become much more useful once they run inside the Claude Code or Codex harness, so I built [claude-team-router](https://github.com/u6vu06Ou/claude-team-router) to route cheap model APIs into those harnesses (projects like claude-code-router and LiteLLM exist—this is just my personal take). [coterm](https://github.com/u6vu06Ou/coterm) is the terminal I wrote for juggling many AI windows at once; [llm-council](https://github.com/u6vu06Ou/llm-council) has several models review each other's work; [parallel-guard](https://github.com/u6vu06Ou/parallel-guard) stops AI agents from spawning when your machine's resources are already maxed out. Most fun of all: a frontier model acts as team lead delegating to cheaper models—all sharing the same harness, calling each other by @name—while an auto-compact mod (open-sourcing soon) keeps sessions cheap enough to vibe code by voice all day. The odds and ends ([time-sense](https://github.com/u6vu06Ou/time-sense), [chrome-md](https://github.com/u6vu06Ou/chrome-md), [learned-rules](https://github.com/u6vu06Ou/learned-rules)) are things I made along the way; feel free to ask your AI to build you one too.
