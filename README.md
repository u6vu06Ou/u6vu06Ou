# u6vu06Ou

> 一個喜歡玩 AI infra、又愛省錢的 vibe 玩家。這裡的東西全是 vibe coding 出來的：有價值的只有念頭，動手捏出來的都是 AI。
> 不是要推薦誰來用，只是樂於分享。覺得有趣就拿去，用不上也無所謂。故事從想省 token 開始。

## 一切從想省 token 開始

Claude Code、Codex 這些外殼（harness）非常強。反過來，用不出名的模型買 API 很便宜，但做出來的東西差強人意。後來發現一件事：把同一個便宜模型套上 Claude Code 或 Codex 的外殼，它就像開了竅，做事順多了。

於是 vibe 了一個 proxy：把便宜模型的 API 翻譯成 Claude Code 聽得懂的格式。這個 proxy 後來越長越大，現在連同下面會講的隊長／隊員分流、平行派工，一起整理在 [claude-team-router](https://github.com/u6vu06Ou/claude-team-router)。外面早有類似的工具（claude-code-router、LiteLLM 之類），這只是我自己用順手的版本。

## 視窗太多，就再 vibe 一個終端機

Claude Code 開一堆、Codex 開一堆，每個都是獨立視窗，桌面亂到自己看了都難受。所以又 vibe 了一個自己用的終端機 [coterm](https://github.com/u6vu06Ou/coterm)：一個視窗裡同時跑好幾個 AI，看得到每個在幹嘛。

便宜模型畢竟不是主流模型，出錯率高，一鑽進死胡同就一路歪下去。那就讓幾個模型開會：互相提案、互相挑錯、再一起決定，這是 [llm-council](https://github.com/u6vu06Ou/llm-council)。

可以放心開一堆視窗了，結果換電腦撐不住：記憶體、CPU 常常被吃滿。於是 vibe 了 [parallel-guard](https://github.com/u6vu06Ou/parallel-guard)：AI 要多派幫手之前，先看一眼這台電腦還撐不撐得住。同一台電腦所有視窗合計一個上限，做完的工作副本也能一鍵安全收掉。

## 想讓 AI 記得你，又不想每次開場就吃掉一大塊

想讓 AI 記得很多事，最直接的做法是開新對話時把記憶檔整份塞給它。問題是記得越多，還沒開口就先吃掉越多 context。再加上每個專案資料夾各記各的，根本管不動。

所以 vibe 了 [ai-memory](https://github.com/u6vu06Ou/ai-memory)：每晚把所有對話摘要進同一個 Obsidian 筆記庫，再像查資料庫一樣去搜，用關鍵字和意思一起找。AI 需要時才查，而且分兩步：先拿一張一行一筆的清單，真的用得到的才展開全文；查不到就直說沒有，不硬掰。結果是不管在哪個視窗、隔幾天再開口，都像在跟同一個記得你的人講話。

## 最爽的玩法：讓最聰明的模型當隊長

便宜模型用得很開心，但心裡總有個遺憾：帶頭的不是最聰明的那個。所以讓一線主流模型當隊長，便宜模型當隊員，做成跟原生 agent team 一樣的多工派工。Claude Code 用 [claude-team-router](https://github.com/u6vu06Ou/claude-team-router)，Codex 用 [codex-team](https://github.com/u6vu06Ou/codex-team)。

![claude team 模式的視窗徽章](assets/claude-team-badge.png)

這是我覺得操作 AI 大軍最爽的方法。前提是大家都穿同一套外殼（同一個 Claude Code 或同一個 Codex），才能互相呼叫，用 @名字 精簡地傳話。負責監督的是一線模型，所以最後成果品質很高；而終端機裡的用量條，跑了一整個早上才多幾個百分點，說不出的舒服。

還有一個沒想到的好處：隊長一直待命，所以不用一開始就把計畫想完、寫一份嚴格的 prompt。想到什麼就講什麼，它都接得住，會自己派下去。比起以前，舒服太多了。

## 把錢花在刀口上

終端機原本有「續快取」的機制：快取快過期前，用很短的一句話把它續下去，就能一直付比較便宜的快取價。後來發現自己很少用，不如閒著的時候直接把對話壓縮。剛好 Claude Code 推出了 mods，就 vibe 了一個「閒置 55 分鐘自動壓縮」的 mod。後來 Claude Code 自己內建了同樣的功能（快取過期前自動壓縮），這個 mod 就功成身退了。

從此幾乎不再付快取以外的原價，終於可以開著語音一直 vibe coding，很 chill。

## 一些小插曲

- [time-sense](https://github.com/u6vu06Ou/time-sense)：讓 AI 知道現在幾點、你離開了多久、它自己做事實際花了多久，不再用人類的工作天亂估時間。
- [chrome-md](https://github.com/u6vu06Ou/chrome-md)：把正在看的網頁存成給 AI 讀的 Markdown。
- [learned-rules](https://github.com/u6vu06Ou/learned-rules)：讓 AI 從自己踩過的坑學習。開場只給標題清單，需要才展開，還附到期提醒。

這些都是過程中冒出來的念頭。比起直接拿去用，更建議把念頭帶走，叫你的 AI 照你的習慣捏一個。

## 專案一覽

| 專案 | 一句話 |
|---|---|
| [claude-team-router](https://github.com/u6vu06Ou/claude-team-router) | 把任何 OpenAI 格式的模型接進 Claude Code；隊長走官方、隊員走你的模型 |
| [codex-team](https://github.com/u6vu06Ou/codex-team) | Codex 版的隊長＋常駐隊員，隊員之間可以直接傳話 |
| [coterm](https://github.com/u6vu06Ou/coterm) | 為「同時開好幾個 AI」而做的終端機 |
| [llm-council](https://github.com/u6vu06Ou/llm-council) | 讓幾個模型開會、互相審查再決議 |
| [parallel-guard](https://github.com/u6vu06Ou/parallel-guard) | 派幫手前先看電腦撐不撐得住；做完的工作副本一鍵收 |
| [ai-memory](https://github.com/u6vu06Ou/ai-memory) | 對話摘要進同一個筆記庫，兩步查詢，查不到就說沒有 |
| [time-sense](https://github.com/u6vu06Ou/time-sense) | 讓 AI 有時間感 |
| [chrome-md](https://github.com/u6vu06Ou/chrome-md) | 把網頁存成給 AI 讀的 Markdown |
| [learned-rules](https://github.com/u6vu06Ou/learned-rules) | 讓 AI 從踩過的坑學習 |

## English

An AI-infra tinkerer who likes spending less. Everything here was vibe coded: the ideas are mine, the code was shaped by AI. Not a pitch — just sharing; use it or don't. It started with wanting to spend fewer tokens. Cheap, lesser-known models get much better once they run inside the Claude Code or Codex harness, so I vibed a proxy that translates their APIs for Claude Code; it grew into [claude-team-router](https://github.com/u6vu06Ou/claude-team-router) (tools like claude-code-router and LiteLLM do similar things — this is just the one I use). Too many windows led to [coterm](https://github.com/u6vu06Ou/coterm), a terminal for running many agents side by side. Error-prone models led to [llm-council](https://github.com/u6vu06Ou/llm-council), where models review each other. A machine running out of RAM and CPU led to [parallel-guard](https://github.com/u6vu06Ou/parallel-guard). Wanting agents to remember a lot without loading a huge memory file into every new session led to [ai-memory](https://github.com/u6vu06Ou/ai-memory): conversations summarized nightly into one Obsidian vault, searched on demand in two steps, and it says "nothing found" instead of guessing. The most fun setup: a frontier model as team lead, cheaper models as teammates, all in the same harness talking by @name — [claude-team-router](https://github.com/u6vu06Ou/claude-team-router) for Claude Code, [codex-team](https://github.com/u6vu06Ou/codex-team) for Codex. The rest ([time-sense](https://github.com/u6vu06Ou/time-sense), [chrome-md](https://github.com/u6vu06Ou/chrome-md), [learned-rules](https://github.com/u6vu06Ou/learned-rules)) are small ideas from along the way — ask your AI to build you one too.
