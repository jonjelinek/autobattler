# svelte typescript autobattler

Goal is to create some game logic for autobattler.

Technologies used: svelte, typescript, vercel

## getting started

    npm i
    npm run dev

## initial repo setup

    nvm use stable
    npx degit sveltejs/template autobattler
    cd autobattler
    git init
    node scripts/setupTypeScript.js
    npm install -g vercel

## To deploy

    cd public
    vercel

Fill out questions:

```bash
$ vercel deploy
Vercel CLI 23.1.2
? Set up and deploy “~/local-projects/autobattler/public”? [Y/n] y
? Which scope do you want to deploy to? jonjelinek
? Link to existing project? [y/N] n
? What’s your project’s name? autobattler
? In which directory is your code located? ./
No framework detected. Default Project Settings:
- Build Command: `npm run vercel-build` or `npm run build`
- Output Directory: `public` if it exists, or `.`
- Development Command: None
? Want to override the settings? [y/N] n
🔗  Linked to jonjelinek/autobattler (created .vercel and added it to .gitignore)
🔍  Inspect: https://vercel.com/jonjelinek/autobattler/4Vc3UYo83aeQmcHQysU3Myun6zWk [743ms]
✅  Production: https://autobattler.vercel.app [11s]
📝  Deployed to production. Run `vercel --prod` to overwrite later (https://vercel.link/2F).
💡  To change the domain or build command, go to https://vercel.com/jonjelinek/autobattler/settings
```

Click the Inspect link to view the built site, or follow instruction to deploy to production.

Note: If you fumble the vercel setup by removing the .vercel folder, then do the following to also delete the deployment on vercel servers.  It's under Advanced settings for each project.

## Reference material
* https://www.sanity.io/guides/using-typescript-with-svelte
