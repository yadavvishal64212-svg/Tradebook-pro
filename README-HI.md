# TradeBook Pro — Web + Android source

## इसमें क्या है
- React + Vite आधारित responsive web app
- PWA manifest और service worker (HTTPS पर installable/offline shell)
- Capacitor configuration ताकि यही app Android wrapper में चल सके
- Trade add/edit/delete, realized P&L, risk/reward estimate, dashboard, equity curve,
  trade history, CSV export, strategy analytics और calendar
- अभी trade data इसी device/browser के localStorage में रहता है

## Web app चलाएँ
Node.js 20+ और npm इंस्टॉल करें:
```bash
npm install
npm run dev
```
Production build:
```bash
npm run build
```
`dist/` फ़ोल्डर को Netlify, Vercel, Cloudflare Pages या किसी static HTTPS hosting पर deploy करें।
वेब पर PWA install करने के लिए Android Chrome में deployed URL खोलें और browser menu से
**Install app** या **Add to Home screen** चुनें।

## Android APK बनाने के लिए
Android Studio, Android SDK और JDK 17+ की ज़रूरत होगी:
```bash
npm install
npm run build
npx cap add android
npx cap sync android
npx cap open android
```
Android Studio में खुलने के बाद **Build > Build Bundle(s) / APK(s) > Build APK(s)** चुनें।
Debug APK सामान्यतः `android/app/build/outputs/apk/debug/app-debug.apk` में मिलेगा।
Play Store के लिए Android Studio में signed release bundle/APK बनाना होगा।

## ध्यान दें
यह source project है; इस environment में Android SDK/Gradle उपलब्ध न होने के कारण
compiled APK binary शामिल नहीं है। Android Studio इसे build कर सकता है।
इस version में cloud login, server database और multi-device sync शामिल नहीं हैं।
localStorage data browser/device के हिसाब से अलग रहता है। CSV export से backup रखें।
TradeBook Pro केवल journaling/analysis tool है, buy/sell signals या financial advice नहीं देता।
