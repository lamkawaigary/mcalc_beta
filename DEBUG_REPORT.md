# mcalc_beta Debug Report
Generated: 2026-02-19

## Test Environment
- Local Server: http://localhost:8080
- Project: ~/projects/mcalc_beta

## Summary

### ✅ Working Features
- All 6 calculator types implemented
- PWA manifest configured
- Service Worker registered
- iOS 26 style UI
- Frosted glass effects
- Share/Export functions (Share, CSV, PDF)

### ⚠️ Issues Found

#### 1. Vercel Redirect (Potential PWA Issue)
**File:** `vercel.json`
```json
{
  "src": "/",
  "headers": { "Location": "/index.html" },
  "status": 302
}
```
**Problem:** 302 redirect from "/" to "/index.html" may break PWA service worker caching.
**Status:** Listed as "fixed" in changelog but code still present.

#### 2. Duplicate Back Navigation
- Back button in header (top-left)
- "返回主頁" link at bottom
- Both point to same destination

#### 3. Test Report Discrepancy
- 11 calculator-form elements
- 8 calculation functions
- 8 calculation buttons

#### 4. Service Worker Cache Paths
```javascript
const [
    '/',
    '/index.html urlsToCache =',
    '/styles/main.css',    // Relative path issue?
    '/scripts/app.js'      // Relative path issue?
];
```
**Note:** Files exist but relative paths may cause offline issues.

## Git Status
- Branch: main
- Status: Clean (up to date with origin)

## Recent Commits
1. f6d83ee Feat: 新增分享/匯出功能
2. 5a324c4 Feat: 新增自流平材料計算功能
3. 11e680d Refactor: 統一 User Flow 與 iOS 26 風格

## Recommendations
1. Test calculations manually to verify math
2. Consider fixing the Vercel redirect for PWA
3. Remove duplicate back navigation
