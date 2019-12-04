## Replication

### 1. Installation

```
npx create-react-app ./ && npm install tailwindcss postcss-cli autoprefixer --save-dev && npm install eslint-plugin-react-hooks --save-dev && npm audit fix && npx tailwind init && touch postcss.config.js && mkdir -p ./src/styles && touch ./src/styles/tailwind.css && rm src/App.test.js src/App.css src/index.css src/logo.svg src/serviceWorker.js
```

```
echo -e "@tailwind base;\n@tailwind components;\n@tailwind utilities;" > ./src/styles/tailwind.css
```

### 2. Additional Code to Files

#### package.json:

```
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "build:styles": "postcss src/styles/tailwind.css -o src/styles.css",
    "prebuild": "npm run build:styles",
    "prestart": "npm run build:styles"
  },
```

#### postcss.config.js:

```
// postcss.config.js
module.exports = {
  plugins: [
    require("tailwindcss"),
    require("autoprefixer")
  ]
};
```

### 3. Starting Code:

#### App.js

```
import React from "react";

function App() {
  return (
    <div className="text-4xl font-bold text-center text-blue-500">
      Hello World!
    </div>
  );
}

export default App;
```

#### index.js

```
import React from "react";
import ReactDOM from "react-dom";
import "./styles.css";
import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));
```

---

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).
