# Git .gitignore

## `.gitignore` কী?

`.gitignore` হলো Git-এর একটি configuration file, যেখানে নির্দিষ্ট file বা folder-এর নাম লিখে দিলে Git সেগুলোকে **untracked অবস্থায় থাকলে tracking-এর জন্য বিবেচনা করে না**।

## কেন ব্যবহার করা হয়?

- অপ্রয়োজনীয় file ও folder Git repository-তে রাখা এড়াতে।
- Password, API key ও secret configuration-এর মতো sensitive তথ্য repository-তে যাওয়া থেকে বিরত রাখতে।
- Generated file ও local development file repository-র বাইরে রাখতে।
- Project repository পরিষ্কার ও organized রাখতে।

## কখন ব্যবহার করা হয়?

যখন কোনো file বা folder GitHub-এ push করার প্রয়োজন নেই, তখন `.gitignore` ব্যবহার করা হয়।

উদাহরণ:
- Flutter-এর generated files ও local build files
- Log files
- IDE-এর ব্যক্তিগত settings
- `.env`-এর মতো secret configuration files

## কীভাবে ব্যবহার করবেন?

Project-এর root directory-তে `.gitignore` নামে একটি file তৈরি করুন।

Example:

```gitignore
# Environment variables
.env

# Log files
*.log

# IDE settings
.idea/

# Generated files
build/
```

এখন Git নতুন ও untracked অবস্থায় থাকা এসব matching file বা folder-কে সাধারণত tracking-এর জন্য দেখাবে না।

## গুরুত্বপূর্ণ বিষয়

**১. `.gitignore` নিজে থেকে আগে থেকেই tracked file-কে Git-এর tracking থেকে বাদ দেয় না।**

আগে থেকেই tracked কোনো file-কে tracking থেকে সরাতে চাইলে:

```bash
git rm --cached filename
```

এরপর পরিবর্তনটি commit করতে হবে। এতে local file মুছে যায় না।

**২. `.gitignore` sensitive তথ্যকে নিরাপদ করার বিকল্প নয়।**

কোনো secret আগে commit বা push হয়ে গেলে শুধু `.gitignore`-এ যোগ করলেই সেটি repository history থেকে মুছে যায় না। প্রয়োজনে secret revoke বা rotate করতে হবে।

**৩. Flutter project-এ** Flutter-এর তৈরি করা default `.gitignore` ব্যবহার করা ভালো। প্রয়োজন অনুযায়ী অতিরিক্ত file বা folder যোগ করা যায়।

## মনে রাখুন

`.gitignore` → Git-কে বলে কোন untracked file বা folder tracking-এর বাইরে রাখতে হবে।