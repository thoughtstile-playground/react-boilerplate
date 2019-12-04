## Replication

### 1. Installation

```
npx create-react-app ./ &&
npm install tailwindcss postcss-cli autoprefixer --save-dev &&
npm install eslint-plugin-react-hooks --save-dev &&
npx tailwind init &&
npm audit fix
```

### 2. Cleanup

```
touch postcss.config.js &&
mkdir -p ./src/styles &&
touch ./src/styles/tailwind.css &&
rm src/App.test.js src/App.css src/index.css src/logo.svg src/serviceWorker.js &&
echo -e "@tailwind base;\n@tailwind components;\n@tailwind utilities;" > ./src/styles/tailwind.css &&
echo -e "module.exports = {" > ./postcss.config.js &&
echo -e  "  plugins: [require('tailwindcss'), require('autoprefixer')]" >> ./postcss.config.js &&
echo -e "};" >> ./postcss.config.js &&
echo -e "import React from 'react'\n\nexport default function App() {" > ./src/App.js &&
echo -e "  return (" >> ./src/App.js &&
echo -e "    <div className='text-4xl font-bold text-center text-blue-500'>" >> ./src/App.js &&
echo -e "      Hello World" >> ./src/App.js &&
echo -e "    </div>\n  );\n}" >> ./src/App.js &&
echo -e "import React from 'react'" > ./src/index.js &&
echo -e "import ReactDOM from 'react-dom'" >> ./src/index.js &&
echo -e "import './styles.css'" >> ./src/index.js &&
echo -e "import App from './App'\n" >> ./src/index.js &&
echo -e "ReactDOM.render(<App />, document.getElementById('root'));" >> ./src/index.js
```

### 3. Alter package.json

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

---

## Archive

#### src/styles/Tailwind.css

```
echo -e "@tailwind base;\n@tailwind components;\n@tailwind utilities;" > ./src/styles/tailwind.css
```

```
echo -e "module.exports = {" > ./postcss.config.js &&
echo -e  "  plugins: [require('tailwindcss'), require('autoprefixer')]" >> ./postcss.config.js &&
echo -e "};" >> ./postcss.config.js
```

#### src/App.js

This boilerplate is copied with the bash commands.

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

```
echo -e "import React from 'react'\n\nexport default function App() {" > ./src/App.js &&
echo -e "  return (" >> ./src/App.js &&
echo -e "    <div className='text-4xl font-bold text-center text-blue-500'>" >> ./src/App.js &&
echo -e "      Hello World" >> ./src/App.js &&
echo -e "    </div>\n  );\n}" >> ./src/App.js
```

#### src/index.js

```
import React from "react";
import ReactDOM from "react-dom";
import "./styles.css";
import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));
```

```
echo -e "import React from 'react'" > ./src/index.js &&
echo -e "import ReactDOM from 'react-dom'" >> ./src/index.js &&
echo -e "import './styles.css'" >> ./src/index.js &&
echo -e "import App from './App'\n" >> ./src/index.js &&
echo -e "ReactDOM.render(<App />, document.getElementById('root'));" >> ./src/index.js
```

---

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).
