# Criathar

Lint JavaScript and HTML in your browser. No install, no build step.

**[Open Criathar](https://nuadyr.github.io/Criathar/)**

Criathar runs [ESLint](https://eslint.org/) on a single web page. The code is parsed by [acorn](https://github.com/acornjs/acorn). HTML pages are checked too, including their inline scripts.

## Use it

1. Paste code, drop a file onto the code box, or use **Open a file** (`.js`, `.mjs`, `.cjs`, `.html`, `.htm`).
2. Read the results. They update as you type.
3. Press **Apply fixes**, then **Download fixed code**.

Or run it locally: download `Criathar.html` and open it in a browser.

## Settings

| Setting | What it does |
| --- | --- |
| Language | JavaScript or HTML. Detected from the code by default. |
| JavaScript version | Latest by default. Go back to ES5 if you need to. |
| Code type | Module, Script or CommonJS. Detected from the code by default. |
| Rule set | Recommended, Recommended plus common checks, or No rules. |
| Known global names | Browser (`window`, `document`) and Node (`process`, `Buffer`). |
| Rules | Switch any rule off, or set it to warning or error. |

Not sure about **Code type**? Leave it on detect. HTML pages ignore it, because each script tag already says what it is.

## HTML pages

- Scripts without a `type` are checked together as one Script, because they share globals.
- Each `type="module"` script is checked as a Module.
- Scripts with a `src`, and types such as `application/ld+json`, are skipped.
- If a fix changes an inline script or style, matching hashes in a `Content-Security-Policy` meta tag are recalculated, so the page keeps working.

## Extra rule

`criathar/no-magic-numbers` names each magic number for you. Set its options as JSON in Settings. Leave the box empty for the defaults.

```json
{ "minOccurrences": 2, "style": "camelCase", "prefix": "app", "names": { "1000": "MS_PER_SECOND" } }
```

## Privacy

Your code never leaves your device. Your code and settings are saved in your browser's local storage so they are there next time.

The page loads acorn and ESLint from a public script host (jsDelivr), so it needs a connection.

## Built with

- [ESLint](https://eslint.org/) 9.17 via `eslint-linter-browserify`
- [acorn](https://github.com/acornjs/acorn) 8.14
- [html-eslint](https://html-eslint.org/) 0.67, bundled into the file

Built on the DeckKit design system. Made by [Nuadyr](https://nuadyr.github.io/).