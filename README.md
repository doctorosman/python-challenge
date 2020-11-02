# PYTHONCHALLENGE.COM ÇÖZÜMLERİ
[Python Challenge](http://www.pythonchallenge.com) sitesinde yer alan meydan okumaların Türkçe çözümleri için oluşturulmuş bir repodur. Projeyi forkleyerek katkıda bulunabilirsiniz. Meydan okumalara farklı yöntemle çözümler de ekleyebilirsiniz.

## ÇÖZÜMLER
0. URL'de yer alan '0.html' bölümünü 2^38 sayısıyla değiştirmeniz gerekiyor. ([#1](http://www.pythonchallenge.com/pc/def/274877906944.html))
```2^38 = 274877906944```
1. Verilen görselde harfler alfabede iki sıra atlatılmış. Bu yüzden verilen metnin her karakterini iki atlatarak çözüme ulaşmanız gerekiyor. Bunun için maketrans() fonksiyonunu kullanabilirsiniz.
```i hope you didnt translate it by hand. thats what computers are for. doing it in by hand is inefficient and that's why this text is so long. using string.maketrans() is recommended. now apply on the url.```
Türkçesi:
```Umarım bu metni elle çevirmemişsindir. Bilgisayarlar bunun için var. Elle çevirmek etkisiz olur, o yüzden bu metin bu kadar uzun. string.maketrans() kullanmanız önerilir. Şimdi de URL için uygulayın.```
Bu bağlamda URL'deki 'map' için aynı yöntemi uygularsanız bir sonraki meydan okumaya geçebilirsiniz. ([#2](http://www.pythonchallenge.com/pc/def/ocr.html))
2. Bu meydan okumada öncelikle 'Ctrl + U' tuş kombinasyonuyla sayfanın kaynağına gitmelisiniz. Daha sonra verilen karmaşık metindeki sayıca az olan karakterleri bulmanız isteniyor. Çözüm için metni kopyalayıp bir metin belgesine yapıştırın. Daha sonra dosyayı Python'da açarak okuyun. Devamında metinde hangi karakterden kaç tane olduğunu öğrenmek için for döngüsü kullanabilirsiniz.
```python
metin = open('metin.txt').read()
sayilar = dict()

for i in metin:
    sayilar[i] = sayilar.get(i, 0) + 1

print(sayilar)
```
Yukarıdaki kodu çalıştırdığınızda aşağıdaki sonucu alacaksınız.
```{'%': 6104, '$': 6046, '@': 6157, '_': 6112, '^': 6030, '#': 6115, ')': 6186, '&': 6043, '!': 6079, '+': 6066, ']': 6152, '*': 6034, '}': 6105, '[': 6108, '(': 6154, '{': 6046, '\n': 1219, 'e': 1, 'q': 1, 'u': 1, 'a': 1, 'l': 1, 'i': 1, 't': 1, 'y': 1}```
Burada karşımıza çıkan harfler 'equality' kelimesini oluşturuyor. Dolayısıyla 'equality.html' sayfasına gidebilirsiniz. ([#3](http://www.pythonchallenge.com/pc/def/equality.html))
3. Bu meydan okumada verilen metnin Türkçesi: 'Bir küçük harf, her iki tarafı üç büyük koruma ile sarılı.' Önceki meydan okumada olduğu gibi sayfanın kaynağına gidip oradaki metni bir metin belgesine yapıştıralım. Daha sonra Python ile bu metin belgesinde 'üç büyük harf + bir küçük harf + üç büyük harf' şeklinde olan kelimeyi bulmamız gerekiyor. Bunu regex araması ile gerçekleştirebiliriz.
```python
import re
metin = open('metin.txt').read()

kelime = re.findall("[^A-Z]+[A-Z]{3}([a-z])[A-Z]{3}[^A-Z]+", metin)
print("".join(kelime))
```
Yukarıdaki kodu çalıştırdığınızda 'linkedlist' kelimesine ulaşacaksınız. ([#4](http://www.pythonchallenge.com/pc/def/linkedlist.html))
4. 'linkedlist.html' sayfasına gittiğimizde bizi 'linkedlist.php' sayfasına yönlendiriyor. Bu sayfadaki görsele tıkladığımızda 'linkedlist.php?nothing=12345' sayfasına ulaşıyoruz. Burada sürekli karşımıza çıkan farklı bir sayıyı URL'deki 'nothing' kısmına yazmamız istenecek. Bunun yerine 'linkedlist.php' sayfasının kaynağında belirtildiği gibi urllib modülünü kullanabiliriz. Sayfanın kaynağında ayrıca bu işlemi 400 kez yapmanın yeterli olacağı söyleniyor. Python kısmına geçelim.
```python
import urllib.request as req

url = 'http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing='

sayi = '12345'
metin = 'and the next nothing is '
metin2 = '<font color=red>Your hands are getting tired </font>and the next nothing is '

c = 1
while True:
    sayfa = req.urlopen(url + sayi).read().decode('utf-8')

    print(c, sayfa)
    
    if sayfa.startswith(metin):
        sayi = sayfa.replace(metin, '')
    elif sayfa.startswith(metin2):
        sayi = sayfa.replace(metin2, '')
    else:
        break
    c += 1
```
Yukarıdaki kodu çalıştırıp bir süre bekledikten sonra '86 Yes. Divide by two and keep going.' (İkiye böl ve devam et.) yazısıyla program sonlanacak. Bu bağlamda sayi değişkenimizi 16044 sayısının yarısı olan 8022 ve c değişkenimizi de 87 ile değiştirip programı tekrar çalıştıralım.
```python
sayi = '8022'
c = 87
```
Kodu bu şekilde değiştirip programı tekrar çalıştırınca aşağıdaki çıktıyı alıyoruz.
```141 There maybe misleading numbers in the text. One example is 82683. Look only for the next nothing and the next nothing is 63579```
Devamında değişkenlerimizi tekrar değiştirip programı tekrar çalıştırıyoruz.
```python
sayi = '63579'
c = 142
```
Programı çalıştırdığımızda son olarak 'peak.html' yazısını görüyoruz. ([#5](http://www.pythonchallenge.com/pc/def/peak.html))