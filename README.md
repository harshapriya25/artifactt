# GitHub Actions: Upload and Download Artifacts

This project demonstrates transferring a text file from one GitHub Actions job to another.

## Workflow

1. `upload-job` creates `message.txt`.
2. `upload-job` uploads it as the artifact `my-text-file`.
3. `download-job` waits for `upload-job` because of `needs: upload-job`.
4. `download-job` downloads the artifact and prints `message.txt` using `cat`.

## Project structure

```text
artifact-demo/
├── .github/
│   └── workflows/
│       └── main.yml
└── README.md
```

## Run it on GitHub

1. Create a new, empty GitHub repository named `artifact-demo` (or use an existing repository).
2. Extract this ZIP file.
3. Open PowerShell in the extracted `artifact-demo` folder (the folder containing `.github`).
4. Run the Git commands below. Replace the URL only if your repository URL is different.

```powershell
git init
git branch -M main
git add .
git commit -m "Add artifact upload and download workflow"
git remote add origin https://github.com/harshapriya25/artifact-demo.git
git push -u origin main
```

If `git remote add origin` says `remote origin already exists`, do not run it again. Check the current URL:

```powershell
git remote -v
```

If it is the wrong URL, correct it with:

```powershell
git remote set-url origin https://github.com/harshapriya25/artifact-demo.git
```

Then push:

```powershell
git push -u origin main
```

For later changes, use:

```powershell
git add .
git commit -m "Update artifact workflow"
git push origin main
```

## View the result

Open your GitHub repository, select **Actions**, and open the latest run. Both jobs should have green check marks. Open `Download and print text file` to see the output.

Expected output:

```text
Downloaded file content:
Hello from Job 1
This file was transferred using GitHub Actions artifacts.
```

## Notes

- The workflow file must be located at `.github/workflows/main.yml` (including the leading dot in `.github`).
- The workflow runs on pushes to the `main` branch and can also be started manually with **Actions → workflow → Run workflow**.
- No dependency lockfile is needed for this example.
