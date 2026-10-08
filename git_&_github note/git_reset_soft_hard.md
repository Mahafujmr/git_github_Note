# Git Reset

`git reset` ব্যবহার করা হয় **ভুল commit undo করা, commit history পরিবর্তন করা এবং changes-এর অবস্থান পরিবর্তন করার জন্য।**

---

## `HEAD~1` কী?

`HEAD` হলো বর্তমানে যে commit-এ তুমি আছো।

```text
HEAD     → বর্তমান commit
HEAD~1   → ১ commit আগে
HEAD~2   → ২ commit আগে
HEAD~3   → ৩ commit আগে
```

Example:

```text
A → B → C
        ↑
       HEAD
```

```bash
git reset HEAD~1
```

করলে:

```text
A → B
    ↑
   HEAD
```

অর্থাৎ **বর্তমান commit থেকে ১ commit আগের অবস্থায় ফিরে যাবে।**

---

## Specific Commit ID ব্যবহার

`HEAD~1` ছাড়াও নির্দিষ্ট **commit ID** ব্যবহার করে `reset` করা যায়।

Example:

```bash
git reset --soft 4d58407
```

এখানে `4d58407` হলো target commit-এর **commit ID (SHA)**।

Commit ID দেখতে:

```bash
git log --oneline
```

Example:

```text
4d58407 Update login UI
8a72bc1 Add login screen
c31ef45 Initial commit
```

এখন:

```bash
git reset --soft 4d58407
```

করলে Git ওই নির্দিষ্ট commit `4d58407`-কে target করে reset করবে।

> **Note:** `git log --oneline` থেকে প্রয়োজনীয় commit ID কপি করে ব্যবহার করা যায়।

---

## 1. `git reset`

```bash
git reset HEAD~1
```

### কাজ কী?

শেষ commit সরিয়ে changes-গুলোকে **unstaged** অবস্থায় রাখে।

### কেন ব্যবহার করা হয়?

ভুল করে commit হয়ে গেলে, কিন্তু code changes রেখে আবার edit বা review করতে চাইলে।

---

## 2. `git reset --soft`

```bash
git reset --soft HEAD~1
```

অথবা নির্দিষ্ট commit ID:

```bash
git reset --soft 4d58407
```

### কাজ কী?

Target commit-এর পরের commitগুলো সরিয়ে দেয়, কিন্তু changes **staged** অবস্থায় রাখে।

### কেন ব্যবহার করা হয়?

ভুল commit message হলে বা changes নতুনভাবে commit করতে চাইলে।

```text
Commit ❌
   ↓
Changes → Staged
```

---

## 3. `git reset --hard`

```bash
git reset --hard HEAD~1
```

অথবা:

```bash
git reset --hard 4d58407
```

### কাজ কী?

Target commit-এর পরের commit এবং সেই সময়ের **uncommitted changes** মুছে দিয়ে target commit-এর অবস্থায় ফিরিয়ে নেয়।

### কেন ব্যবহার করা হয়?

করা changes সম্পূর্ণ বাদ দিয়ে project-কে নির্দিষ্ট পুরোনো অবস্থায় ফিরিয়ে নিতে চাইলে।

```text
Commit ❌
Changes ❌
   ↓
Target Commit
```

⚠️ **সতর্কতা:** `--hard` ব্যবহার করলে uncommitted changes হারিয়ে যেতে পারে।

---

## Quick Comparison

| Command                   | Changes-এর অবস্থা | ব্যবহার                        |
| ------------------------- | ----------------- | ------------------------------ |
| `git reset HEAD~1`        | Unstaged          | Commit undo করে code edit করতে |
| `git reset --soft HEAD~1` | Staged            | Changes রেখে নতুন commit করতে  |
| `git reset --hard HEAD~1` | Changes মুছে যায়  | সম্পূর্ণ আগের অবস্থায় ফিরতে    |

### দুইভাবে Target করা যায়

```bash
git reset --soft HEAD~1
```

**অথবা**

```bash
git reset --soft 4d58407
```

* `HEAD~1` → বর্তমান commit থেকে ১ ধাপ আগে
* `4d58407` → নির্দিষ্ট commit ID

### সহজে মনে রাখুন

```text
reset
→ Commit সরাও, changes রাখো

--soft
→ Commit সরাও, changes staged রাখো

--hard
→ Commit + changes সরাও
```

> **Important:** `git reset` মূলত local Git history ঠিক করার জন্য ব্যবহার করা হয়। Shared বা pushed commit reset করার আগে সতর্ক থাকতে হবে।
