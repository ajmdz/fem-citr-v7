npm init -y 

PRETTIER VS ESLINT
Prettier - where to put whitespaces, etc.
ESLint - Code opinion, etc.
"go with what prettier says over ESLint"

`npm audit | fix` to see vulnerabilities (and fix them?)

PRETTIER SETUP
	npx - install and run immediately (e.g. npx prettier src/App.js | --write)
	Dev dependencies: --save-dev == -D

	1. npm install -D prettier | --write
	2. create a file called .prettierrc and put {} in it
	3. Install Prettier Extension -> Turn on 'Format on Save' and 'Prettier: Require config' (optional)
	4. Create a format script in package.json:
		"format": "prettier --write \"src/**/*.{js,jsx}\""
		"format:check": "prettier --check \"src/**/*.{js,jsx}\""
	5. Run the script with `npm run format`

	If format on save doesn't work:
	1. Open Settings (JSON)
	2. Paste this:
		"[javascript]": {
    			"editor.defaultFormatter": "esbenp.prettier-vscode"
  		},
  		"[javascriptreact]": {
   			 "editor.defaultFormatter": "esbenp.prettier-vscode"
  		},

ESLINT SETUP
	1. npm install -D eslint@8.8.0 eslint-config-prettier@8.3.0 
	2. Create a file called .eslintrc.json 
		{
  			"extends": ["eslint:recommended", "prettier"],
 			"plugins": [],
  			"parserOptions": {
    				"ecmaVersion": 2022,
    				"sourceType": "module",
    				"ecmaFeatures": {
      					"jsx": true
    			  	}
  			},
  			"env": {
    				"es6": true,
    				"browser": true,
    				"node": true
  			}
		}
	3. Add the lint script in package.json
		"lint": "eslint \"src/**/*.{js,jsx}\" --quiet"
	4. Run the script with `npm run lint -- | --fix | --debug"
		first -- is for npm
		second -- is for the script we want to run (e.g. lint)

	ADDITIONAL PLUGIN SETUP FOR REACT:
	Plugins augment the ability of ESLint to understand additional language features
	1. npm install -D eslint-plugin-import@2.25.4 eslint-plugin-jsx-a11y@6.5.1 eslint-plugin-react@7.28.0
	npm install -D eslint-plugin-react-hooks@4.3.0

	2. Update the .eslintrc.json by adding:
	"extends": [
		...,
		"plugin:import/errors",
    		"plugin:react/recommended",
    		"plugin:jsx-a11y/recommended",
			"plugin:react-hooks/recommended",
		...
	],

	"rules": {
    		"react/prop-types": 0,
    		"react/react-in-jsx-scope": 0
  	},

	"plugins": ["react", "import", "jsx-a11y", "react-hooks"],

	"settings": {
    		"react": {
   		   "version": "detect"
   		 }
  	}

	In previous versions, we had to extend prettier/react as well as prettier. As of version 8 of this plugin it's all rolled into the prettier config.
	

GIT SETUP
	1. Create a .gitignore file
		node_modules
		.parcel-cache/
		dist/
		.env
		.DS_Store
		coverage/
		.vscode/

PARCEL SETUP
	1. `npm install -D parcel`
	2. Replace the App.js import with <script type="module" src="./App.js"></script>
	3. Add this script to package.json
		"dev": "parcel src/index.html"
	4. If things don't work as expected, try to delete /.parcel-cache and /dist, and run dev again
	5. Add a browserslist
		"browserslist": [
    			"last 2 Chrome versions"
  		]

REACT SETUP
	1. `npm install react@17.0.2 react-dom@17.0.2`
	
	A GOOD RULE OF THUMB: Pull out only the code you need from a package:
	e.g. import { render } from "react-dom"
		so we can just say `render()` instead of `ReactDOM.render()`


REACT ROUTER SETUP
	1. `npm install react-router-dom@6.2.1`
	
render will become createroot in react18 

