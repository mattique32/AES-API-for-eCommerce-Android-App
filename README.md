AESCrypt-Android
================

Simple API to perform AES encryption on Android with no dependancies. 

For compatiblity with AESCrypt, AESCrypt-Android has the same defaults namely: 

 * 256-bit AES key
 * CBC mode
 * PKCS7Padding
 * Blank/Empty IV **(default*)** 

```java
dependencies {
  compile 'com.scottyab:aescrypt:0.0.1'
}
```

# Usage

## Encrypt

```java
String password = "password";
String message = "hello world";	
try {
    String encryptedMsg = AESCrypt.encrypt(password, message);
}catch (GeneralSecurityException e){
    //handle error
}
```

## Decrypt

```java
String password = "password";
String encryptedMsg = "2B22cS3UC5s35WBihLBo8w==";
try {
    String messageAfterDecrypt = AESCrypt.decrypt(password, encryptedMsg);
}catch (GeneralSecurityException e){
     //handle error - could be due to incorrect password or tampered encryptedMsg
}
```

## Recommended ~Advanced~ usage

Please if you are going to use this library provide your own key, and use a different IV per message that you encrypt.. 

`AESCrypt.encrypt(final SecretKeySpec key, final byte[] iv, final byte[] message)`

`AESCrypt.decrypt(final SecretKeySpec key, final byte[] iv, final byte[] decodedCipherText)`

**Note:** for flexibility these 'adv' methods don't provide BASE64 encoding/decoding.


## Debugging/Logging

To enable logging simple change switch on the logging flag as shown below.   

`AESCrypt.DEBUG_LOG_ENABLED = true;`

*Remember to disable in Live, recommend the below snippet if possible*


```java
if (BuildConfig.DEBUG) {
    AESCrypt.DEBUG_LOG_ENABLED = true;
}
```
       
   
