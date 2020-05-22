# DPM 設計想法

1. 對 import 沒指定版本時，採用 rewrite 的方式修改為 package.json 裡指定的版本。
2. 當 dpm run 執行時，先將 該資料夾下的原始碼，全部複製並 rewrite 放到 ./dpk/version/ 底下儲存，然後再呼叫 deno run dpk 底下的主程式。
3. 使用 dpm publish 時，將 ./dpk/version/ 資料夾下的的檔案，全部丟上統一的 git server 儲存，並以 gitserver/packageName@version/fileName 的方式儲存。
4. 當其他用戶想引用該 package 時，可以 import gitserver/packageName@version/fileName，但是也可以引用 import packageName@version/fileName 這樣就好，因為可以在 package.json 中指定 gitserver。
