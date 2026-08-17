# Git 入門課程 — 作業繳交 repo

這是課程作業用的公開 repo。

| | |
|---|---|
| **繳交期限** | 9 月 2 日（三）23:59 |
| **完成標準** | 發出 Pull Request，內容確認沒問題就算完成 |

**請不要直接推送到這裡**，你也沒有權限這樣做。
交作業的方式是 **Fork + Pull Request**，這也是所有開源專案的標準流程。

---

## 作業內容

在 `students/` 資料夾底下，新增一個屬於你的 Markdown 檔案，
裡面寫 **2 行**自我介紹，或是今天學到的 Git 指令。

檔名用你的名字，例如 `students/王小明.md`。

---

## 繳交步驟

### 步驟 1：Fork

1. 在這個頁面的右上角按 **Fork** → **Create fork**
2. 完成後你會被帶到一個新頁面，網址變成
   `https://github.com/你的帳號/git-class-homework`

> 這份才是**你的**，你在上面有完整權限，想怎麼改都可以。

### 步驟 2：Clone 到你的電腦

在**你自己那一份**的頁面上按綠色的 **Code** 按鈕，複製網址，然後：

```bash
git clone <你 fork 後的網址>
cd git-class-homework
```

> ⚠️ 最常見的錯誤：clone 到這個原始 repo。
> 檢查一下網址裡是不是**你自己的帳號名**。

### 步驟 3：開一個自己的分支

```bash
git switch -c 你的名字-intro
```

例如：`git switch -c 王小明-intro`

### 步驟 4：新增檔案並 commit

在 `students/` 底下建立 `你的名字.md`，寫好內容之後：

```bash
git add students/你的名字.md
git commit -m "Add my intro"
```

### 步驟 5：Push 到你的 fork

```bash
git push -u origin 你的名字-intro
```

> 這裡的 `origin` 是**你的 fork**，不是這個原始 repo，所以你 push 得上去。

**第一次 push 會要求登入 GitHub**，這是正常的，不是你做錯了。
畫面上會跳出一個視窗，選 **Sign in with your browser**，
瀏覽器登入一次之後就會記住，之後不會再問。

> 如果視窗被你不小心關掉，或是一直登入失敗，
> 重新執行一次 `git push` 就會再跳出來。

### 步驟 6：發 Pull Request

1. push 完回到 GitHub，頁面上方會出現 **Compare & pull request** 按鈕
2. 按下去，確認方向是「**你的分支 → 原始 repo 的 `main`**」
3. 填個標題（例如 `Add 王小明 intro`），按 **Create pull request**

```text
Fork → Clone → Branch → Commit → Push → Pull Request → Merge
```

---

## 交件標準

- **繳交期限：9 月 2 日（三）23:59**
- **發出 PR、內容確認沒問題，作業就算完成。**
- 如果有地方需要修改，會直接在你的 PR 底下留言。
  不用重開 PR——在**同一個分支**再 commit + push 一次，PR 會自動更新。

---

## 檔案格式

`students/example.md` 是範例檔，可以打開來看格式，但**不要修改它**，
請自己另外開一個檔案。

內容大概像這樣就可以：

```markdown
# 王小明

- 資工系二年級，之前完全沒用過版本控制。
- 今天學到最有用的指令是 `git status`，可以隨時看目前改了什麼。
```

---

## 常見狀況

| 狀況 | 原因 | 怎麼辦 |
|------|------|--------|
| 第一次 `push` 跳出登入視窗 | 需要 GitHub 身分驗證，正常現象 | 選 **Sign in with your browser**，登入一次就會記住 |
| 終端機顯示 `"students/\347\216\213..."` | 中文檔名被跳脫顯示 | `git config --global core.quotepath false` |
| `push` 出現 403 / permission denied | clone 到原始 repo 了 | 確認網址是你的帳號，重新 clone |
| PR 頁面找不到你的修改 | 忘記 push 分支 | `git push -u origin <你的分支名>` |
| PR 方向選成自己的 fork | base 選錯 | 把 base 改成原始 repo 的 `main` |
| `fatal: not a git repository` | 不在專案資料夾裡 | 先 `cd git-class-homework` |
| `nothing to commit` | 檔案沒存檔，或還沒新增 | 存檔後再 `git status` 確認 |

---

## 目錄結構

```text
git-class-homework/
├─ README.md
└─ students/
   ├─ example.md      ← 範例，不要改
   └─ 你的名字.md      ← 你要新增的檔案
```

---

> 不要在自己 fork 的 `main` 上直接改，養成先開分支的習慣。
