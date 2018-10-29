
我們需要在前端先用 Javascript 做 AES 加密在傳到後端

```javascript
var myString   = "hello world";
var myPassword = "0123456789abcdef0123456789abcdef";

function AESEncrypto(str, key){                                 
        key = CryptoJS.enc.Utf8.parse(key);
        // 加密結果返回的是CipherParams object類型                                                          
        var encrypted = CryptoJS.AES.encrypt(str, key, {        
                iv: key,                                        
                mode: CryptoJS.mode.CBC,                        
                padding: CryptoJS.pad.Pkcs7                     
        });
        // ciphertext是密文，toString()內傳編碼格式，比如Base64，這裡用了16進制
        return  encrypted.ciphertext.toString(CryptoJS.enc.Base64);
}


function AESDecrypt(str, key){                                 
        key = CryptoJS.enc.Utf8.parse(key);
        // 加密結果返回的是CipherParams object類型                                                          
        var decrypted = CryptoJS.AES.decrypt(str, key, {        
                iv: key,                                        
                mode: CryptoJS.mode.CBC,                        
                padding: CryptoJS.pad.Pkcs7                     
        });
        // ciphertext是密文，toString()內傳編碼格式，比如Base64，這裡用了16進制
        return  decrypted.ciphertext.toString(CryptoJS.enc.Utf8);
}
```



References:
https://blog.csdn.net/Planet_X/article/details/78496823
https://www.jianshu.com/p/9c1c8958b279