# AniEnjoy Download System Setup Guide

This guide explains the complete download system infrastructure for AniEnjoy and how to set it up.

## System Architecture

The AniEnjoy download system consists of four main components:

1. **GitHub Actions Workflow** - Automated build and release system
2. **Download Website** - Beautiful landing page with direct downloads
3. **Download Script** - Bash script for command-line downloads
4. **Installation Guide** - User-friendly installation documentation

## Components Overview

### 1. GitHub Actions Workflow (`.github/workflows/build.yml`)

**Purpose**: Automatically build the APK and create releases on every push to main.

**Features**:
- Triggers on push to main branch
- Supports manual workflow dispatch
- Builds APK automatically
- Creates GitHub Release with version tag
- Uploads APK as a release asset

**Setup Requirements**:
- Update the build command based on your project type
- For Android Gradle: `./gradlew assembleRelease`
- For Flutter: `flutter build apk --release`

**File Location**:
```
.github/workflows/build.yml
```

### 2. Download Website (`docs/index.html`)

**Purpose**: Beautiful, responsive landing page for end-users to download the app.

**Features**:
- Modern gradient UI with animations
- Auto-fetches latest version from GitHub API
- Shows download progress with spinner animation
- Displays app features
- Includes installation instructions
- Responsive design (works on mobile and desktop)

**Setup Requirements**:
- Enable GitHub Pages in repository settings
- Source: Deploy from branch
- Branch: `main`
- Folder: `/docs`

**File Location**:
```
docs/index.html
```

**API Used**:
- GitHub API: `https://api.github.com/repos/{owner}/repo/releases/latest`
- Automatically fetches the latest release version and APK download URL

### 3. Download Script (`download.sh`)

**Purpose**: Command-line script for developers and advanced users to download and optionally install the APK.

**Features**:
- Fetches latest release from GitHub API
- Downloads the APK to current directory
- Checks for ADB installation
- Optionally installs via ADB if device is connected
- Error handling and user-friendly messages

**Usage**:
```bash
# Method 1: Direct execution
bash download.sh

# Method 2: One-liner from internet
curl -sSL https://raw.githubusercontent.com/davidomogbai004-ops/Anienjoy/main/download.sh | bash
```

**File Location**:
```
download.sh
```

### 4. Installation Guide (`INSTALL.md`)

**Purpose**: Comprehensive guide for end-users to install and troubleshoot the app.

**Includes**:
- System requirements
- Multiple installation methods
- Step-by-step installation instructions
- Troubleshooting section with common issues
- Advanced ADB installation for power users

**File Location**:
```
INSTALL.md
```

## Complete Setup Instructions

### Step 1: Project Setup

Make sure your project is ready:

```bash
# Initialize git if needed
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit with download system"

# Add remote
git remote add origin https://github.com/YOUR_USERNAME/Anienjoy.git

# Push to GitHub
git push -u origin main
```

### Step 2: Enable GitHub Actions

1. Go to your repository on GitHub
2. Click **Actions** tab
3. You should see the workflow listed
4. Click **Enable** if prompted
5. Optionally, edit `.github/workflows/build.yml` with your build commands

**Update Build Commands**:

For Android Gradle projects:
```yaml
- name: Build APK
  run: ./gradlew assembleRelease
```

For Flutter projects:
```yaml
- name: Build APK
  run: flutter build apk --release
```

For other build systems, adjust accordingly.

### Step 3: Configure GitHub Pages

1. Go to **Settings** → **Pages**
2. Select **Source**: "Deploy from branch"
3. **Branch**: Select `main`
4. **Folder**: Select `/docs`
5. Click **Save**

Your site will be available at:
```
https://github.com/YOUR_USERNAME/Anienjoy
```

Once GitHub Pages finishes building (usually 1-2 minutes), it will be live.

### Step 4: Optional - Custom Domain

If you have a custom domain (e.g., `anienjoy.app`):

1. Create `docs/CNAME` file with your domain:
```
anienjoy.app
```

2. Configure DNS records (contact your domain provider):
   - **Type**: CNAME
   - **Value**: `YOUR_USERNAME.github.io`

3. GitHub will automatically handle HTTPS

### Step 5: Update Download Links

Update the repository URL in the website if needed:

