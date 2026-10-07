# Professional Git Commit Message লেখার নিয়ম

Git-এ `commit message` ব্যবহার করা হয় একটি commit-এ **কী পরিবর্তন করা হয়েছে** তা সংক্ষেপে বোঝানোর জন্য।

একটি ভালো commit message দেখলেই অন্য developer বুঝতে পারবে—**কী পরিবর্তন হয়েছে এবং প্রয়োজনে কেন হয়েছে।**

---

## Commit কী?

Commit হলো Git-এর একটি **save point** বা project-এর নির্দিষ্ট অবস্থার record।

উদাহরণ:

```bash
git commit -m "feat: add login screen"
```

এখানে:

```text
feat
↓
কী ধরনের পরিবর্তন

add login screen
↓
কী পরিবর্তন করা হয়েছে
```

---

# ভালো Commit Message কেমন হওয়া উচিত?

একটি professional commit message সাধারণত:

* ছোট ও পরিষ্কার হবে
* নির্দিষ্ট হবে
* কী পরিবর্তন হয়েছে তা বোঝাবে
* একটি logical change-এর জন্য হবে
* একই ধরনের format অনুসরণ করবে
* অপ্রয়োজনীয় কথা থাকবে না

---

# 1. Imperative Form ব্যবহার করুন

Commit message লেখার সময় সাধারণত **Imperative Form** ব্যবহার করা হয়।

অর্থাৎ `Add`, `Fix`, `Update`, `Remove` ইত্যাদি action word দিয়ে শুরু করা ভালো।

### ✅ ভালো

```bash
git commit -m "Add login screen"
git commit -m "Fix password validation"
git commit -m "Update profile UI"
git commit -m "Remove unused dependency"
```

### ❌ এড়িয়ে চলুন

```bash
git commit -m "Added login screen"
git commit -m "Fixing password validation"
git commit -m "I updated profile UI"
```

### সহজভাবে মনে রাখুন

```text
Add
Fix
Update
Remove
Create
Improve
Refactor
```

---

# 2. Commit Message Specific করুন

শুধু `Update`, `Fix`, `Changes` লিখলে বোঝা যায় না আসলে কী পরিবর্তন হয়েছে।

### ❌ খারাপ

```bash
git commit -m "Update"
git commit -m "Fix"
git commit -m "Changes"
git commit -m "Done"
```

### ✅ ভালো

```bash
git commit -m "Fix email validation in signup form"
```

এখানে পরিষ্কারভাবে বোঝা যাচ্ছে **signup form-এর email validation ঠিক করা হয়েছে।**

---

# 3. একটি Commit-এ একটি Logical Change রাখুন

একটি commit-এ চেষ্টা করুন **একটি নির্দিষ্ট কাজের পরিবর্তন** রাখতে।

### ❌ খারাপ

```text
Add login + fix home page + update API + change button color
```

এখানে অনেকগুলো আলাদা কাজ একসাথে আছে।

### ✅ ভালো

```bash
git commit -m "feat: add login screen"
git commit -m "fix: resolve home page navigation"
git commit -m "feat: update user API integration"
git commit -m "style: update primary button"
```

এতে project history পরিষ্কার থাকে এবং প্রয়োজন হলে নির্দিষ্ট পরিবর্তন আলাদাভাবে খুঁজে পাওয়া সহজ হয়।

---

# 4. Conventional Commit Format ব্যবহার করুন

Professional project-এ commit message-এর শুরুতে একটি **type** ব্যবহার করা যায়।

### Format

```text
type: description
```

উদাহরণ:

```bash
git commit -m "feat: add login screen"
```

এখানে:

```text
feat
↓
পরিবর্তনের ধরন

add login screen
↓
পরিবর্তনের বিবরণ
```

---

## গুরুত্বপূর্ণ Commit Types

