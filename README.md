# Project Setup Instructions

This document provides a step-by-step guide to set up and run a new project that uses the Internet Computer (DFX/Motoko) for the backend and a React frontend with Vite. Use these instructions each time you create a new project.

---

## Initial Setup for a New Project

1. **Edit Frontend `package.json`**

   In `src/projectName_frontend/package.json`, add (or verify) the following in your **scripts** section:

   ```json
   "scripts": {
     "dev": "vite",
     "start": "vite --port 3000",
     "build": "tsc && vite build",
     // ...other scripts as needed
   }

2. Install Dependencies Using Workspaces

From your project’s root directory (e.g., ~/ic_projects/projectName), run:

npm install --workspaces

This installs dependencies for both the root and the frontend workspace.

3. Start the Local ICP Replica

From the project root, start DFX in the background (with a clean state):

dfx start --clean --background

4. Create All Canisters

In the project root, create your backend and frontend canisters:

dfx canister create --all

5. Deploy Your Canisters

Deploy your backend (and frontend assets) to the local network:

dfx deploy

6. Start the Frontend Development Server

Change into the frontend workspace directory and start the Vite server:

cd src/projectName_frontend

npm run dev

This will launch your React app (typically at http://localhost:3000).

Cleaning and Rebuilding (For Major Changes)
When you make significant changes to your files, structure, or dependencies, run these commands from your project root to clean and rebuild everything:
1. Clean Existing Installations and Generated Files:

rm -rf node_modules package-lock.json src/declarations

2. Install Dependencies for All Workspaces:

npm install --workspaces

3. Start the Local Internet Computer (DFX) Replica

dfx start --clean --background

4. Create All Canisters:

dfx canister create --all

5: Generate Canister Declarations:
dfx generate

6: Build the Canisters:
dfx build

Note: Watch for errors (e.g., unresolved imports) and adjust paths if needed.

7. Deploy the Canisters:
dfx deploy

8. Start the Frontend Development Server:

cd src/projectName_frontend
npm run dev

Summary of Command Order
1. Edit package.json in src/projectName_frontend to add "dev": "vite".
Install dependencies:
npm install --workspaces

2. Start DFX locally:
dfx start --clean --background

3. Create canisters:
dfx canister create --all

4. Deploy canisters:
dfx deploy

5. Run frontend server:
cd src/projectName_frontend
npm run dev


When to Run These Commands
Initial Project Setup:
Run the Initial Setup steps when you first create a new project.

After Major Changes:
Use the Cleaning and Rebuilding commands if you modify your project’s structure, update dependencies, or change build configurations. This resets your environment, regenerates canister declarations, and rebuilds your canisters and frontend.