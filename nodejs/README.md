# Initialize

-   in your root nodejs directory run `pnpm init`. then add `"type":"module"` to the package.json

-   install TypeScript and tsx with `pnpm add -D typescript tsx`

-   initialize typescript in the project with `pnpm exec tsc --init`

-   add the livekit and realtime model deps:

```
pnpm add @livekit/agents \
         @livekit/agents-plugin-openai \
         @livekit/noise-cancellation-node \
         dotenv
```

-   Set a package.json script to download the models: `pnpm pkg set "scripts.download-files=tsc && node agent.js download-files"`

-   NodeJS does not support console mode interaction. So we use playground directly in `dev` mode. We add the script to package.json with `pnpm pkg set "scripts.dev=tsx agent.ts dev"`

-   run `pnpm dev` and then connect to the [hosted LiveKit Playground](https://agents-playground.livekit.io/)
