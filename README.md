# Mesai Kasası — Privacy & Support site

This is the public support and privacy website for **Mesai Kasası** (App Store
name "Mesai Kasası: Fazla Mesai") for iPhone. It provides the Privacy Policy URL
and Support URL that App Store Connect requires. **Turkish is the primary
language** and lives at the site root; English lives under `/en/`.

- **Developer:** Fatih Öztürkbay
- **Support email:** `feesheet.support@icloud.com` (placeholder; see below)

It is a plain static site: HTML and one CSS file. There is no framework, build
step or JavaScript, and it loads no external fonts, scripts or stylesheets.

## URLs

The site is meant for GitHub Pages, served from the `main` branch at the
repository root.

| Page | URL |
| --- | --- |
| Ana sayfa (TR) | https://ozturkbay.github.io/mesaikasasi-support/ |
| Gizlilik Politikası (TR) | https://ozturkbay.github.io/mesaikasasi-support/gizlilik/ |
| Destek (TR) | https://ozturkbay.github.io/mesaikasasi-support/destek/ |
| Home (EN) | https://ozturkbay.github.io/mesaikasasi-support/en/ |
| Privacy Policy (EN) | https://ozturkbay.github.io/mesaikasasi-support/en/privacy/ |
| Support (EN) | https://ozturkbay.github.io/mesaikasasi-support/en/support/ |

The app links to `destek/` and `gizlilik/` (see `Shared/SharedConfig.swift` in
the `mesaikasasi` repository). Use the same two URLs in App Store Connect.

Every page links to its counterpart in the other language and has `hreflang`
alternates (`tr`, `en`, and `x-default` pointing to Turkish). All internal links
are relative. The only absolute URLs are the canonical and `hreflang` tags in
each page's `<head>`.

## Before publishing: set the support email

Every address on the site is the literal placeholder `feesheet.support@icloud.com`.
Replace it, then confirm that none remain:

```sh
grep -rl feesheet.support@icloud.com --include='*.html' . \
  | xargs sed -i '' 's/feesheet.support@icloud.com/you@example.com/g'
grep -rn feesheet.support@icloud.com --include='*.html' .
```

## Publish on GitHub Pages

1. On GitHub, create a **public** repository named `mesaikasasi-support` under
   the `Ozturkbay` account. Don't add a README, license or .gitignore.
2. Push `main`:

   ```sh
   git remote add origin https://github.com/Ozturkbay/mesaikasasi-support.git
   git push -u origin main
   ```

3. Open **Settings → Pages**, choose *Deploy from a branch*, then `main` and
   `/ (root)`.
4. Check every page at https://ozturkbay.github.io/mesaikasasi-support/.

## Local preview

```sh
python3 -m http.server 8000
```

## Keeping it in sync with the app

- The privacy pages show their date: `Son güncelleme: 20 Ekim 2026` and
  `Last updated: October 20, 2026`. Edit both together.
- The policy describes the app as it works today:
  - free download, with a one-time non-consumable "Tam Sürüm" purchase and no
    subscription
  - no account, analytics or server
  - since 2026-10-20: Google AdMob ads in the free version, at task boundaries
    only, with Google UMP consent first and then the ATT prompt. Tam Sürüm
    removes all ads. Logged data is never given to the ad SDK.
  - logged days, salary and settings stored only on the device
  - a widget summary shared through the app's own app group
  - an optional local reminder
- If the app ever adds iCloud sync, an SDK, analytics, push notifications or a
  server, update both privacy pages before release.
- **Every January**, update the 2026 parameter table and the holiday tables
  in `destek/index.html` and `en/support/index.html` to match
  `docs/PAYROLL_PARAMETERS_2026.md` in the app repository.

## Design

The colors follow the app:

- **Light:** time-card paper background (`#ECE8DF`), carbon ink (`#191C20`).
- **Dark:** `#111315` background, `#E5664B` accent.
- **Accent:** stamp red (`#B83A22`) for links, rules and focus.

The icon images come from `Design/icon-1024.png` in the app repository and were
resized with `sips`.
