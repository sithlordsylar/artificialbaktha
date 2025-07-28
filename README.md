Virtual Baktha (SamaLore Q&A App)

Project Description

Virtual Baktha is an interactive web application designed to help users explore the intricate and expansive Lore of Lord Vikramnantha Sama-Ji and its associated universe. As the name suggests ("Baktha" means devotee), this app acts as a virtual sage or devotee, providing knowledge and insights into the SamaLore. It offers a dynamic interface to query specific documents or conduct deep, multi-document research, leveraging a Large Language Model (LLM) to deliver accurate and comprehensive answers.

Whether you're curious about the origins of Dimension 69, the Divine Aspects (Kunjus), the history of the Annunaki, or the prophecies of Ste'vi 'Ra, this app aims to be your ultimate guide to the SamaLore universe.


Features:
 * Contextual Q&A: Ask questions about the SamaLore, and the app will retrieve relevant information.

 * Document Selection: Choose a specific lore document (e.g., The Bible of Sama-Ji, kunjus.txt) to narrow down your query.

 * "Unsure" Mode: If you're unsure which document is most relevant, the app intelligently suggests the best context based on your question's keywords.

 * "Proper Research" Mode: For complex queries spanning multiple texts (e.g., "Tell me about Sama-Ji" or "Who are the Kunjus?"), enable this mode to trigger a multi-step AI analysis across relevant documents, synthesizing a comprehensive answer.

 * Exact Answer Extraction: Get the precise, verbatim section from a document that directly answers your question (in standard mode).

 * TLDR Summaries: Receive concise, AI-generated summaries and direct answers to your queries.

 * OpenRouter API Integration: Utilizes OpenRouter.ai for flexible and cost-effective access to various LLMs.

 * API Key Management: Securely upload your OpenRouter API key via a .env file (stored in browser session storage).

 * Clear Instance: A button to easily reset the application state, including the API key from session storage.


Lore Data:
The core lore for this application is derived from "The Bible of Sama-Ji" and its expanded texts. This includes:
 * The Bible of Sama-Ji.pdf: The foundational text detailing the origins of Dimension 69, Sama-Ji, the Kunjumonz, and the Divine Aspects (Kunjus).
 * Individual .txt files in public/context/: Each "Book" or significant section of the lore is broken down into separate .txt files (e.g., bible_of_samaji_intro.txt, book1.txt, book2.txt, kunjus.txt, etc.) for efficient AI processing and context management.
 * document_keywords.json: Maps keywords to specific lore documents, enabling the "Unsure" mode to suggest the most relevant context.
 * references_and_relations.json: Provides additional external context and relationships between entities in the lore, which the AI can draw upon for richer answers.
 * alt_names_mapping.json: Contains alternative names or spellings for characters and concepts, helping the AI understand variations in user queries.


Beyond SamaLore: Reusing this App for Any Knowledge Domain

This "Virtual Baktha" application is built with a modular design, making it highly adaptable for use with any text-based knowledge domain. You can easily repurpose this app to create a custom Q&A system for your own content!

