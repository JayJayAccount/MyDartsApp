# My Darts App - Progressive Web App Setup

Your app has been converted into a Progressive Web App (PWA) that can be fully installed on Samsung phones and other Android devices. This guide will help you complete the setup.

## Files Added

1. **manifest.json** - PWA metadata and installation configuration
2. **service-worker.js** - Offline support and caching
3. **dartboard.svg** - Vector icon for your app
4. **browserconfig.xml** - Windows/Microsoft app configuration
5. **generate-icons.html** - Helper tool to generate PNG icons
6. **index.html** (updated) - Added PWA meta tags and service worker registration

## Setup Instructions

### Step 1: Deploy to HTTPS

PWAs **require HTTPS** to work. When deploying:
- Use a hosting service that supports HTTPS (GitHub Pages, Vercel, Netlify, etc.)
- Enable HTTPS on your domain
- Ensure all resources are loaded via HTTPS

### Step 2: Test Installation

**On Samsung/Android Phone:**

1. Open Chrome browser
2. Navigate to your app's URL (must be HTTPS)
3. Wait for the install prompt or use the menu:
   - Chrome menu → "Install app" or "Add to Home screen"
4. Follow the prompts to install
5. The app will appear on your home screen with the dartboard icon

**Alternative Installation Methods:**
- Menu (⋮) → "Add to Home screen"
- Long-press in Chrome → "Create shortcut"
- Share menu → "Add to Home screen"

**On iPhone (Limited PWA Support):**
1. Open Safari
2. Tap Share → "Add to Home Screen"
3. Works as a web app shortcut (not full PWA)

## Key PWA Features Configured

### Manifest Settings
- **Display**: `standalone` - Runs as a full-screen app without browser UI
- **Orientation**: `portrait-primary` - Locks to portrait orientation
- **Theme Color**: `#1e293b` - Matches your app's color scheme
- **Background Color**: `#0f172a` - App loading screen color

### Service Worker Features
- **Offline Support**: App works without internet (loads cached files)
- **Auto Updates**: Checks for app updates every minute
- **Background Sync**: Prepares for future sync capabilities
- **Push Notifications**: Ready for notification support

### Installation Features
- Multiple icon sizes for different devices and contexts
- Maskable icons for proper display on modern Android devices
- App shortcuts for quick actions
- Custom app name and description

## File Structure

```
MyDartsApp/
├── index.html (updated with PWA meta tags)
├── manifest.json (PWA configuration)
├── service-worker.js (offline & caching)
├── dartboard.svg (SVG icon - vector format)
└── browserconfig.xml (Windows app config)
```

## Troubleshooting

### "Install option not appearing"
- Ensure you're on HTTPS
- Use Chrome, Edge, or Samsung Internet browser
- Wait 30 seconds for Service Worker to register
- Clear browser cache and reload
- Check browser console for errors

### "App crashes when offline"
- Make sure Service Worker is registered (check DevTools → Application → Service Workers)
- Verify all CSS/JS files are loading (no 404 errors)
- Check that external CDNs (Tailwind, Font Awesome) are cached

### "Icon looks wrong or pixelated"
- Ensure PNG files are in the project root
- Verify file names match manifest.json exactly
- PNG files should not be corrupted during generation

### "App won't install on Samsung phone"
- Use Samsung Internet app instead of Chrome
- Ensure device has minimum Android 5.0+
- Check that manifest.json is valid (use `manifest-validator.appspot.com`)
- Try clearing app cache: Settings → Apps → Chrome → Clear Cache

## Testing Locally

### Using Python HTTP Server (requires HTTPS certificate)
```bash
# Python 3
python -m http.server 8000

# Then access via https://localhost:8000 (with self-signed cert)
```

### Using ngrok (for HTTPS testing)
```bash
ngrok http 8000
# Access via the HTTPS URL provided
```

### Using a Local Testing Service
- GitHub Pages (free HTTPS)
- Vercel (free HTTPS)
- Netlify (free HTTPS)

## Verification Checklist

- [ ] manifest.json is accessible and valid
- [ ] service-worker.js is registered (check DevTools → Application)
- [ ] All PNG icon files exist in project root
- [ ] HTTPS is enabled on your domain
- [ ] index.html includes:
  - `<link rel="manifest" href="/manifest.json">`
  - `<meta name="theme-color" content="#1e293b">`
  - Service Worker registration script
- [ ] Install prompt appears on Samsung/Android devices
- [ ] App launches in fullscreen/standalone mode
- [ ] App icon displays correctly on home screen
- [ ] App works offline after installation

## Next Steps

1. Generate PNG icons using `generate-icons.html`
2. Deploy to HTTPS hosting
3. Test installation on a Samsung/Android device
4. Customize manifest.json with your app details if needed
5. Monitor Service Worker updates in production

## Resources

- [PWA Documentation](https://web.dev/progressive-web-apps/)
- [Manifest Validator](https://manifest-validator.appspot.com/)
- [Chrome DevTools - Application Tab](https://developer.chrome.com/docs/devtools/application/)
- [Samsung Internet PWA Support](https://www.samsunginternet.com/en-us/developers/)

## Support

For more information on Progressive Web Apps, visit:
- https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps
- https://web.dev/pwa-checklist/
- https://www.w3.org/TR/appmanifest/
