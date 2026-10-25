# Git Diff, Git Restore & Git Log

এই Git commands গুলো মূলত project-এর changes **দেখা, undo করা এবং commit history দেখার** জন্য ব্যবহার করা হয়।

---

## 1. `git diff`

### কাজ কী?

`git diff` ব্যবহার করে **কোনো file-এ পরিবর্তন করার পর কী কী change হয়েছে** তা দেখা যায়।

সহজভাবে:

> **Code পরিবর্তন করেছি, কিন্তু এখনো `git add` করিনি — কী পরিবর্তন করেছি সেটা দেখতে `git diff` ব্যবহার করি।**

### Command

```bash
git diff
```

### কখন ব্যবহার করা হয়?

- Code পরিবর্তন করার পর
- `git add` করার আগে
- কোন line add/remove/change হয়েছে তা check করতে
- Commit করার আগে নিজের changes review করতে

### Example

ধরো আগে ছিল:

```dart
String name = "Tuhin";
```

তুমি পরিবর্তন করে করলে:

```dart
String name = "Tuhin Hossain";
```

এখন:

```bash
git diff
```

দিলে Git দেখাবে কোন অংশ পরিবর্তন হয়েছে।

### Important

`git diff` সাধারণত **working directory-এর changes** দেখায় যেগুলো এখনো staging area-তে যায়নি।

---

# 2. `git restore`

### কাজ কী?

`git restore` ব্যবহার করে **করা changes undo / restore** করা যায়।

সহজভাবে:

> ভুল করে code পরিবর্তন করেছি এবং সেই পরিবর্তন আর রাখতে চাই না → `git restore` ব্যবহার করতে পারি।

### Command

```bash
git restore filename
```

### Example

```bash
git restore main.dart
```

এতে `main.dart`-এর **unstaged changes** বাদ দিয়ে সর্বশেষ committed version ফিরিয়ে আনা হবে।

### কখন ব্যবহার করা হয়?

- ভুল করে code পরিবর্তন করলে
- কোনো পরিবর্তন আর দরকার না হলে
- কোনো file-এর আগের অবস্থায় ফিরে যেতে চাইলে

### ⚠️ Important

`git restore` করার আগে সাবধান থাকতে হবে।

কারণ uncommitted changes restore করলে সেই changes হারিয়ে যেতে পারে।

---

## `git restore --staged`

যদি কোনো file ভুল করে `git add` করে ফেলো, কিন্তু এখনো commit করোনি, তাহলে staging area থেকে remove করতে:

```bash
git restore --staged filename
```

Example:

```bash
git add main.dart
```

এখন fileটি staged।

Staging থেকে বের করতে:

```bash
git restore --staged main.dart
```

### মনে রাখার সহজ নিয়ম

```text
git restore filename
        ↓
Unstaged changes Undo

git restore --staged filename
        ↓
Staging Area থেকে বের করা
```

---

# 3. `git log`

### কাজ কী?

`git log` ব্যবহার করে repository-এর **commit history** দেখা যায়।

অর্থাৎ project-এ আগে কখন কী commit করা হয়েছে এবং কে commit করেছে তা দেখা যায়।

### Command

```bash
git log
```

### সাধারণত কী তথ্য দেখায়?

- Commit ID (SHA)
- Author
- Commit date
- Commit message

Example:

```text
commit 8f3a21c...
Author: Tuhin Hossain
Date:   ...

    Add login screen
```

### কখন ব্যবহার করা হয়?

- আগের commits দেখতে
- কোন সময়ে কী কাজ করা হয়েছিল দেখতে
- কোনো পুরোনো commit খুঁজতে
- Commit ID বের করতে
- Project-এর history বুঝতে

---

# 4. `git log --oneline`

### কাজ কী?

`git log --oneline` হলো `git log`-এর **সংক্ষিপ্ত version**।

প্রতিটি commit এক লাইনে দেখায়।

### Command

```bash
git log --oneline
```

Example:

```text
8f3a21c Add login screen
4bc72de Create home screen
91a2c44 Setup Flutter project
```

এখানে:

```text
8f3a21c
```

হলো commit-এর short ID।

### কখন ব্যবহার করা হয়?

- দ্রুত commit history দেখতে
- অনেকগুলো commit একসাথে দেখতে
- কোনো নির্দিষ্ট commit-এর short ID নিতে
- Terminal output পরিষ্কার রাখতে

---

# `git log` vs `git log --oneline`

| Command             | কাজ                                       |
| ------------------- | ----------------------------------------- |
| `git log`           | বিস্তারিত commit history দেখায়            |
| `git log --oneline` | সংক্ষিপ্তভাবে প্রতি commit এক লাইনে দেখায় |

---

# Quick Revision

| Command                | মূল কাজ                   | কখন ব্যবহার করব             |
| ---------------------- | ------------------------- | --------------------------- |
| `git diff`             | Changes দেখা              | Commit/add করার আগে         |
| `git restore`          | Changes Undo করা          | ভুল changes বাদ দিতে        |
| `git restore --staged` | Staging থেকে file বের করা | ভুল করে `git add` করলে      |
| `git log`              | Commit history দেখা       | বিস্তারিত history দরকার হলে |
| `git log --oneline`    | Short commit history      | দ্রুত history দেখতে         |

## সহজে মনে রাখুন

```text
git diff
↓
কি পরিবর্তন করেছি দেখো

git restore
↓
পরিবর্তন Undo করো

git restore --staged
↓
Staging থেকে বের করো

git log
↓
পুরোনো Commit দেখো

git log --oneline
↓
পুরোনো Commit সংক্ষেপে দেখো
```