Here's how you can adapt it:
 * Replace the Lore Documents (.txt files):
   * Swap out the existing SamaLore .txt files in the public/context/ folder with your own content. This could be:
     * Chapters from textbooks: Create a .txt file for each chapter.
     * Sections of novels or stories: Break down long narratives into manageable .txt files.
     * Technical documentation: Organize your documentation into separate .txt files for different topics or modules.
     * Personal notes or research papers: Turn your unstructured text into a searchable knowledge base.
   * Ensure your new .txt files are structured with clear headings or markers (e.g., [Chapter 1], ## Section Title, Verse 5:) if you want the "Exact Answer from Document" feature to work effectively.

 * Update the Metadata (.json files):
   * public/context/file_list.json: Update this array to list the filenames of your new .txt documents.
   * public/context/document_keywords.json: Create keyword mappings for your new documents. This is crucial for the "Unsure" mode to correctly suggest relevant documents based on user questions. Think about important terms, names, or concepts in each of your new .txt files.
   * public/context/references_and_relations.json (Optional but Recommended): If your new domain has external facts, common knowledge, or relationships between entities that the AI should be aware of but aren't explicitly in your .txt files, update this file.
   * public/context/alt_names_mapping.json (Optional): If your new content uses alternative terms, abbreviations, or spellings for key concepts, update this file to help the AI understand variations in user queries.

 * Customize the User Interface Text (.jsx files):
   * You can easily change the display text within the src/App.jsx (or other React components if you expand the project) to match your new domain. For example:
     * Change the main title from "SamaLore Contextual Q&A App" to "My Novel Q&A Assistant" or "Tech Doc Navigator."
     * Adjust labels for input fields, buttons, or result sections to better suit your content.
   * Remember that any changes to .jsx files require a local npm run build followed by npm run deploy to update the live GitHub Pages site.

By following these steps, you can transform this "Virtual Baktha" into a powerful, custom Q&A tool for virtually any collection of text-based information.

Getting Started
To run this project locally, you'll need Node.js and npm installed.
 * Clone the Repository:
   git clone https://github.com/sithlordsylar/artificialbaktha.git
cd artificialbaktha # Or whatever your repository name is

 * Install Dependencies:
   npm install

 * Configure Vite's Base Path:
   Open vite.config.js and ensure the base property matches your GitHub repository name (including leading and trailing slashes). For this project, it should be:
   // vite.config.js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react-swc'

export default defineConfig({
  base: '/artificialbaktha/', // Ensure this matches your repo name
  plugins: [react()],
})

 * Obtain an OpenRouter API Key:
   * Go to OpenRouter.ai/keys.
   * Sign in/create an account and generate a new API key.
 * Create a .env file:
   * In the root of your project directory (same level as package.json), create a file named .env.
   * Add your API key to this file in the following format:
     OPENROUTER_API_KEY=your_copied_api_key_here

   * Important: This .env file is for local development and will not be committed to Git (it's typically ignored by .gitignore). For the deployed app, you will upload this file directly via the UI.
 * Run Locally:
   npm run dev

   Your app should now be running at http://localhost:5173/ (or a similar address).
Deployment to GitHub Pages
This project is configured for easy deployment to GitHub Pages using the gh-pages package.
 * Install gh-pages: (If you haven't already, as part of npm install)
   npm install gh-pages --save-dev

 * Configure package.json:
   Ensure your package.json has the homepage and predeploy/deploy scripts set up as follows (replace sithlordsylar and artificialbaktha with your actual GitHub username and repository name):
   {
  "name": "sama-lore",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "homepage": "https://sithlordsylar.github.io/artificialbaktha/",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint . --ext js,jsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  },
  // ... rest of your package.json
}

 * Commit Your Changes:
   Make sure all your local changes (including vite.config.js and package.json updates) are committed to your master (or main) branch and pushed to GitHub.
   git add .
git commit -m "Configure for GitHub Pages deployment and update fetch paths"
git push origin master # or git push origin main if your branch is 'main'

 * Deploy the Application:
   This command will build your app and push the dist folder content to the gh-pages branch, which GitHub Pages uses.
   npm run deploy

 * Configure GitHub Pages (if not already done):
   * Go to your GitHub repository -> Settings -> Pages.
   * Under "Build and deployment," set "Source" to Deploy from a branch.
   * Set "Branch" to gh-pages and "Folder" to / (root).
   * Click "Save."
Your application should now be live at the URL specified in your homepage field!
Contributing & Extending
Feel free to fork this repository, contribute to the SamaLore, or extend the Q&A functionality.
 * Adding more lore: Simply add new .txt files to public/context/ and update public/context/file_list.json and public/context/document_keywords.json accordingly.
 * Improving AI prompts: Experiment with the prompt structures in App.jsx to refine the AI's responses.
 * UI/UX enhancements: Improve the user interface and experience.
"Owh Yeah!"