| Type       | কখন ব্যবহার করবেন              | Example                           |
| ---------- | ------------------------------ | --------------------------------- |
| `feat`     | নতুন feature যোগ করলে          | `feat: add login screen`          |
| `fix`      | Bug fix করলে                   | `fix: resolve login error`        |
| `refactor` | Code structure উন্নত করলে      | `refactor: simplify auth service` |
| `docs`     | Documentation পরিবর্তন করলে    | `docs: update Git guide`          |
| `style`    | UI বা formatting পরিবর্তন করলে | `style: update button style`      |
| `test`     | Test যোগ/পরিবর্তন করলে         | `test: add login tests`           |
| `chore`    | Project maintenance করলে       | `chore: update dependencies`      |
| `perf`     | Performance উন্নত করলে         | `perf: optimize image loading`    |

---

# 5. ভালো Commit Message-এর কিছু Example

### নতুন Feature

```bash
git commit -m "feat: add user registration"
```

### Bug Fix

```bash
git commit -m "fix: resolve password validation error"
```

### Documentation

```bash
git commit -m "docs: update Git installation guide"
```

### Code Refactoring

```bash
git commit -m "refactor: simplify authentication logic"
```

### Dependency Update

```bash
git commit -m "chore: update Flutter dependencies"
```

---

# 6. বড় পরিবর্তনের ক্ষেত্রে

কোনো পরিবর্তন যদি অনেক বড় হয়, তাহলে শুধু এক লাইনের message যথেষ্ট নাও হতে পারে।

প্রথম লাইনে সংক্ষেপে মূল পরিবর্তন লিখে নিচে বিস্তারিত দেওয়া যায়।

```text
feat: add Firebase authentication

- Add email and password login
- Add user registration
- Handle authentication errors
- Add logout functionality
```

তবে সাধারণ ছোট commit-এর ক্ষেত্রে **একটি পরিষ্কার short message-ই যথেষ্ট।**

---

# 7. Bad vs Professional Commit

| ❌ Bad       | ✅ Professional                        |
| ----------- | ------------------------------------- |
| `Update`    | `feat: add profile screen`            |
| `Fix`       | `fix: resolve login validation error` |
| `Changes`   | `refactor: simplify user service`     |
| `Done`      | `docs: update project guide`          |
| `New code`  | `feat: add password reset flow`       |
| `Bug fixed` | `fix: resolve incorrect cart total`   |

---

# 8. Commit করার আগে কী করবেন?

Professional workflow:

### Step 1 — Status Check

```bash
git status
```

কোন files পরিবর্তন হয়েছে তা দেখুন।

### Step 2 — Changes Review

```bash
git diff
```

কী পরিবর্তন করেছেন তা যাচাই করুন।

### Step 3 — Stage

```bash
git add .
```

Changes staging area-তে পাঠান।

### Step 4 — Commit

```bash
git commit -m "feat: add login screen"
```

একটি meaningful commit তৈরি করুন।

### Step 5 — History Check

```bash
git log --oneline
```

Commit history দেখতে পারেন।

---

# Professional Commit লেখার সহজ Formula

```text
type: action + specific change
```

উদাহরণ:

```bash
feat: add dark mode
```

```bash
fix: resolve API timeout error
```

```bash
refactor: simplify user repository
```

```bash
docs: update Git workflow guide
```

---

# Commit করার আগে ৩টি প্রশ্ন করুন

### 1. আমি কী পরিবর্তন করেছি?

```text
Add login screen
```

### 2. পরিবর্তনটি কী ধরনের?

```text
feat
```

### 3. Commit message দেখেই কি অন্য developer বুঝবে?

যদি উত্তর **হ্যাঁ** হয়, তাহলে commit message ভালো হয়েছে।

---

# Quick Revision

```text
Good Commit Message
        ↓
Clear
        ↓
Specific
        ↓
Short
        ↓
One Logical Change
        ↓
Consistent Format
```

### Recommended Format

```bash
git commit -m "feat: add login screen"
git commit -m "fix: resolve password validation"
git commit -m "refactor: simplify auth service"
git commit -m "docs: update project guide"
```

> **মনে রাখবেন:** একটি ভালো commit message এমন হওয়া উচিত, যাতে code না খুলেও অন্য developer বুঝতে পারে—এই commit-এ কী পরিবর্তন করা হয়েছে।
