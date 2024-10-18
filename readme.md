# How to Recreate
Make svelte debug in vscode and view the output.


1. have `src/routes/+page.svelte` open in client project to force svelte lsp to load and tsconfig
2. have `src/lib/Button.svelte` open in shared project
3. Remove the top line `<script lang="ts">` completely from the `Button.svelte` file in shared.
4. LSP will now output `Error: Debug Failure. False expression: Script kind should match provided ScriptKind:3 and sourceFile.scriptKind: 1, !entry: false` on every file save.
5. ADD a new file svelte file in the `shared` project inside lib, can be named anything.
6. new error is logged `Error: Could not find source file: `
7. Only way around this is to restart the LSP and ts-server


whilst intellisense works with these errors, on larger projects this eventually removes all intellisense and type checking in a file.



## Notes


Changing the shared projects tsconfig to module resulution to `"moduleResolution": "Bundler"` seems to prevent this issue, however after about 20-30 mins I seem to get the  ``Error: Debug Failure. False expression: Script kind should match provided ScriptKind:3 and sourceFile.scriptKind: 1, !entry: false`` error again, im unable to reproduce this exactly.

Also the sveltekit docs says to use NodeNext resolution: (https://kit.svelte.dev/docs/packaging#caveats)

So this wouldn't work for people who want to develope the library in realtime in a monorepo and publish it afterwards.