# HRM Mobile OTA

Repository public untuk distribusi OTA JavaScript bundle HRM Mobile Android.

Repo ini sengaja hanya berisi artifact OTA yang aman untuk public:

- `ota/android/production/manifest.json`
- `ota/android/production/bundles/*.zip`

Jangan simpan source code aplikasi, `.env`, keystore, atau credential di repo ini.

## GitHub Pages

Aktifkan GitHub Pages dari:

- Source: `Deploy from a branch`
- Branch: `main`
- Folder: `/ (root)`

URL manifest production:

```text
https://krisnasantosa15.github.io/hrm-mobile-ota/ota/android/production/manifest.json
```

## Publish OTA

Jalankan dari repo mobile/build folder yang pendek, misalnya `F:\hrm`:

```powershell
powershell -ExecutionPolicy Bypass -File scripts/export-ota-android.ps1 `
  -Version 1 `
  -OtaRepoPath "D:\Projects\WebDevelopment\arsitekhijau\hrm-mobile-ota" `
  -Message "Initial OTA update"
```

Lalu commit dan push repo ini:

```powershell
git add .nojekyll README.md ota
git commit -m "publish android ota v1"
git push origin main
```

## Rollback

Rollback cukup dengan mengembalikan `manifest.json` ke versi bundle sebelumnya, lalu commit dan push.

Jika perlu mematikan OTA sementara, ubah `disabled` menjadi `true` di `manifest.json`.
