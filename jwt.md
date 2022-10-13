#node 

參考文章
https://medium.com/@danilo.vilhena/what-are-json-web-tokens-for-27b0f5806da0
-   jwt 分成三個部分 三部分用dot隔開
    -   Header(會轉為base64)
        -   存有有加密的演算法等等資訊
    -   Payload (會轉為base64)
        -   我們需要用到的資訊
    -   Signature(將base64 進行加密）
        -   透過Header 提供的加密方法，將Header.payload 經由secret key加密
-   要有以上三部分才會解碼成功，才能使用我們的功能。

# payload
> JWT 的 payload 裡面有標準公認的訊息建議可以放一些。

-   iss(Issuer)：JWT簽發者
-   exp(Expiration Time)：JWT的過期時間，過期時間必須大於簽發JWT時間
-   sub(Subject)：JWT所面向的用戶
-   aud(Audience)：接收JWT的一方
-   nbf(Not Before)：也就是定義擬發放JWT之後，的某段時間點前該JWT仍舊是不可用的
-   iat(Issued At)：JWT簽發時間
-   jti(JWT Id)：JWT的身分標示，每個JWT的Id都應該是不重複的，避免重複發放
## 注意事項
- exp 必須大於 iat
- 像是 js 的套件就可以透過內建函式解碼，如果出來是過期他就幫我 throw Error。