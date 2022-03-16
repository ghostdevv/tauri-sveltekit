# Tauri Svelte Kit

You can use this repo as a template to get started with Tauri Svelte Kit! You can also read the instructions below if you want to know how to make this yourself

# Use this

We clone the template, and remove the .git folder so it's fresh!

```bash
git clone https://github.com/ghostdevv/tauri-sveltekit my-tauri-project
cd my-tauri-project
rm .git -r
```

# Running build or dev

Build:

```
npm run tauri build
```

Dev:

```
npm run tauri dev
```

# Create this yourself

1. First we will create a svelte kit project

```bash
npm init svelte@next
```

2. Next we will install tauri cli & add a script

```
npm i @tauri-apps/cli -D
npm set-script tauri tauri
```

3. Next we will init tauri

```
npm run tauri init
```

Most of the questions you can answer how you want, here are the questions that need a specific answer:

| Question                                                                                                                               | Answer                |
|----------------------------------------------------------------------------------------------------------------------------------------|-----------------------|
| Where are your web assets (HTML/CSS/JS) located, relative to the "<current dir>/src-tauri/tauri.conf.json" file that will be created?  | ../static             |
| What is the url of your dev server?                                                                                                    | http://localhost:3000 |

4. Update our tauri config

In `src-tauri/tauri.conf.json` you need to update the `beforeDevCommand` and `beforeBuildCommand` build options:

```json
"build": {
    "beforeDevCommand": "npm run dev",
    "beforeBuildCommand": "npm run build"
}
```

5. Now we need to switch to the static adaper

```bash
npm i @sveltejs/adapter-static -D
npm remove @sveltejs/adapter-auto
```

Edit your `svelte.config.js` file to use the newly installed adapter, for example:

```js
import static from '@sveltejs/adapter-static';

/** @type {import('@sveltejs/kit').Config} */
const config = {
	kit: {
		adapter: static()
	}
};

export default config;
```

6. You are done! Start running dev with

```bash
npm run tauri dev
```