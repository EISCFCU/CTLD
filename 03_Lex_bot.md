# 機器學習、運算與辨識服務應用

# 情境

各行各業的組織都需要處理大量紙質檔，其中又以發票類票據居多。以往，對於包含表格、表單、段落以及核取方塊的各類掃描文檔，我們往往很難從中提取出有效資訊。雖然目前不少組織已經通過人工、自訂代碼或者光學字元辨識（OCR）等技術解決了資訊提取難題，但其中仍然需要借助完善的表單提取與自訂工作流範本。
此外，在從文檔中提取到文本或其他形式的內容之後，使用者還希望從收據或發票中幫助最終用戶整理出更多深層洞見。但這又需要構建起複雜的自然語言處理（NLP）模型，模型的訓練又要佔用大量訓練資料與計算資源。機器學習模型的構建與訓練往往既昂貴、又極為耗時。
再有，對於最終用戶來說，提供類似於人的介面來與這些文檔交互是很麻煩的。雖然最終使用者可以通過給服務台打電話的方式得到不少説明，但隨著時間的推移，組織成本總會因此而不斷提升。


# 實施架構

![image](https://user-images.githubusercontent.com/103306835/174040053-355481b3-5654-4c3b-b23e-ff44f14e2cd7.png)


# 發票資料

![image](https://user-images.githubusercontent.com/103306835/174040280-57566827-7216-4e49-b458-ef0f87ad6a1c.png)


# 操作步驟

![image](https://user-images.githubusercontent.com/103306835/174040336-a4bc78d6-9d69-4c3e-8c92-e92bade21d83.png)


# 步驟1：建立S3

1.搜尋S3

![image](https://user-images.githubusercontent.com/103306835/174040696-2cbb3e80-105a-4a3b-af42-5152a208e10e.png)

2.點選S3

![image](https://user-images.githubusercontent.com/103306835/174040744-57ac4dd0-58be-4019-bb65-05109e0aaac6.png)

3.點選[建立儲存貯體]

![image](https://user-images.githubusercontent.com/103306835/174040782-a046e175-eaa0-4c05-9aa3-b1033e46f43c.png)

4.輸入名稱：invoice-0616(名稱請自訂)

![image](https://user-images.githubusercontent.com/103306835/174040841-8dd6cc43-24b9-4fac-b370-4fa3588f1cd6.png)

5.點選[建立儲存貯體]

![image](https://user-images.githubusercontent.com/103306835/174040893-2e8239ee-a448-4eef-bc9c-24a999df6753.png)

6.成功建立儲存貯體

![image](https://user-images.githubusercontent.com/103306835/174040933-a5f3c305-0424-43af-9c82-5ec5d92b611d.png)

# 步驟2：上傳資料

1.點選儲存貯體

![image](https://user-images.githubusercontent.com/103306835/174041038-1753fd74-4472-4a19-8bc6-3fcd9cc89dc9.png)

2.點選[上傳]

![image](https://user-images.githubusercontent.com/103306835/174041117-ca3b662f-0054-43b4-930e-d9fc7881f071.png)

3.點選[新增檔案]

![image](https://user-images.githubusercontent.com/103306835/174041171-d653a14a-d0b1-4ee1-b127-0730aed96338.png)

4.點選[上傳]

![image](https://user-images.githubusercontent.com/103306835/174041215-34e5373e-637d-4af4-aedc-14f05a5c6587.png)

5.等待上傳

![image](https://user-images.githubusercontent.com/103306835/174041272-2aace7c8-112a-441c-8722-906d8f7f31e4.png)

6.成功上傳

![image](https://user-images.githubusercontent.com/103306835/174041584-e7ca0149-2ea7-43ee-b119-736c4d150a2b.png)

# 步驟3：建立Lambda

1.搜尋Lambda 並點選

![image](https://user-images.githubusercontent.com/103306835/174042571-acb69ba8-65ef-4fdf-8103-888674fe786c.png)

2.點選[建立函式]

![image](https://user-images.githubusercontent.com/103306835/174042618-3350d02d-73a6-4769-a0e1-29b8a8b9fa63.png)

3.點選[使用藍圖]

![image](https://user-images.githubusercontent.com/103306835/174042663-83655540-ca97-47e9-af24-22d15db64f74.png)

4.搜尋s3-get-object-python

![image](https://user-images.githubusercontent.com/103306835/174042691-6b6957d0-c38b-4513-aa37-de79a3fb1e1d.png)

5.點選s3-get-object-python

![image](https://user-images.githubusercontent.com/103306835/174042727-11c0fc83-6c2f-4fe7-b13c-ee5b3d385c5f.png)

6.點選[設定]

![image](https://user-images.githubusercontent.com/103306835/174042916-59882b98-cc59-4f32-8129-a0cad515558c.png)

7.輸入函數名稱getImagetext

![image](https://user-images.githubusercontent.com/103306835/174043002-bc8ecc7f-e55d-4cad-a1d8-4c4de08194f8.png)

8.勾選[使用現有的角色]

![image](https://user-images.githubusercontent.com/103306835/174043050-4719277f-a787-4623-8489-3e2e4c29d8ba.png)

9.選擇LabRole

![image](https://user-images.githubusercontent.com/103306835/174043090-88c3d538-d18d-43d6-8efe-4fc4cd7d5ae7.png)

10.選擇步驟1建立的S3

![image](https://user-images.githubusercontent.com/103306835/174043119-461c8f5d-5193-40eb-b6e6-068e54548c39.png)

11.點選[建立函式]

![image](https://user-images.githubusercontent.com/103306835/174043319-711ab2d8-59ac-437b-b579-e609f663430b.png)

12.點選[程式碼]頁籤

![image](https://user-images.githubusercontent.com/103306835/174043450-74e7d431-7b91-4634-9852-6ce42187c683.png)

13.點選[上傳於]

![image](https://user-images.githubusercontent.com/103306835/174043518-ce25e2c7-1abc-4429-a099-406efc6c063d.png)

14.貼上S3 URL

![image](https://user-images.githubusercontent.com/103306835/174043586-a11886dc-767e-4f17-adeb-f5d5d161fb3d.png)

15.點選[儲存]

![image](https://user-images.githubusercontent.com/103306835/174043627-e69da247-7571-4e8d-b95b-6bf0dbc1ae54.png)

16.點選[TEST]

![image](https://user-images.githubusercontent.com/103306835/174043683-396341d7-be41-42af-8974-015f3dd92bae.png)

17.輸入事件名稱：test

![image](https://user-images.githubusercontent.com/103306835/174044089-a45ff965-77b5-487a-9959-2e819d2b0b23.png)

18.修改成自己的S3跟照片名稱

![image](https://user-images.githubusercontent.com/103306835/174044144-90744b47-3eed-46b1-a793-adb268b5ed36.png)

19.點選[儲存]

![image](https://user-images.githubusercontent.com/103306835/174044209-a8bc1b8f-a3dc-4bd9-a3be-48173d0a92cc.png)

# 步驟4：圖片辨識文字

1.點選[Test]

![image](https://user-images.githubusercontent.com/103306835/174044338-047a594c-402e-4af8-adb9-cfc0478c7c15.png)

2.成功執行

![image](https://user-images.githubusercontent.com/103306835/174044392-035cbd9c-b0bb-42bf-a27f-ee51e40935fd.png)

3.回到S3 點選[更新]

![image](https://user-images.githubusercontent.com/103306835/174044427-83a00504-c912-431a-985d-6b7bec147d63.png)

4.產生TXT

![image](https://user-images.githubusercontent.com/103306835/174044476-87b7a8f4-8676-4137-b808-b883165c9b13.png)

5.

