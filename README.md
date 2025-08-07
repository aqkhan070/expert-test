# Welcome to your Lovable project

### 1. Added `industry` Field to Lead Interface

**Problem**  
The frontend was sending an `industry` field for lead submissions, but the backend `Lead` interface was missing this parameter. This caused TypeScript errors and ignored valuable user input.

**Solution**  
The `industry` property has been added as an optional field in the `Lead` interface:

```ts
interface Lead {
  name: string;
  email: string;
  industry: string;
  submitted_at: string;
}
```
### 2. 💾 Implemented Function to Save Lead Data

**Problem**  
Lead data received from the frontend was not being persisted to the database, resulting in missing records.

**Solution**  
A new function was created to store incoming leads in the database, ensuring all data (including `industry`) is saved correctly.

```ts
import { db } from '../lib/db';

  const { data, error: dbError } = await supabase
          .from('leads')
          .insert([
            {
              name: formData.name,
              email: formData.email,
              industry: formData.industry,
              submitted_at: new Date().toISOString(),
            }
          ])
          .select();
```

## Project info

**URL**: https://lovable.dev/projects/94b52f1d-10a5-4e88-9a9c-5c12cf45d83a

## How can I edit this code?

There are several ways of editing your application.

**Use Lovable**

Simply visit the [Lovable Project](https://lovable.dev/projects/94b52f1d-10a5-4e88-9a9c-5c12cf45d83a) and start prompting.

Changes made via Lovable will be committed automatically to this repo.

**Use your preferred IDE**

If you want to work locally using your own IDE, you can clone this repo and push changes. Pushed changes will also be reflected in Lovable.

The only requirement is having Node.js & npm installed - [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating)

Follow these steps:

```sh
# Step 1: Clone the repository using the project's Git URL.
git clone <YOUR_GIT_URL>

# Step 2: Navigate to the project directory.
cd <YOUR_PROJECT_NAME>

# Step 3: Install the necessary dependencies.
npm i

# Step 4: Start the development server with auto-reloading and an instant preview.
npm run dev
```

**Edit a file directly in GitHub**

- Navigate to the desired file(s).
- Click the "Edit" button (pencil icon) at the top right of the file view.
- Make your changes and commit the changes.

**Use GitHub Codespaces**

- Navigate to the main page of your repository.
- Click on the "Code" button (green button) near the top right.
- Select the "Codespaces" tab.
- Click on "New codespace" to launch a new Codespace environment.
- Edit files directly within the Codespace and commit and push your changes once you're done.

## What technologies are used for this project?

This project is built with:

- Vite
- TypeScript
- React
- shadcn-ui
- Tailwind CSS

## How can I deploy this project?

Simply open [Lovable](https://lovable.dev/projects/94b52f1d-10a5-4e88-9a9c-5c12cf45d83a) and click on Share -> Publish.

## Can I connect a custom domain to my Lovable project?

Yes, you can!

To connect a domain, navigate to Project > Settings > Domains and click Connect Domain.

Read more here: [Setting up a custom domain](https://docs.lovable.dev/tips-tricks/custom-domain#step-by-step-guide)
