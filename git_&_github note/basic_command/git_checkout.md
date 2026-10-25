# Git Checkout

## What is `git checkout`?

`git checkout` ব্যবহার করা হয় মূলত **branch পরিবর্তন করা** এবং নির্দিষ্ট অবস্থার/commit-এর code **দেখতে বা restore করতে**।

সহজভাবে:

> **এক branch থেকে অন্য branch-এ যেতে বা কোনো পুরোনো commit-এর code দেখতে `git checkout` ব্যবহার করা যায়।**

---

## 1. Branch Change

এক branch থেকে অন্য branch-এ যেতে:

```bash
git checkout branch-name
```

### Example

```bash
git checkout develop
```

এতে বর্তমান branch থেকে `develop` branch-এ চলে যাবে।

### কখন ব্যবহার করা হয়?

যখন project-এ একাধিক branch থাকে এবং একটি branch থেকে অন্য branch-এ কাজ করতে যেতে হয়।

---

## 2. নতুন Branch তৈরি করে সেখানে যাওয়া

```bash
git checkout -b feature-login
```

এটি একসাথে দুটি কাজ করে:

1. `feature-login` নামে নতুন branch তৈরি করে
2. সেই branch-এ switch করে

Example:

```bash
git checkout -b login-page
```

এরপর তুমি `login-page` branch-এ কাজ করতে পারবে।

### কখন ব্যবহার করা হয়?

নতুন কোনো feature বা কাজ আলাদা branch-এ শুরু করতে।

```text
main
  ↓
checkout -b login-page
  ↓
login-page
```

---

## 3. নির্দিষ্ট Commit-এ যাওয়া

একটি নির্দিষ্ট commit-এর code দেখতে:

```bash
git checkout commit-id
```

Example:

```bash
git checkout 8f3a21c
```

এতে Git ওই commit-এর অবস্থায় চলে যাবে।

### কখন ব্যবহার করা হয়?

- পুরোনো code দেখতে
- কোনো পুরোনো version পরীক্ষা করতে
- কোনো commit-এর সময় project কেমন ছিল দেখতে

### ⚠️ Important: Detached HEAD

কোনো সরাসরি commit-এ checkout করলে সাধারণত **detached HEAD state** তৈরি হয়।

```text
HEAD → commit
```

এ অবস্থায় নতুন কাজ করার আগে সাধারণত একটি branch তৈরি করা ভালো।

---

# `git checkout` vs `git switch` vs `git restore`

আধুনিক Git-এ `git checkout`-এর কাজগুলো আলাদা করার জন্য দুটি command ব্যবহার করা হয়:

### Branch পরিবর্তনের জন্য

```bash
git switch main
```

### নতুন branch তৈরি করার জন্য

```bash
git switch -c feature-login
```

### File-এর changes restore করার জন্য

```bash
git restore filename
```

অর্থাৎ:

| কাজ                  | পুরোনো পদ্ধতি             | Modern recommended              |
| -------------------- | ------------------------- | ------------------------------- |
| Branch change        | `git checkout main`       | `git switch main`               |
| New branch + switch  | `git checkout -b feature` | `git switch -c feature`         |
| File restore         | `git checkout -- file`    | `git restore file`              |
| Specific commit দেখা | `git checkout commit-id`  | `git switch --detach commit-id` |

---

## Why is `git checkout` still important?

`git checkout` পুরোনো Git workflow-এর একটি গুরুত্বপূর্ণ command এবং অনেক existing tutorial/project-এ এখনো দেখা যায়।

তবে নতুন project-এ কাজ করার সময় **branch-এর জন্য `git switch` এবং file-এর জন্য `git restore` ব্যবহার করা বেশি পরিষ্কার ও recommended**।

---

## Quick Revision

```text
git checkout main
        ↓
main branch-এ যাও

git checkout -b feature-login
        ↓
নতুন branch তৈরি + সেই branch-এ যাও

git checkout commit-id
        ↓
নির্দিষ্ট পুরোনো commit দেখো
```

### মনে রাখার সহজ নিয়ম

> **`git checkout` = branch change / নির্দিষ্ট Git state-এ যাওয়া**

> **Modern Git → `git switch` = branch, `git restore` = file changes**
