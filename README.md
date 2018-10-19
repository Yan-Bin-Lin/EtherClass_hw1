## 1. Please compare hash function and cryptographic hash function and give an example

cryptographic hash function�Ohash function���@�ءA�j�թ�w���譱�A�p�A���G���i�f�A�ܸI�����S�ʡA�pSHA3�A�ܩ�@��hash function�A�u�n�O�@�ӥ��N��J������ܩT�w�榡����X�A�Y�i�٤���hash function�A�pF(X) = x %10


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

## b. In addition, if we don��t want to use the getAddressString() to get the address, how can we obtain the address by hashing the public key?

```javascript
/***** address *****/

// step 2:  
const public_key_hash  = keccak256(pubKey)


// step 3:  
const address = "0x" + public_key_hash.slice(-40)
```

![](https://raw.githubusercontent.com/Yan-Bin-Lin/EtherClass_hw1/master/3.PNG)


## c. There is a file called Keystore that is used to encrypt the private key and save in a JSON file. Can you generate a Keystore with the password ��nccu��? You can find the details about Keystore below.

```javascript
//JSON
const keystore = wallet.toV3("nccu");
console.log("keystore:",keystore);
```

![](https://raw.githubusercontent.com/Yan-Bin-Lin/EtherClass_hw1/master/4.PNG)


## What is HD Wallet, BIP32, BIP39 and BIP44? 

BIP ���W�O Bitcoin Improvement Proposals�A�O���X Bitcoin ���s�\��Χ�i���I�����ABIP32, BIP39 and BIP44��w�FHD���]�t�ΡC

HD���]��Hierarchical Deterministic�]���h�̩w�ʡ^���]�A�Ѥ@�ըp�_�A�g�Lhash function��ͦ��l�p�_�A�l�p�_�]�̦���k���~��W�ͨ�L�p�_�A�ѩ�x���F�p�_�N��x���ӱb��A���b���l�b�ᦳ���諸�v���A�����hash function���i�f����h�A�l�b��S��k����b��@�ƻ�A�o��k�����Φb���~���o��������U�������A��K�ʺު��y�A�]��Φb�@�ӤH�޲z�h�ӱb��A���Υh�@�Ӥ@�ӳB�z�\�h�b��C

BIP32�w�q�F�̪쪺���h�t�ΡA�ѳ�@��seed�����Y�g�Lhash function�h�ͦ��p�_

BIP39�G�N seed �Τ�K�O�ЩM�Ѽg����r��ܡA�@��� 12 �ӳ�r�զ��A�٬� mnemonic code(phrase)�A�g�Lhash function�ഫ���Ʀr��A�h�ͦ��p�_

BIP44�G��� BIP32 ���t�ΡA�ᤩ�𪬵��c�����U�h�S���N�q�C���P�@�� seed �i�H�䴩�h���ءB�h�b�ᵥ�A�U�h�w�q�p�U�G
m / purpose' / coin_type' / account' / change / address_index


## What is RFC 6979 for?
��S���O�ϥξ�ꦱ�u�[�K�k�ӥͦ��p�_���A�䤤����K���ȬO�H�����X�Ӫ��A�p�GK�Ȭ��������H��(�e���o�͸I���Ψ��O�`����)�A�e���y���p�_��ۥX���D�ARFC6976�w�q�F���T�w�ʡ�����k�ӥͦ���K���ȡA�P�ɫO�ҤF���O�K���P���ߤ@��
k = SHA256(d + HASH_function(m));
d���p�_�A�T�w�F���O�K���Am���奻�A�T�w�F���ߤ@��

