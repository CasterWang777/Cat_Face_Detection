# Cat_Face_Detection
this is a guideline of NICT class

適用於 Espressif 晶片組的 TensorFlow Lite Micro


安裝 ESP IDF
------------
依照 ESP-IDF 入門指南的說明設定工具鏈和 ESP-IDF 本身。接下來的步驟假設此安裝成功且 IDF 環境變數已設定。具體來說，
設定 IDF_PATH 環境變數

* 切換到 esp-idf 目錄：
```
cd esp-idf/
```
* 執行 install.sh 腳本，安裝開發環境：
```
./install.sh
```
* 執行 export.sh 腳本，設置環境變量：
```
source ./export.sh
```
* 返回上一級目錄：
```
cd ..
```

建構範例 : cat_face_detection
------------

* 從 IDF_PATH 環境變量指定的路徑復制 cat_face_detection 範例到當前目錄：
```
cp -r $IDF_PATH/examples/get-started/cate_face_detection .
```
* 切換到 cat_face_detection 目錄：
```
cd cat_face_detection/
```

* 執行 idf.py 工具進行配置（例如設置項目參數）：
```
idf.py set-target esp32s3
idf.py menuconfig
```

* 使用 idf.py 工具構建項目：
```
idf.py fullclean
idf.py build
```
下載檔案
*bootloader.bin
*cat_face_detection_lcd.bin
*partition-table.bin

#### 燒錄韌體

* 使用 ESP-IDF 提供的燒錄工具將下載的韌體燒錄到您的裝置上。 esp32燒錄指令可能看起來像這樣：
* 底下指定tty.SLAB_USBtoUART 需要改成自己的port
```
esptool.py --chip esp32 -p /dev/tty.SLAB_USBtoUART  write_flash -z 0x1000 ./bootloader.bin 0x8000 ./partition-table.bin  0x10000 ./cat_face_detection.bin
```
#### 執行結果（minicom）
*只需要將境頭對準貓臉，即會在terminal顯示讀取到的照片指令。


貓臉辨識影片:
------------
