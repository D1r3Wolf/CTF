# Reverse : Hard-looks

```
Given Cipher Text :
--_--___--_-_-__--_--__--__-_-__--_--___--__--__--_---__--__-___--_---__---__-__--_---__--______--_---__--_-____--_-____--__--__--_-_-__--_-____--_-____--_--___--_---_--___-___--_-_-__--_---__--__--__--_-____--__--__--_-_-__--_-_-_--__--___--__--__--___-__--__--__--_---__--_-_-_--__--___--_-____---_____--__--__--_-____--_-_-__--__-___--_-____--_-____--_-_-_--__--___--__--__--__--__--_-___--__-_-__--__--__--______--_-_-__--_-_-__--_-____--_---__--_-____---_____--__--_--__--___--__-___--___-__--_---_--__-__
```
* Its looks likes MOrse code, But morse code needs delimeter,
* Then Assumed then like a binary and conveted them into string

```py
from Crypto.Util.number import long_to_bytes
def Bin_to_Str(S):
	Long = int(S,2) # base 2 to base 10
	return long_to_bytes(Long) # base 10 to base 256(str)

Ct = "--_--___--_-_-__--_--__--__-_-__--_--___--__--__--_---__--__-___--_---__---__-__--_---__--______--_---__--_-____--_-____--__--__--_-_-__--_-____--_-____--_--___--_---_--___-___--_-_-__--_---__--__--__--_-____--__--__--_-_-__--_-_-_--__--___--__--__--___-__--__--__--_---__--_-_-_--__--___--_-____---_____--__--__--_-____--_-_-__--__-___--_-____--_-____--_-_-_--__--___--__--__--__--__--_-___--__-_-__--__--__--______--_-_-__--_-_-__--_-____--_---__--_-____---_____--__--_--__--___--__-___--___-__--_---_--__-__"

A = Ct.replace('-','0').replace('_','1')
B = Ct.replace('-','1').replace('_','0')

print (Bin_to_Str(A))
print (Bin_to_Str(B))
```
* output
```
$ python exp.py 
	�ɚ����������������ȝ������ʙ����ʙ��������ʙ��˚��������̙��ț
656e63727970744354467b5734355f31375f483452445f334e305547483f217d
```
* Therefore 'B' is the correct String ; We have hex decode it

### Python CODE :
```py
from Crypto.Util.number import long_to_bytes
def Bin_to_Str(S):
	Long = int(S,2) # base 2 to base 10
	return long_to_bytes(Long) # base 10 to base 256(str)

Ct = "--_--___--_-_-__--_--__--__-_-__--_--___--__--__--_---__--__-___--_---__---__-__--_---__--______--_---__--_-____--_-____--__--__--_-_-__--_-____--_-____--_--___--_---_--___-___--_-_-__--_---__--__--__--_-____--__--__--_-_-__--_-_-_--__--___--__--__--___-__--__--__--_---__--_-_-_--__--___--_-____---_____--__--__--_-____--_-_-__--__-___--_-____--_-____--_-_-_--__--___--__--__--__--__--_-___--__-_-__--__--__--______--_-_-__--_-_-__--_-____--_---__--_-____---_____--__--_--__--___--__-___--___-__--_---_--__-__"

B = Ct.replace('-','1').replace('_','0')
S = Bin_to_Str(B)
flag = S.decode('hex')
print "[+] flag :",flag
```
### output
```
$ python exp.py 
[+] flag : encryptCTF{W45_17_H4RD_3N0UGH?!}
```

## flag is : `encryptCTF{W45_17_H4RD_3N0UGH?!}`