Edit `docs/index.html` and update this line:
```javascript
const response = await fetch('https://api.github.com/repos/davidomogbai004-ops/Anienjoy/releases/latest');
```

Change `davidomogbai004-ops/Anienjoy` to your `username/repo`.

Also update in `download.sh`:
```bash
REPO="YOUR_USERNAME/Anienjoy"
```

## File Structure

After setup, your repository structure should look like:

```
Anienjoy/
├── .github/
│   └── workflows/
│       └── build.yml           (GitHub Actions workflow)
├── docs/
│   ├── index.html              (Download website)
│   └── CNAME                   (Optional: custom domain)
├── download.sh                 (Download script)
├── INSTALL.md                  (Installation guide)
├── DOWNLOAD_SETUP.md           (This file)
├── README.md                   (Project readme)
├── LICENSE                     (Project license)
└── .gitignore
```

## Usage Workflow

### For End Users:

1. **Visit Website**
   - Go to your GitHub Pages URL
   - Click "Download APK" button
   - Follow installation guide

2. **Alternative: Terminal Download**
   ```bash
   curl -sSL https://raw.githubusercontent.com/davidomogbai004-ops/Anienjoy/main/download.sh | bash
   ```

3. **GitHub Releases**
   - Go to releases page
   - Download latest APK directly

### For Developers:

1. **Make changes** to your app code
2. **Commit and push** to main branch
3. **GitHub Actions** automatically:
   - Builds the APK
   - Creates a release
   - Uploads the APK
4. **Users can download** immediately

## Customization

### Changing App Name/Description

Edit `docs/index.html`:
```html
<title>AniEnjoy - Download</title>
<h1>AniEnjoy</h1>
<p>Your favorite anime, manga, and novels in one app</p>
```

### Changing Features

Edit the feature cards in `docs/index.html`:
```html
<div class="feature-card">
    <h3>📚 Manga</h3>
    <p>Read unlimited manga and manhwa</p>
</div>
```

### Changing Colors/Theme

Edit the CSS in `docs/index.html`:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

Change the hex colors to your preferred colors.

## Troubleshooting

### Website Not Showing

1. Check GitHub Pages is enabled in Settings → Pages
2. Wait 1-2 minutes for GitHub to build and deploy
3. Check branch and folder settings (main, /docs)
4. Verify `docs/index.html` exists

### GitHub Actions Not Running

1. Check `.github/workflows/build.yml` is in correct location
2. Go to Actions tab and enable workflows
3. Check YAML syntax (no indentation errors)
4. Review GitHub Actions logs for errors

### Download Button Not Working

1. Open browser DevTools (F12) → Console
2. Check for JavaScript errors
3. Verify API is reachable: `https://api.github.com/repos/YOUR_USERNAME/Anienjoy/releases/latest`
4. Check CORS isn't blocking requests

### No Releases Appearing

1. Ensure GitHub Actions workflow completed successfully
2. Check Actions tab for workflow runs and logs
3. Verify build command in workflow is correct
4. Check releases page: `https://github.com/YOUR_USERNAME/Anienjoy/releases`

## Security Considerations

1. **API Rate Limiting**: GitHub API has rate limits (60 requests/hour for unauthenticated)
2. **HTTPS**: GitHub Pages provides automatic HTTPS
3. **APK Signing**: Ensure APKs are properly signed in your build process
4. **Permissions**: Users should review APK permissions before installation

## Best Practices

1. **Version Tagging**: Use semantic versioning (v1.0.0, v1.0.1, etc.)
2. **Release Notes**: Add detailed release notes for each build
3. **Testing**: Test the download workflow before publishing
4. **Documentation**: Keep INSTALL.md updated with new instructions
5. **Monitoring**: Check GitHub Actions for failed builds

## Maintenance

### Weekly
- Monitor GitHub Actions for build failures
- Check for and fix any issues

### Monthly
- Review download statistics
- Update documentation if needed
- Check for GitHub platform updates

### As Needed
- Update build commands if dependencies change
- Add new features to the website
- Fix reported issues

## Support

For issues with the download system:

1. Check the Troubleshooting section above
2. Review GitHub Actions logs for build errors
3. Open an issue on GitHub with detailed information
4. Check the repository's Discussions section

---

**Last Updated**: 2026
**Version**: 1.0
**Maintained by**: AniEnjoy Team