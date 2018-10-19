## 1. Please compare hash function and cryptographic hash function and give an example

cryptographic hash function是hash function的一種，強調於安全方面，如，結果不可逆，抗碰撞等特性，如SHA3，至於一般hash function，只要是一個任意輸入能對應至固定格式的輸出，即可稱之為hash function，如F(X) = x %10


##  a. Can you print the private/public key with hex string representation? Please give us an example.

```javascript
// privKey
const privKey = wallet.getPrivateKeyString();
console.log("privKey:", privKey);

// pubKey
const pubKey = wallet.getPublicKeyString();
console.log("pubKey:", pubKey);
```

![](https://raw.githubusercontent.com/Yan-Bin-Lin/EtherClass_hw1/master/2.PNG)

## b. In addition, if we don’t want to use the getAddressString() to get the address, how can we obtain the address by hashing the public key?

```javascript
/***** address *****/

// step 2:  
const public_key_hash  = keccak256(pubKey)


// step 3:  
const address = "0x" + public_key_hash.slice(-40)
```

![](https://raw.githubusercontent.com/Yan-Bin-Lin/EtherClass_hw1/master/3.PNG)


## c. There is a file called Keystore that is used to encrypt the private key and save in a JSON file. Can you generate a Keystore with the password “nccu”? You can find the details about Keystore below.

```javascript
//JSON
const keystore = wallet.toV3("nccu");
console.log("keystore:",keystore);
```

![](https://raw.githubusercontent.com/Yan-Bin-Lin/EtherClass_hw1/master/4.PNG)


## What is HD Wallet, BIP32, BIP39 and BIP44? 

BIP 全名是 Bitcoin Improvement Proposals，是提出 Bitcoin 的新功能或改進措施的文件，BIP32, BIP39 and BIP44制定了HD錢包系統。

HD錢包為Hierarchical Deterministic（分層确定性）錢包，由一組私鑰，經過hash function後生成子私鑰，子私鑰也依此辦法能繼續增生其他私鑰，由於掌握了私鑰就能掌握該帳戶，父帳戶對子帳戶有絕對的權限，但基於hash function不可逆的原則，子帳戶沒辦法對父帳戶作甚麼，這辦法能應用在企業派發資金給底下的部門，方便監管金流，也能用在一個人管理多個帳戶，不用去一個一個處理許多帳戶。

BIP32定義了最初的分層系統，由單一的seed為源頭經過hash function去生成私鑰

BIP39：將 seed 用方便記憶和書寫的單字表示，一般由 12 個單字組成，稱為 mnemonic code(phrase)，經過hash function轉換為數字後再去生成私鑰

BIP44：基於 BIP32 的系統，賦予樹狀結構中的各層特殊的意義。讓同一個 seed 可以支援多幣種、多帳戶等，各層定義如下：
m / purpose' / coin_type' / account' / change / address_index


## What is RFC 6979 for?
比特幣是使用橢圓曲線加密法來生成私鑰的，其中的”K”值是隨機取出來的，如果K值為”偽”隨機(容易發生碰撞或其實是循環的)，容易造成私鑰跟著出問題，RFC6976定義了”確定性”的方法來生成”K”值，同時保證了”保密”與”唯一”
k = SHA256(d + HASH_function(m));
d為私鑰，確定了”保密”，m為文本，確定了”唯一”

