# vcard
# 📇 Digital Business Cards

Host your own mobile-friendly digital business card (with a one-tap **Save Contact** button) on GitHub Pages, then link it to a QR code for your printed card, badge, or email signature.

Every employee gets their own folder inside this one shared repository, so everyone's card lives at a predictable URL:

```
https://<org-name>.github.io/<repo-name>/<your-folder>/
```

Hosting is free, ad-free, and fully under company control. Because the page is self-hosted, your QR code will never break because a third-party QR or vCard service changes its pricing or shuts down.

---

## Contents

- [How the repository is organized](#how-the-repository-is-organized)
- [Part 1: One-time admin setup](#part-1-one-time-admin-setup)
- [Part 2: Create your own card](#part-2-create-your-own-card)
- [Part 3: Fill in your details](#part-3-fill-in-your-details)
- [Part 4: Generate your QR code](#part-4-generate-your-qr-code)
- [Updating your card later](#updating-your-card-later)
- [Troubleshooting](#troubleshooting)
- [The template (index.html)](#the-template-indexhtml)

---

## How the repository is organized

```
<repo-name>/
├── README.md              ← these instructions
├── .nojekyll              ← tells GitHub Pages to serve plain HTML (see Part 1)
├── _template/
│   └── index.html         ← blank template with [[PLACEHOLDERS]]; copy this
├── mark-chuberka/
│   ├── index.html         ← Mark's card
│   └── headshot.jpg       ← Mark's photo
└── jane-doe/
    ├── index.html
    └── headshot.jpg
```

Each person's folder contains exactly two files: `index.html` and `headshot.jpg`. The folder name becomes part of the permanent URL, for example `https://<org-name>.github.io/<repo-name>/mark-chuberka/`.

---

## Part 1: One-time admin setup

> [!NOTE]
> Only a repository administrator needs to do this, and only once. If the repository already exists, skip to [Part 2](#part-2-create-your-own-card).

### 1.1 Create the repository

1. In the company GitHub organization, click **New repository**.
2. Name it something descriptive, such as `digital-business-cards`.
3. Set visibility to **Public**. The cards must be publicly viewable for anyone scanning a QR code, and GitHub Pages requires a public repository on Free and Team plans.
4. Check **Add a README file**, then click **Create repository**.
5. Replace the default README with this file.

> [!WARNING]
> Everything in a public repository is visible to anyone. Only commit information employees are comfortable sharing publicly (work email, work or approved mobile number, professional headshot).

### 1.2 Add the `.nojekyll` file

1. Click **Add file → Create new file**.
2. Name the file `.nojekyll` (leading dot, no extension) and leave it empty.
3. Click **Commit changes**.

This tells GitHub Pages to serve the HTML files exactly as written instead of running them through its Jekyll site builder. It speeds up deployments and prevents special characters in the files from being misinterpreted.

### 1.3 Add the template folder

1. Click **Add file → Create new file**.
2. Type `_template/index.html` as the file name. Typing the `/` automatically creates the folder.
3. Paste the full code from [The template (index.html)](#the-template-indexhtml) at the bottom of this README.
4. Click **Commit changes**.

### 1.4 Enable GitHub Pages

1. Open the repository's **Settings** tab.
2. In the left sidebar, under **Code and automation**, click **Pages**.
3. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
4. Set **Branch** to `main` and the folder to `/ (root)`, then click **Save**.
5. After a minute or two, refresh the page. A banner will show the site address: `https://<org-name>.github.io/<repo-name>/`.

### 1.5 (Recommended) Protect the `main` branch

To prevent anyone from accidentally editing someone else's card:

1. Go to **Settings → Branches** (or **Rules → Rulesets**) and add a rule for `main`.
2. Enable **Require a pull request before merging** with at least one approval.
3. Grant employees **Write** access (or have them fork the repository and submit pull requests).

### 1.6 (Optional) Custom domain

If the company wants URLs such as `https://cards.yourcompany.com/mark-chuberka/`, add a custom domain under **Settings → Pages → Custom domain** and create the matching DNS record. Do this **before** anyone prints QR codes, because changing the domain later changes every card's URL.

---

## Part 2: Create your own card

### 2.1 Choose your folder name

Use your first and last name in **lowercase**, separated by a hyphen, with no spaces or special characters.

| ✅ Good | ❌ Avoid |
| --- | --- |
| `mark-chuberka` | `Mark Chuberka` (space) |
| `jane-doe` | `JaneDoe` (capitals) |
| `jose-garcia` | `josé_garcía` (accents, underscores) |

> [!IMPORTANT]
> Your folder name becomes part of your permanent URL and QR code. Choose carefully, because renaming it later breaks any QR codes you have already printed.

### 2.2 Prepare your headshot

1. Crop your photo to a **square** (1:1 aspect ratio). The page displays it as a circle.
2. Resize it to roughly **400 × 400 to 600 × 600 pixels** and keep the file under about **300 KB** so it loads quickly on a phone.
3. Save it as a JPEG named exactly **`headshot.jpg`** (all lowercase).

> [!WARNING]
> GitHub Pages file names are **case-sensitive**. `Headshot.jpg`, `headshot.JPG`, and `headshot.jpeg` will **not** match `headshot.jpg` in the HTML, and your photo will not appear.

### 2.3 Create your folder and `index.html`

1. Open `_template/index.html` in this repository and click the **Copy raw file** button (the copy icon at the top right of the file view).
2. Return to the repository's main page and click **Add file → Create new file**.
3. In the file name box, type your folder name followed by `/index.html`, for example:
   ```
   mark-chuberka/index.html
   ```
4. Paste the template code into the editor.
5. Replace every `[[PLACEHOLDER]]` with your own information by following [Part 3](#part-3-fill-in-your-details).

### 2.4 Commit your `index.html`

1. Click **Commit changes...**.
2. Enter a message such as `Add business card for Mark Chuberka`.
3. Choose one of the following:
   - If `main` is protected, select **Create a new branch for this commit and start a pull request**, then open the pull request for review.
   - Otherwise, select **Commit directly to the main branch**.
4. Click **Commit changes** (or **Propose changes**).

### 2.5 Upload your headshot

1. Navigate into **your folder** in the repository (click its name in the file list).
2. Click **Add file → Upload files**.
3. Drag and drop `headshot.jpg` into the upload area.
4. Commit using the same branch or pull request as in step 2.4.

Your folder should now contain exactly `index.html` and `headshot.jpg`.

### 2.6 Verify your live page

1. Once your changes are on `main`, wait one to two minutes. You can watch progress in the repository's **Actions** tab (look for **pages build and deployment**).
2. Open your URL in a browser:
   ```
   https://<org-name>.github.io/<repo-name>/<your-folder>/
   ```
3. Test it **on your phone**:
   - [ ] Your photo, name, title, and bio display correctly
   - [ ] **Save Contact to Phone** opens the contact import screen with the correct details
   - [ ] **Call** dials your number
   - [ ] **Email** opens a new message to your address
   - [ ] Every website and LinkedIn button opens the correct page
   - [ ] The page looks right in both light mode and dark mode

---

## Part 3: Fill in your details

Every value you must change appears in the template as a `[[PLACEHOLDER]]` in square brackets, and every line containing one is marked with a `<!-- ✏️ EDIT -->` comment directly above it.

> [!TIP]
> When you are finished, press **Ctrl + F** (or **Cmd + F**) in the editor and search for `[[`. You should find **zero** matches. Any remaining match is a field you missed.

### 3.1 Field reference

**Plain-text fields** (type normally):

| Placeholder | Where it appears | Example |
| --- | --- | --- |
| `[[FULL_NAME]]` | Browser tab title, photo alt text, large name heading (3 places) | `Mark Chuberka` |
| `[[JOB_TITLE]]` | Bold line under your name (followed by "at Elliott Davis") | `Sr. Solutions Architect` |
| `[[BIO]]` | Short tagline under your title (one sentence, about 80 characters) | `Designing modern advanced analytics systems and tools with NSAW and OAC` |
| `[[FIRST_LAST]]` | File name of the downloaded contact card | `Mark_Chuberka` |
| `[[PHONE_DIGITS]]` | **Call** button. Use `+1` and digits only, no spaces or dashes | `+15129051819` |
| `[[EMAIL]]` | **Email** button | `mark.chuberka@elliottdavis.com` |
| `[[LINKEDIN_HANDLE]]` | **LinkedIn** button. The part of your profile URL after `/in/` | `markchuberka` |

**vCard fields** (must be URL-encoded; see [3.2](#32-encoding-the-vcard-fields)):

| Placeholder | vCard field | Example (already encoded) |
| --- | --- | --- |
| `[[VCARD_FULL_NAME]]` | `FN` (display name) | `Mark%20Chuberka` |
| `[[VCARD_LAST_NAME]]` | `N` (last name) | `Chuberka` |
| `[[VCARD_FIRST_NAME]]` | `N` (first name) | `Mark` |
| `[[VCARD_TITLE]]` | `TITLE` (job title saved to the contact) | `Sr.%20Solutions%20Architect%20-%20Advanced%20Analytics` |
| `[[VCARD_EMAIL]]` | `EMAIL` | `mark.chuberka%40elliottdavis.com` |
| `[[VCARD_PHONE]]` | `TEL` | `%2B1-512-905-1819` |

**Company-standard items** (do **not** change unless your role requires it): the "at Elliott Davis" text, the vCard `ORG` (organization), the two company website URLs inside the vCard, and the ElliottDavis.com and EquifyAdvisors.com buttons.

### 3.2 Encoding the vCard fields

The **Save Contact** button stores your entire contact card inside the link itself (a `data:` URL). Because it is a URL, certain characters must be replaced with codes:

| Character | Replace with | Character | Replace with |
| --- | --- | --- | --- |
| space | `%20` | `+` | `%2B` |
| `@` | `%40` | `,` | `%2C` |
| `:` | `%3A` | `&` | `%26` |
| `;` | `%3B` | `#` | `%23` |
| `/` | `%2F` | `'` | `%27` |

Letters, numbers, hyphens (`-`), periods (`.`), and underscores (`_`) can be typed normally.

> [!CAUTION]
> A single unencoded **space**, **`#`**, or **`&`** can silently break the Save Contact button or cut off everything after it. Double-check each vCard value before committing.

> [!TIP]
> To encode a value automatically, open your browser's developer console (**F12 → Console**), type `encodeURIComponent("Sr. Solutions Architect - Advanced Analytics")`, and press Enter. Copy the result without the surrounding quotes.

For reference, this is what the encoded vCard looks like once a phone decodes it:

```
BEGIN:VCARD
VERSION:3.0
FN:Mark Chuberka
N:Chuberka;Mark;;;
ORG:Elliott Davis
TITLE:Sr. Solutions Architect - Advanced Analytics
EMAIL;TYPE=WORK:mark.chuberka@elliottdavis.com
TEL;TYPE=CELL:+1-512-905-1819
URL;TYPE=WORK:https://www.elliottdavis.com
URL;TYPE=OTHER:https://www.equifyadvisors.com
END:VCARD
```

If the number you list is a desk line rather than a mobile phone, change `TEL%3BTYPE%3DCELL` to `TEL%3BTYPE%3DWORK` in the template.

### 3.3 Before and after

Red lines show the template as copied; green lines show the same lines filled in. These are the **only** lines you need to change.

```diff
- <title>[[FULL_NAME]] - Digital Business Card</title>
+ <title>Mark Chuberka - Digital Business Card</title>

- <img src="headshot.jpg" alt="[[FULL_NAME]]" class="avatar">
+ <img src="headshot.jpg" alt="Mark Chuberka" class="avatar">

- <h1>[[FULL_NAME]]</h1>
+ <h1>Mark Chuberka</h1>

- <p class="title">[[JOB_TITLE]] at Elliott Davis</p>
+ <p class="title">Sr. Solutions Architect at Elliott Davis</p>

- <p class="bio">[[BIO]]</p>
+ <p class="bio">Designing modern advanced analytics systems and tools with NSAW and OAC</p>

- <a href="data:text/vcard;charset=utf-8,BEGIN%3AVCARD%0AVERSION%3A3.0%0AFN%3A[[VCARD_FULL_NAME]]%0AN%3A[[VCARD_LAST_NAME]]%3B[[VCARD_FIRST_NAME]]%3B%3B%3B%0AORG%3AElliott%20Davis%0ATITLE%3A[[VCARD_TITLE]]%0AEMAIL%3BTYPE%3DWORK%3A[[VCARD_EMAIL]]%0ATEL%3BTYPE%3DCELL%3A[[VCARD_PHONE]]%0AURL%3BTYPE%3DWORK%3Ahttps%3A%2F%2Fwww.elliottdavis.com%0AURL%3BTYPE%3DOTHER%3Ahttps%3A%2F%2Fwww.equifyadvisors.com%0AEND%3AVCARD" download="[[FIRST_LAST]].vcf" ...>
+ <a href="data:text/vcard;charset=utf-8,BEGIN%3AVCARD%0AVERSION%3A3.0%0AFN%3AMark%20Chuberka%0AN%3AChuberka%3BMark%3B%3B%3B%0AORG%3AElliott%20Davis%0ATITLE%3ASr.%20Solutions%20Architect%20-%20Advanced%20Analytics%0AEMAIL%3BTYPE%3DWORK%3Amark.chuberka%40elliottdavis.com%0ATEL%3BTYPE%3DCELL%3A%2B1-512-905-1819%0AURL%3BTYPE%3DWORK%3Ahttps%3A%2F%2Fwww.elliottdavis.com%0AURL%3BTYPE%3DOTHER%3Ahttps%3A%2F%2Fwww.equifyadvisors.com%0AEND%3AVCARD" download="Mark_Chuberka.vcf" ...>

- <a href="tel:[[PHONE_DIGITS]]" class="btn btn-success">Call</a>
+ <a href="tel:+15129051819" class="btn btn-success">Call</a>

- <a href="mailto:[[EMAIL]]" class="btn btn-email">Email</a>
+ <a href="mailto:mark.chuberka@elliottdavis.com" class="btn btn-email">Email</a>

- <a href="https://www.linkedin.com/in/[[LINKEDIN_HANDLE]]" ...>💼 LinkedIn</a>
+ <a href="https://www.linkedin.com/in/markchuberka" ...>💼 LinkedIn</a>
```

---

## Part 4: Generate your QR code

1. Copy your live URL from step 2.6 (including the trailing `/`).
2. Open a free QR code generator that creates **static** codes, such as [QRCode Monkey](https://www.qrcode-monkey.com/).
3. Paste your URL, then download the code as **SVG** (best for print and engraving) or high-resolution **PNG**.
4. Scan it with your phone camera **before** printing to confirm it opens your card.

> [!IMPORTANT]
> Use a **static** QR code, which encodes your URL directly. Avoid "dynamic" or "trackable" QR codes: they route through the vendor's own short link, which can expire or move behind a paywall and break your printed cards.

---

## Updating your card later

Edit `<your-folder>/index.html` (click the pencil icon) or upload a new `headshot.jpg` with the same name, then commit. The changes go live within a few minutes, and your existing QR code keeps working because the URL does not change.

Do **not** rename your folder or the `index.html` file, since either change alters your URL.

---

## Troubleshooting

| Problem | Likely cause and fix |
| --- | --- |
| Page shows **404** | Wait a few minutes after committing. Confirm the file is named exactly `index.html`, the folder name in the URL matches exactly (case-sensitive), your changes are merged into `main`, and Pages is enabled (Part 1.4). |
| Photo does not appear | The file must be named exactly `headshot.jpg` (lowercase) and sit in the **same folder** as your `index.html`. |
| **Save Contact** does nothing, or contact details are cut off or garbled | A vCard value contains an unencoded character (most often a space, `#`, or `&`). Re-check against [3.2](#32-encoding-the-vcard-fields). |
| Contact saves, but a field is blank | A `[[PLACEHOLDER]]` was left in the vCard, or a `%0A` separator was deleted while editing. Search for `[[` and compare against the example in [3.3](#33-before-and-after). |
| Text still shows `[[FULL_NAME]]` or similar | A placeholder was missed. Search the file for `[[`. |
| Changes are not showing | Your browser may be showing a cached copy. Refresh, or open the page in a private window. |
| Colors look different on another phone | Expected. The card automatically switches between light and dark themes to match each device's setting. |

---

## The template (index.html)

This is the contents of `_template/index.html`. Lines that require your information are marked with `<!-- ✏️ EDIT -->`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- ✏️ EDIT: browser tab title -->
    <title>[[FULL_NAME]] - Digital Business Card</title>
    <style>
        :root {
            --bg-color: #f4f4f9;
            --card-bg: #ffffff;
            --text-color: #222222;
            --subtext-color: #555555;
            --primary-btn: #0066cc;
            --secondary-btn: #28a745;
            --email-btn: #007aff;
            --email-btn-text: #ffffff;
            --outline-btn: #f0f0f5;
            --outline-btn-text: #222222;
            --outline-border: rgba(0,0,0,0.08);
        }

        /* Automatic Dark Mode Styles */
        @media (prefers-color-scheme: dark) {
            :root {
                --bg-color: #121212;
                --card-bg: #1e1e1e;
                --text-color: #ffffff;
                --subtext-color: #bbbbbb;
                --primary-btn: #0a84ff;
                --secondary-btn: #30d158;
                --email-btn: #f5a623;
                --email-btn-text: #ffffff;
                --outline-btn: #2c2c2e;
                --outline-btn-text: #ffffff;
                --outline-border: rgba(255,255,255,0.12);
            }
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            background: var(--bg-color);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
            box-sizing: border-box;
        }

        .card {
            background: var(--card-bg);
            padding: 30px;
            border-radius: 16px;
            box-shadow: 0 8px 24px rgba(0,0,0,0.18);
            text-align: center;
            max-width: 360px;
            width: 100%;
        }

        .avatar {
            width: 90px;
            height: 90px;
            border-radius: 50%;
            object-fit: cover;
            margin-bottom: 12px;
            background-color: #ddd;
        }

        h1 { margin: 8px 0 4px; font-size: 22px; }

        p.title {
            color: var(--subtext-color);
            margin: 0 0 6px;
            font-size: 14px;
            font-weight: 700;
        }

        p.bio { color: var(--subtext-color); margin: 0 0 20px; font-size: 13px; line-height: 1.4; }

        .btn-group { display: flex; gap: 10px; margin-bottom: 12px; }

        .btn {
            display: block;
            width: 100%;
            padding: 12px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 600;
            font-size: 14px;
            box-sizing: border-box;
            transition: opacity 0.2s, background-color 0.2s;
        }
        .btn:hover { opacity: 0.88; }

        .btn-primary { background: var(--primary-btn); color: #ffffff; }
        .btn-success { background: var(--secondary-btn); color: #ffffff; }
        .btn-email { background: var(--email-btn); color: var(--email-btn-text); }
        .btn-outline {
            background: var(--outline-btn);
            color: var(--outline-btn-text);
            border: 1px solid var(--outline-border);
        }
    </style>
</head>
<body>

    <div class="card">
        <!-- ✏️ EDIT: photo alt text. Upload your photo to THIS folder named exactly headshot.jpg (lowercase). -->
        <img src="headshot.jpg" alt="[[FULL_NAME]]" class="avatar">

        <!-- ✏️ EDIT: name, job title, and one-line bio -->
        <h1>[[FULL_NAME]]</h1>
        <p class="title">[[JOB_TITLE]] at Elliott Davis</p>
        <p class="bio">[[BIO]]</p>

        <!-- ✏️ EDIT: Save Contact vCard. All [[VCARD_...]] values must be URL-encoded (see README section 3.2). Also edit [[FIRST_LAST]] in the download file name. -->
        <a href="data:text/vcard;charset=utf-8,BEGIN%3AVCARD%0AVERSION%3A3.0%0AFN%3A[[VCARD_FULL_NAME]]%0AN%3A[[VCARD_LAST_NAME]]%3B[[VCARD_FIRST_NAME]]%3B%3B%3B%0AORG%3AElliott%20Davis%0ATITLE%3A[[VCARD_TITLE]]%0AEMAIL%3BTYPE%3DWORK%3A[[VCARD_EMAIL]]%0ATEL%3BTYPE%3DCELL%3A[[VCARD_PHONE]]%0AURL%3BTYPE%3DWORK%3Ahttps%3A%2F%2Fwww.elliottdavis.com%0AURL%3BTYPE%3DOTHER%3Ahttps%3A%2F%2Fwww.equifyadvisors.com%0AEND%3AVCARD" download="[[FIRST_LAST]].vcf" class="btn btn-primary" style="margin-bottom: 12px;">Save Contact to Phone (.vcf)</a>

        <!-- ✏️ EDIT: phone (+1 and digits only) and email address -->
        <div class="btn-group">
            <a href="tel:[[PHONE_DIGITS]]" class="btn btn-success">Call</a>
            <a href="mailto:[[EMAIL]]" class="btn btn-email">Email</a>
        </div>

        <!-- Company websites (standard for all employees; no edit needed) -->
        <a href="https://www.elliottdavis.com" target="_blank" rel="noopener" class="btn btn-outline" style="margin-bottom: 8px;">🌐 ElliottDavis.com</a>
        <a href="https://www.equifyadvisors.com" target="_blank" rel="noopener" class="btn btn-outline" style="margin-bottom: 8px;">🌐 EquifyAdvisors.com</a>

        <!-- ✏️ EDIT: LinkedIn handle (the part of your profile URL after /in/) -->
        <a href="https://www.linkedin.com/in/[[LINKEDIN_HANDLE]]" target="_blank" rel="noopener" class="btn btn-outline">💼 LinkedIn</a>
    </div>

</body>
</html>
```
