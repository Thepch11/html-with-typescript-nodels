👨🏻‍💻 You can generate a web HTML project by following shell script 👨🏻‍💻

Creating a shell script (.sh) to generate a web HTML project with TypeScript and Node.js involves several steps. In this example, I'll guide you through the process of creating a simple script that sets up a basic project structure. Keep in mind that this script assumes you have Node.js and npm installed on your machine.

Here's a shell script to create a web HTML project with TypeScript and Node.js:

	#!/bin/bash
	
	# Check if Node.js is installed
	if ! command -v node &> /dev/null; then
	    echo "Node.js is not installed. Please install it first."
	    exit 1
	fi
	
	# Check if npm is installed
	if ! command -v npm &> /dev/null; then
	    echo "npm is not installed. Please install it first."
	    exit 1
	fi
	
	# Get project name from user
	read -p "Enter project name: " projectName
	
	# Create project directory
	mkdir $projectName
	cd $projectName
	
	# Initialize npm package
	npm init -y
	
	# Install necessary packages
	npm install express typescript ts-node @types/node --save
	
	# Create TypeScript configuration file (tsconfig.json)
	echo '{
	  "compilerOptions": {
	    "target": "es6",
	    "module": "commonjs",
	    "outDir": "./dist",
	    "rootDir": "./src",
	    "strict": true
	  }
	}' > tsconfig.json
	
	# Create source and distribution directories
	mkdir src
	mkdir dist
	
	# Create a simple Express app in TypeScript (src/app.ts)
	echo 'import express from "express";
	
	const app = express();
	const port = 3000;
	
	app.get("/", (req, res) => {
	  res.send("Hello, TypeScript with Node.js!");
	});
	
	app.listen(port, () => {
	  console.log(`Server is running at http://localhost:${port}`);
	});
	' > src/app.ts
	
	# Create a simple HTML file (src/index.html)
	echo '<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>TypeScript Node.js App</title>
	</head>
	<body>
	    <h1>Hello, TypeScript with Node.js!</h1>
	</body>
	</html>
	' > src/index.html
	
	# Compile TypeScript code
	npx tsc
	
	# print
	echo 'You are rock 🤘🏻🤘🏻🤘🏻'
	
	# Run the application
	node dist/app.js
	
Save this script with a .sh extension (e.g., create_project.sh) and give it execute permissions:
		
	chmod +x create_project.sh
	
	
Then, run the script:

	./create_project.sh
	


This script does the following:
> 	1. Checks if Node.js and npm are installed.
> 	2. Prompts the user for a project name.
> 	3. Creates a project directory and navigates into it.
> 	4. Initializes an npm package.
> 	5. Installs necessary packages (Express, TypeScript, ts-node).
> 	6. Creates a tsconfig.json file for TypeScript configuration.
> 	7. Sets up the project structure with source and distribution directories.
> 	8. Creates a simple Express app in TypeScript (src/app.ts).
> 	9. Creates a simple HTML file (src/index.html).
> 	10. Compiles TypeScript code using tsc.
> 	11. Runs the Node.js application.
