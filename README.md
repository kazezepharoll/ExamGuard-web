# ExamGuard download website

A small, standalone website (no server, no scripts) where Cavendish students download ExamGuard, hosted free on **GitHub Pages**. The installer itself is attached to a **GitHub Release** in the same repository, so the site's Download buttons always fetch the latest version.

## Set it up once (about 10 minutes, in a browser)
1. On GitHub (signed in as kazezepharoll), create a **public** repository named **`examguard-download`**. (Public is needed so students can download without a GitHub account. It holds only this website and the installer, no ExamGuard code.)
2. **Add files → Upload files**: drag in everything from this folder (`index.html`, `404.html`, `.nojekyll`, the `assets` folder, this README). Commit.
3. **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main`, folder `/ (root)`. Save. After a minute the site is live at **https://kazezepharoll.github.io/examguard-download/**.

## Publish an installer (each new version)
1. Build it on a Windows PC, in the ExamGuard app folder: `npm install`, then `npm run build:win` → `dist\ExamGuard-Setup.exe`.
2. Its fingerprint: `certutil -hashfile dist\ExamGuard-Setup.exe SHA256`.
3. In the repository: **Releases → Draft a new release** → tag `v1.1.0` (the version) → attach **ExamGuard-Setup.exe** (exactly this name) → in the notes, write what changed and paste the fingerprint → **Publish release**.
4. In `index.html`, update the one line marked **VERSION** (version number and size). Nothing else changes: every Download button points to `releases/latest/download/ExamGuard-Setup.exe`, which GitHub always serves from the newest release.

## Photos
`assets/img/` holds the photos used on the page. To swap one, replace the file with another JPEG of the same name (about 600–1200 px wide, under 200 KB).

## Later: a university address
IT can point a university address such as `exams.cavendishza.org` at this site: **Settings → Pages → Custom domain**, plus one DNS (CNAME) record set by IT to `kazezepharoll.github.io`. GitHub then provides the https certificate.
