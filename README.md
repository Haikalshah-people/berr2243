
# Week 1 Exercise: Environment Setup, Git Workflows & Hello MongoDB

## ✅ Objective

Set up a NodeJS development environment, learn Git workflows, and create a simple NodeJS script that connects to MongoDB.

---

## 🔧 Tools Installed

### 1. **Visual Studio Code (VSCode)**
- Downloaded from: [https://code.visualstudio.com](https://code.visualstudio.com)
- Installed extension: **MongoDB for VSCode**

### 2. **Node.js and npm**
- Downloaded from: [https://nodejs.org](https://nodejs.org)
- Installed LTS version
- Verified installation:
  ```bash
  node -v
  npm -v
  ```

### 3. **MongoDB Community Server**
- Installed from: [MongoDB Docs](https://www.mongodb.com/docs/manual/administration/install-community/)
- Started MongoDB service:
  ```bash
  net start MongoDB
  ```

### 4. **Git**
- Downloaded from: [https://git-scm.com](https://git-scm.com)
- Configured user information:
  ```bash
  git config --global user.name "Your Name"
  git config --global user.email "you@example.com"
  ```

### 5. **MongoDB Compass (Optional)**
- Downloaded from: [https://www.mongodb.com/products/compass](https://www.mongodb.com/products/compass)

---

## 📁 GitHub Repository Setup

1. Created a GitHub repository: `week1-mongo-setup`
2. Created two branches:
   - `main`
   - `feature/setup`
3. Added `.gitignore` with:
   ```
   node_modules/
   ```
4. Pushed code using:
   ```bash
   git add .
   git commit -m "Initial MongoDB setup"
   git push origin feature/setup
   ```

---

## 💻 Hello MongoDB: NodeJS Script

### 1. Initialize Node Project
```bash
npm init -y
```

### 2. Install MongoDB Driver
```bash
npm install mongodb
```

### 3. `index.js` Script
```javascript
const { MongoClient } = require("mongodb");

const uri = "mongodb://localhost:27017";
const client = new MongoClient(uri);

async function run() {
  try {
    await client.connect();
    console.log("Connected to MongoDB!");

    const db = client.db("testDB");
    const users = db.collection("users");

    const result = await users.insertOne({ name: "Your Name", age: 2000 });
    console.log("Inserted document:", result);

    const docs = await users.find().toArray();
    console.log("All documents:", docs);
  } catch (err) {
    console.error("Error:", err);
  } finally {
    await client.close();
  }
}

run();
```

### 4. Run the Script
```bash
node index.js
```

---

## 📸 Screenshots Required

- [ ] Console output showing successful connection
- [ ] Document shown in MongoDB Compass or Atlas

---

## 📦 Submission Summary

- GitHub Repository with:
  - `README.md`
  - `index.js`
  - `.gitignore`
- Screenshots of:
  - MongoDB connection in Node.js
  - Document shown in Compass

---

## ✅ Notes

Answer the exercise questions based on your testing:
- Console output of inserted document and its `_id`
- Behavior when `client.connect()` is missing
- Error when port is incorrect (e.g., 27018)
- Shell query: `db.users.find()`
- Dependency version (`mongodb`) from `package-lock.json`
- Time taken for `Connected to MongoDB!` message
