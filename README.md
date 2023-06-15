# Test how to extend Vector

Just an example to post on Stackoverflow to ask how this would work. See src/routes/+page.svelte

Problem: Importing p5 as a dev dependency doesn't work (500 "window not defined")
**Solution:** switch off SSR (Server Side Rendering) in an additional +page.js file: `export const ssr = false;`

Thanks for the help to [H.B. on GitHub](https://stackoverflow.com/a/76466672/2633652)!

# Credits

[`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte)

[`p5-svelte`](https://p5-svelte.netlify.app/docs/get-started)