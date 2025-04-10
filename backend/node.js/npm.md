# npm (Node Package Manager)

`npm` is the **default package manager for Node.js**. It helps developers install, share, and manage third-party packages and dependencies for their Node.js projects.

---

## Why npm?

- Install and manage libraries or tools (like `express`, `mongoose`, etc.)
- Share your own packages with others
- Manage project dependencies easily with `package.json`

---

## 1. Initializing a Project

```bash
npm init
```
Or for quick setup:
```
npm init -y
```
This creates a package.json file to manage your project’s metadata and dependencies.

## 2. Installing Packages
- Local Installation (default)
Installs into the node_modules/ directory.
```
npm install express
```
Shortcut:
```
npm i express
```
- Global Installation
```
npm install -g nodemon
```
## 3. package.json Breakdown
```
{
  "name": "my-app",
  "version": "1.0.0",
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js"
  },
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^2.0.22"
  }
}
```
## 4. Scripts
You can define custom commands in scripts.
```
npm run start
npm run dev
```
Some scripts like start can be run without run:
```
npm start
```
## 5. Uninstalling Packages
```
npm uninstall express
```
## 6. Updating Packages
```
npm update
```
## 7. Development vs Production Dependencies
dependencies: Needed in production

devDependencies: Needed only during development

Add dev dependency:
```
npm install --save-dev nodemon
```
## 8. Useful Commands
Command	Description
- npm init	Create package.json
- npm install	Install all dependencies from package.json
- npm list	Show installed packages
- npm outdated	Show outdated packages
- npm audit	Scan for security issues
- npm run <script>	Run a custom script

## 9. Exploring npm Packages
Browse: https://www.npmjs.com/

## Bonus Tips
Use .gitignore to exclude node_modules/

Commit package-lock.json to maintain consistency

Avoid global installs unless necessary

