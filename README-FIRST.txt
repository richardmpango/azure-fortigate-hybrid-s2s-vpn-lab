GITHUB UPLOAD - IMPORTANT
=========================

1. Extract this ZIP to a normal folder on your Windows PC.
2. Open the extracted folder.
3. Right-click UPLOAD_TO_GITHUB.ps1 and choose "Run with PowerShell".
   If Windows blocks scripts, open PowerShell in this folder and run:

   powershell -ExecutionPolicy Bypass -File .\UPLOAD_TO_GITHUB.ps1

4. Paste the URL of your existing GitHub repository when prompted.
5. Sign in to GitHub if Git asks you to authenticate.
6. The script clones the repository, restores the correct project structure,
   commits the corrected files, and pushes them.

Do NOT upload the ZIP file itself into GitHub.
Do NOT move README.md away from the repository root.

Expected root structure:
README.md
SECURITY.md
assets/
docs/
.gitignore

The README image links are relative and require the assets/ directory to be
at the same repository root level as README.md.
