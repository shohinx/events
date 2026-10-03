# sv

Everything you need to build a Svelte project, powered by [`sv`](https://github.com/sveltejs/cli).

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npx sv create

# create a new project in my-app
npx sv create my-app
```

## Developing

Use Node.js 22.17 or newer. This project uses SvelteKit 3, Svelte 5, and TypeScript 6,
with SvelteKit and Cloudflare adapter configuration in `vite.config.ts`.

Formatting and lint rules live in `prettier.config.ts` and `eslint.config.ts`.
Use `npm run format` and `npm run lint`; these commands enable Prettier's TypeScript
config support on Node 22.17. ESLint loads its TypeScript config through `jiti`.

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://svelte.dev/docs/kit/adapters) for your target environment.
