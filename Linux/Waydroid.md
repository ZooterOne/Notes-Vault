```
sudo dnf install waydroid
sudo waydroid init -f -s GAPPS -v https://ota.waydro.id/vendor -c https://ota.waydro.id/system
sudo waydroid shell
```

Type `ANDROID_RUNTIME_ROOT=/apex/com.android.runtime ANDROID_DATA=/data ANDROID_TZDATA_ROOT=/apex/com.android.tzdata ANDROID_I18N_ROOT=/apex/com.android.i18n sqlite3 /data/data/com.google.android.gsf/databases/gservices.db "select * from main where name = \"android_id\";"` in the shell and note the id.

Go to [https://www.google.com/android/uncertified](https://www.google.com/android/uncertified) and register the id above.

```
sudo waydroid session stop
```

Remove menu entry from `.local/share/applications/waydroid.*`.