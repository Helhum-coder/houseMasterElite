# Git LFS Setup for houseMasterElite

## Overview

This repository is configured with Git LFS (Large File Storage) to efficiently manage large files. Git LFS stores large files outside the main repository and replaces them with lightweight pointers.

## Git LFS Configuration

### Files Tracked by Git LFS

The following file types are automatically tracked by Git LFS (configured in `.gitattributes`):

#### Binary Archives
- `*.zip`, `*.tar.gz`, `*.tgz`, `*.rar`, `*.7z`

#### Media Files
- **Images**: `*.jpg`, `*.jpeg`, `*.png`, `*.gif`, `*.bmp`, `*.tiff`, `*.webp`, `*.ico`, `*.svg`
- **Videos**: `*.mp4`, `*.avi`, `*.mov`, `*.wmv`, `*.flv`, `*.webm`
- **Audio**: `*.mp3`, `*.wav`, `*.flac`, `*.ogg`, `*.aac`

#### Documents
- `*.pdf`, `*.doc`, `*.docx`, `*.xls`, `*.xlsx`, `*.ppt`, `*.pptx`

#### Database Files
- `*.sqlite`, `*.db`, `*.sql`, `*.dump`

#### Application Files
- `*.exe`, `*.msi`, `*.dmg`, `*.pkg`, `*.deb`, `*.rpm`, `*.app`, `*.apk`, `*.ipa`

#### Development Files
- `*.jar`, `*.war`, `*.ear`, `*.so`, `*.dll`, `*.dylib`, `*.a`, `*.lib`

#### Large Generated Files
- `*.log`, `*.tmp`, `*.cache`

## Setup Instructions

### 1. Install Git LFS

#### On Windows
```bash
# Using Chocolatey
choco install git-lfs

# Using GitHub Desktop (includes Git LFS)
# Download from https://desktop.github.com/
```

#### On macOS
```bash
# Using Homebrew
brew install git-lfs

# Using MacPorts
port install git-lfs
```

#### On Linux
```bash
# Ubuntu/Debian
sudo apt-get install git-lfs

# CentOS/RHEL/Fedora
sudo yum install git-lfs
# or
sudo dnf install git-lfs
```

### 2. Initialize Git LFS

```bash
# Initialize Git LFS in the repository
git lfs install

# Verify LFS is installed
git lfs version
```

### 3. Using GitKraken with Git LFS

#### GitKraken Setup
1. **Install GitKraken**: Download from [https://www.gitkraken.com/](https://www.gitkraken.com/)
2. **Git LFS Integration**: GitKraken automatically detects and manages Git LFS files
3. **Visual Indicators**: LFS files are marked with special icons in GitKraken

#### GitKraken Features for LFS
- **Visual LFS Status**: See which files are stored in LFS
- **LFS File Management**: Easy staging/unstaging of LFS files
- **LFS History**: Track changes to LFS files
- **LFS Bandwidth**: Monitor LFS bandwidth usage

### 4. Working with Large Files

#### Adding Large Files
```bash
# Files matching .gitattributes patterns are automatically tracked
git add large-file.zip
git commit -m "Add large file"
git push
```

#### Manually Track Additional Files
```bash
# Track specific file types
git lfs track "*.psd"
git lfs track "*.blend"

# Track specific files
git lfs track "large-database.sql"

# Track files in specific directories
git lfs track "assets/**"
```

#### Check LFS Status
```bash
# See which files are tracked by LFS
git lfs ls-files

# See LFS tracking patterns
git lfs track

# Check LFS status
git lfs status
```

### 5. Migrating Existing Large Files

If you have existing large files in your repository history:

```bash
# Migrate all files matching a pattern
git lfs migrate import --include="*.zip"

# Migrate specific files
git lfs migrate import --include="large-file.dat"

# Migrate and rewrite history (use with caution)
git lfs migrate import --include="*.zip" --include-ref=refs/heads/main
```

### 6. GitKraken LFS Workflow

#### Daily Workflow
1. **Clone Repository**: GitKraken automatically handles LFS files
2. **Stage Changes**: LFS files show with special indicators
3. **Commit**: LFS files are committed like normal files
4. **Push/Pull**: GitKraken handles LFS transfer automatically

#### LFS File Indicators in GitKraken
- **LFS Icon**: Files tracked by LFS show a special icon
- **Size Display**: Shows pointer size vs. actual file size
- **Transfer Status**: Shows LFS transfer progress

### 7. Best Practices

#### File Size Guidelines
- **Use LFS for files > 100MB**: Essential for large files
- **Consider LFS for files > 10MB**: Recommended for better performance
- **Avoid LFS for code**: Keep source code in regular Git

#### Repository Management
- **Regular Cleanup**: Use `git lfs prune` to remove old LFS objects
- **Bandwidth Monitoring**: Check LFS bandwidth usage in GitKraken
- **Team Coordination**: Ensure all team members have Git LFS installed

#### GitKraken Tips
- **LFS Preferences**: Configure LFS settings in GitKraken preferences
- **File Filters**: Use GitKraken's file filters to show/hide LFS files
- **Branch Management**: LFS files are tracked per branch in GitKraken

### 8. Troubleshooting

#### Common Issues
```bash
# LFS not initialized
git lfs install

# Missing LFS files
git lfs pull

# Check LFS configuration
git lfs env

# Reset LFS tracking
git lfs untrack "*.zip"
git lfs track "*.zip"
```

#### GitKraken Specific Issues
- **LFS Files Not Showing**: Refresh repository or restart GitKraken
- **LFS Icons Missing**: Check Git LFS installation
- **Transfer Failures**: Check network connection and LFS server status

### 9. Repository Status

**Current Status**: 
- Git LFS is configured but not yet initialized
- All common large file types are pre-configured for LFS tracking
- No existing large files need migration

**Next Steps**:
1. Run `git lfs install` to initialize LFS
2. Install GitKraken for visual LFS management
3. Start adding large files - they'll be automatically tracked by LFS

## Resources

- [Git LFS Documentation](https://git-lfs.github.io/)
- [GitKraken Git LFS Guide](https://help.gitkraken.com/gitkraken-desktop/git-lfs/)
- [Git LFS Tutorial](https://github.com/git-lfs/git-lfs/wiki/Tutorial)