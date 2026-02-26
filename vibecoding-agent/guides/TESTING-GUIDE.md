# Testing Guide for Non-Developers

Everything you need to know to test your project in a browser without
a coding background. Bookmark this page.

## Opening Your Project in a Browser

For simple HTML/CSS/JS projects with no build step:

**Double-click `index.html`** in your file explorer. It opens in your
default browser. That's it.

This works for most testing. The URL will show something like
`file:///C:/Users/you/project/index.html` — this is fine.

### When file:// doesn't work

Some features don't work when opened directly from your computer:
- **Clipboard copy** (the "Copy summary" button) needs HTTPS or localhost
- **Some font loading** may be blocked
- **API calls** to external services won't work

If you hit these issues, run a local server instead:

**On Mac/Linux:** Open Terminal, navigate to your project folder, run:
```
python3 -m http.server 8000
```
Then open `http://localhost:8000` in your browser.

**On Windows:** Open Command Prompt or PowerShell, navigate to your project folder, run:
```
python -m http.server 8000
```
Then open `http://localhost:8000` in your browser.

To stop the server: press `Ctrl+C` in the terminal.

**Don't have Python?** That's okay. Most testing works fine with
double-click. Only switch to localhost if something specific isn't working.

## The Browser Console (Your Debugging Best Friend)

The console shows error messages, warnings, and lets you test code manually.

### How to open it

| Browser | Shortcut |
|---|---|
| Chrome (Windows/Linux) | `F12` then click "Console" tab |
| Chrome (Mac) | `Cmd + Option + J` |
| Firefox | `F12` then click "Console" tab |
| Safari | `Cmd + Option + C` (enable in Safari → Settings → Advanced → "Show Develop menu") |
| Edge | `F12` then click "Console" tab |

### What you're looking for

**Red text = error.** Something broke. This is what you want to fix.
Common errors:
- `ReferenceError: functionName is not defined` — code is calling
  something that doesn't exist yet (probably a task dependency issue)
- `TypeError: Cannot read property of null` — code is trying to find
  an HTML element that doesn't exist (probably a mismatched ID)
- `SyntaxError` — the code has a typo (a missing bracket or quote)

**Yellow text = warning.** Usually not blocking, but worth noting.

**No red text = good.** Your verify step "No errors in browser console"
passes.

### Testing functions directly

You can type JavaScript directly into the console. This is useful for
testing calculation functions:

```
calculate(100000, 7500)
```

If the function works, you'll see its output. If it doesn't exist, you'll
see a ReferenceError.

### Copying console output

If you need to share error messages with your AI agent:
1. Click on the error message in the console
2. Right-click → "Copy" (or select the text and `Ctrl+C`)
3. Paste it into your chat with the agent

The more context you give the agent, the faster it fixes things.

## Testing Mobile Layout

You don't need a phone. Your browser can simulate mobile screens.

### How to resize

**Quick method:** Grab the edge of your browser window and drag it
narrower until it's about phone-width (~375px). Check that nothing
overflows horizontally and all elements are still usable.

**Precise method (Chrome):**
1. Open DevTools (`F12`)
2. Click the device toggle icon (looks like a phone/tablet, top-left of DevTools)
3. Select "iPhone SE" or set custom dimensions to 375 × 667
4. Your page now renders at that size

### What to check

- No horizontal scrollbar (nothing overflows the screen)
- Text is readable without zooming
- Buttons and inputs are large enough to tap (at least 44px)
- Nothing overlaps or hides behind other elements

## Keyboard Navigation Test

Tab through your entire page to verify accessibility:

1. Click somewhere on the page
2. Press `Tab` repeatedly
3. Each interactive element (inputs, buttons, links) should get a
   visible focus outline
4. The order should be logical (top to bottom, left to right)

If an element gets focus but has no visible indicator, that's an
accessibility issue worth flagging.

## Checking File Sizes

If your spec has a file size target (e.g., "all files under 50KB combined"):

**Windows:** Open your project folder, select all files, right-click →
Properties. The "Size" field shows the total.

**Mac/Linux:** Open Terminal, navigate to your project folder, run:
```
ls -la
```
Add up the file sizes shown. Or run:
```
du -sh .
```

## Safe Editing of Generated Files

Sometimes you need to edit the HTML directly — to fix translations, update
text, or correct a typo. Here's what's safe to change and what isn't.

### Safe to change

- Any visible text between HTML tags: `<h1>This text</h1>`
- The `content` attribute in meta tags
- The `title` in the `<title>` tag
- Text inside `<script>` blocks that's clearly labeled as content strings

### Do NOT change

- Anything inside `id="..."` — JavaScript uses these exact names
- Anything inside `class="..."` — CSS uses these exact names
- Anything inside `href="..."` or `src="..."` — these are links and file paths
- Template placeholders like `{amount}` or `{url}` — code replaces these at runtime
- HTML structure (don't delete or rearrange tags)

### How to save

In VS Code: `Ctrl+S` (Windows/Linux) or `Cmd+S` (Mac).
Then refresh your browser (`F5` or `Ctrl+R`) to see changes.

## Deploying to Netlify (Drag and Drop)

For static sites (HTML/CSS/JS with no build step):

1. Go to [app.netlify.com](https://app.netlify.com)
2. You can deploy without creating an account — but if you want to
   update later, create a free account first
3. Drag your entire project folder onto the deploy area
4. Wait 10-20 seconds — you'll get a live URL like `random-name.netlify.app`
5. Click the URL to verify your site works

**Note:** If you deployed without an account, you can't update that same
URL. You'll get a new random URL each time. Create a free account if you
want a persistent URL.

### Custom domain (optional)

You can set a custom domain in Netlify's site settings, but don't worry
about this for v1. Ship first, polish later.

## When Something Doesn't Work

Before pasting "it's broken" into your AI chat, gather this information:

1. **What you expected** — "I expected the slider to reach 7.50"
2. **What actually happened** — "The slider stops at 7"
3. **Console errors** — open F12, check for red text, copy it
4. **What you were doing** — "I typed 100 in the dividend field"

This information helps the AI agent fix the problem in one attempt
instead of three.
