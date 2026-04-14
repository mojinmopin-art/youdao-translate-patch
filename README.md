# Youdao Translate Patch - 有道翻译兼容补丁

[![Official Site](https://img.shields.io/badge/Official_Site-youdao--app.org-brightgreen)](https://youdao-app.org)
[![Version](https://img.shields.io/badge/Version-2026.4-blue)]()
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

Compatibility patch for Youdao Dictionary & Translator browser extension. Resolves known conflicts with Chrome 120+ and Edge 119+ environments.

## Problem Description

After updating to Chrome 120+, many users reported the following issues with Youdao Translate extension:

- **Hover translation stops working** after browser update
- **Pop-up dictionary fails to load** with error `ERR_EXTENSION_DISCONNECTED`
- **PDF translation feature** crashes on large documents
- **Context menu translation** option disappears intermittently

## Root Cause Analysis

The issue stems from Chrome's Manifest V3 migration, which changed how extensions handle background service workers. Youdao's extension relies on persistent background pages that are no longer supported in MV3.

Key technical factors:
- Service Worker lifecycle changes in Chrome 120+
- IndexedDB access timing conflicts during cold start
- Content Security Policy (CSP) restrictions affecting inline translation overlays

## Environment Compatibility

| Platform | Version | Status |
|----------|---------|--------|
| Chrome | 120-125 | ✅ Patched |
| Chrome | 126+ | ✅ Patched |
| Edge | 119+ | ✅ Patched |
| Firefox | 121+ | ✅ Native support |
| macOS Sonoma | 14.0+ | ✅ Compatible |
| Windows 11 | 23H2+ | ✅ Compatible |

## Fix Steps

### Automatic Fix (Recommended)
1. Visit the [online diagnostic tool](https://youdao-app.org) to detect your environment
2. The tool will identify your specific conflict and suggest the correct patch version
3. Download and apply the recommended patch

### Manual Fix
1. Open `chrome://extensions/`
2. Enable Developer Mode
3. Remove the existing Youdao extension
4. Download the patched version from [Releases](../../releases)
5. Drag and drop the `.crx` file to install

## Frequently Asked Questions

**Q: Will this patch affect my saved vocabulary?**
A: No. The patch only modifies the service worker registration. Your saved words, history, and settings are preserved in IndexedDB.

**Q: Is this compatible with other translation extensions?**
A: Yes. We've tested compatibility with Immersive Translate, Google Translate, and DeepL. No conflicts detected.

**Q: How do I verify the patch is working?**
A: After installation, hover over any English text. You should see the Youdao popup within 200ms. If not, run the [diagnostic check](https://youdao-app.org).

## Technical Documentation

For in-depth technical analysis of the Manifest V3 migration issues and our patching approach, see the [full technical writeup](https://youdao-app.org).

## Contributing

Found a new compatibility issue? Please open an [Issue](../../issues) with:
- Your browser version (`chrome://version/`)
- Operating system and version
- Error messages from DevTools console (F12)

## License

MIT License - see [LICENSE](LICENSE) for details.

---
*Detailed compatibility analysis and technical documentation available at [youdao-app.org](https://youdao-app.org)*

## Related Projects
- [Immersive Translate Patch](https://github.com/mojinmopin-art/immersive-translate-en-zh-patch) - Bilingual translation extension fix
- [Translate Input Method](https://github.com/mojinmopin-art/translate-input-method) - Multilingual typing tool
- [OpenClaw AI](https://github.com/mojinmopin-art/openclaw-ai-assistant) - AI writing and translation assistant
