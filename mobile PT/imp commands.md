
```
adb shell settings put global http_proxy localhost:<some port>

adb reverse tcp:<some port> tcp:<port burp is listening on>

adb shell settings put global http_proxy localhost:3333
adb reverse tcp:3333 tcp:8082

```

