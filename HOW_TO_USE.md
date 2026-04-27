# 📘 How to Use This Repository

Welcome! 🙋‍♀️ This repo contains curated 📚 UPSC notes. Follow these simple steps to access and download them:

---

## 📥 1. Download a **Single File**

To download an individual file:

1. Click the subject folder (e.g., [Anthropology](https://github.com/madhurimarawat/UPSC-Notes-Resources/blob/main/UPSC-Notes-Resources/Anthropology)).
2. Open the file you want (e.g., `Anthropology_Handwritten_Notes.pdf`).
3. Click the three dots `...` at the top-right of the file view.
4. Click **Download** ⬇️ to save the file locally.

> [!TIP]
> Best when you need **just one topic** or a quick revision sheet! 📝

---

## 📁 2. Download a **Complete Subject Folder** (e.g., Anthropology)

Want all units of a subject 📘 like *Anthropology*?

GitHub doesn’t allow direct folder downloads, so use one of the methods below:

### ✅ Option 1: [**DownGit**](https://minhaskamal.github.io/DownGit/#/home)

1. Open [DownGit](https://minhaskamal.github.io/DownGit/#/home)
2. Paste the folder link, for example:

   ```
   https://github.com/madhurimarawat/UPSC-Notes-Resources/blob/main/UPSC-Notes-Resources/Anthropology
   ```
3. Click **Download** 🚀
   A ZIP file of that folder will be generated.

> [!TIP]
> Great for downloading **only one subject** without the full repo.

---

### ✅ Option 2: Git Sparse Checkout (Advanced)

Use this if you're comfortable with Git and need just one folder:

```bash
git clone --filter=blob:none --no-checkout https://github.com/madhurimarawat/UPSC-Notes-Resources.git
cd UPSC-Notes-Resources
git sparse-checkout init --cone
git sparse-checkout set "Previous_Year/Notes/Anthropology"
git checkout main
```

> [!CAUTION]
> Requires Git version 2.25+ and basic command line knowledge.

---

## 🧰 3. Clone the Entire Repo (All Semesters & Subjects)

Use this if you want to:

* Contribute 🛠️
* Always get the **latest updates** 🔄
* Access everything offline

Run:

```bash
git clone https://github.com/madhurimarawat/UPSC-Notes-Resources.git
```

> [!WARNING]
> Make sure [Git](https://git-scm.com/downloads) is installed.

> [!NOTE]
> Recommended for users who want to fork or make changes 💻.

---

## 🙌 Happy Studying!

If you find this helpful, feel free to 🌟 star the repo and contribute to make it even better for everyone!
