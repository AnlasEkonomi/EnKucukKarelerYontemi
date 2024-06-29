# En Küçük Kareler Yöntemi

Regresyon yazımızda Y= α + βX + ε  bir model yapısının nasıl ortaya çıktığını geometrik olarak göstermeye çalışmıştık.

Peki bu modelde Y bağımlı değişkeni tahmin etmek istersek ne yapacağız? İşte EKK (En Küçük Kareler) dediğimiz yöntem bu doğrusal denklemi tahmin etmek için kullanılan yöntemlerden bir tanesidir. 

Amacımız Y değişkenini gerçekteki değerine en yakın şekilde tahmin etmek ise bu durumda "ε" hata terimini minimize etmemiz gerekir.

Peki baştan başlayalım...

En Küçük Kareler Yönteminin ilk uygulamalarından birisi, Dünya’nın şeklinin belirsizliğini içeren bir anlaşmazlığı çözmek oldu. Isaac Newton 1687 yılında yayınladığı Philosophiae Naturalis Principia Mathematica (Doğa Felsefesinin Matematiksel Prensipleri) isimli kitabında, Dünya’nın mükemmel bir küre olmadığını, kutuplardan biraz daha basık bir yapıda olduğunu savundu. 

![image](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/dfdb2fc9-5721-41fc-b8ed-7e6624930085)

1718 yılında ünlü İtalyan astronom ve matematikçi Giovanni Domenico Cassini’nin oğlu Jacques Cassini, Paris Gözlemevi’nde yaptığı ölçümlerine dayanarak Dünya’nın şeklinin Prolate (limonun şekli gibi) bir yapıda olduğunu öne sürdü.

1736 yılında Fransız Bilimler Akademisi bu anlaşmazlığın çözümü için, Ekvator ve Finlandiya’nın kuzey bölgesi olan Laponya’ya araştırmacılar gönderdi. Ancak gelen verilere göre ölçüm hataları belirsizlik yaratacak kadar büyüktü. Bunun üzerine toplanan bu verilere bir doğru yerleştirmek, yani meridyen yayı uzunluğunu enlemle ilişkilendiren ve buna en iyi uyan doğruyu elde etmek için çeşitli yöntemler denenmişti.

![image](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/9df4af44-ee3e-491e-bd00-efc14821d9e9)


Uygulanan bazı yöntemler sonucunda, Newton’un teorisi destek bulmuş gibiydi ama sapmaların (hata terimlerinin) büyüklüğü sonradan fark edilecekti. 
1805 yılında Fransız matematikçi Adrien Marie Legendre bu sapmaları en aza indiren çizginin kullanılmasına yönelik bir yöntem yayınladı. Bu yöntemin adı en küçük kareler yöntemiydi. Daha sonra bu yöntemi kullanacak ve teorik olarak büyük katkılar sağlayacak olan kişi ise Alman matematikçi Carl Friedrich Gauss’dan başkası değildi. (Kaynak: https://www.britannica.com)


Basit bir regresyon modelinin yapısını Y= α + βX + ε şeklinde tanımlamıştık. Şimdi ilk amacımız “ε” dediğimiz hata terimlerini minimize edip, gerçeğe en yakın modeli tahmin edebilmek olacak. Peki modelde neleri tahmin etmemiz gerekiyor? X dediğimiz bağımsız değişkenler ve Y dediğimiz bağımlı değişkenler zaten bizim gözlemlerimizdi. O zaman geriye ne kalacak? “α” sabit terimimiz ve “β” dediğimiz eğim parametremiz veya diğer adıyla eğim katsayımız.

Yeni bir model yapısı tanımlayalım. Sakın kafanız karışmasın ama. Gayet açık ve net anlatacağım. 😊

Aşağıda tanımladığımız model aslında Y= α + βX + ε modeli için bir tahmin edici olarak kullanılacaktır.

y ̂=α ̂+β ̂x+ε ̂ 

y ̂ = Y için

α ̂ = α için

β ̂ = β için

ε ̂ = ε için 

Olmak üzere tahmin edici parametrelerdir. X için tahmin parametresi kullanmadık, çünkü gözlemlenebilir bağımsız değişken yapısıdır. O zaman yapıyı biraz daha düzenleyelim.

Hata terimi, gerçek model ile tahmin modeli arasındaki sapmalar ise,

ε ̂=Y-y ̂  şeklinde tanımlanabilir.

Amacımız hata terimlerinin toplamını minimize ederek, sabit ve eğim parametresini bulmak ise, yapıyı düzenlemeye devam edelim. Önce hataları toplayalım sonra y ̂  yerine α ̂+β ̂x yapısını yazalım.

![1](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/eb1575df-bea0-42f6-9fda-ecaded517dd1)

Ama burada bir problem var? Hata terimleri matematiksel olarak artı veya eksi değerler alabilir. Ancak bizim için önemli olan nokta, hata terimlerinin, regresyon doğrusuna olan uzaklığıdır. Eğer hata terimlerini toplarsak, artı veya eksi değerler yüzünden uzaklık ölçüsünü hatalı ölçebiliriz. Bu yüzden biz hataların toplamı yerine hataların kareleri toplamını alacağız. İşte en küçük kareler yöntemine ismini veren yapıda burasıdır. O zaman yapıyı hataların kareleri toplamı şeklinde düzenlersek;

![2](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/413eddbc-5576-481b-a87a-722f104784c4)

Şimdi yine bir lise yıllarına gidelim. Dersimiz matematik, konumuz türev!

F(x) = ax² + bx + c ve a ≠ 0 şeklinde ikinci derece bir parabol düşünün. Bunu standart formda ifade edersek, f(x) = a(x-h)2 + k şeklinde olur. Burada eğer a > 0 ise parabolün kolları yukarı, a < 0 ise parabolün kolları aşağı olacaktır. Bizim çözmek istediğimiz üstteki yapı cebirsel olarak incelenirse katsayılar nedeni ile parabolün kollarının yukarı olduğunu görebiliriz. Bunun için bu yapıyı tek tek açmamız gerekiyor ama ben bunu burada yapmayacağım. Eğer bunu cebirsel olarak görmek isterseniz buradan https://brownmath.com/stat/leastsq.htm#FindCalc  inceleyebilirsiniz. 

Benim anlatmak istediğim ise bu parabolün hem α hem de β ̂ parametrelerinin tepe noktasının minimum değeri için kısmi türev alınması gerektiğini göstermektir. Bu şekilde hata terimini minimum yapan α ve β ̂ parametrelerini bulacak formülü elde edebiliriz. Burası biraz karışık geldiyse bile sakın korkmayın, adım adım devam ediyoruz. 

İlk olarak α için kısmi türev alıp sıfıra eşitleyelim;

![3](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/ecec2429-ac83-40b9-94aa-27047fac4546)


Şeklinde olacaktır. Bu şimdilik burada dursun ve biz yolumuza diğer parametre olan β ̂ parametresine göre kısmi türev alarak devam edelim. Tamamen aynı mantık;

![4](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/c4d3e90f-df9c-474d-8c37-6d4e12171089)

Hem α hem de β parametreleri için bulduğumuz bu iki yapıya “Normal Denklemler” ismi verilir.

Şimdi ise bu denklemleri alt alta çözerek, parametrelerimizin tahmincilerini bulalım.

![5](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/114b9cae-cef0-4abb-bd6d-ad66ec90b594)

Burada ilk yapmamız gereken nokta bağımlı değişkenleri içeren yapıları eşitliğin sol tarafına atmak olacak. Şimdi tekrar düzenleyelim;

![6](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/466f3fdb-528e-4281-b92f-879757ae6f84)

Bu doğrusal denklem yapısı “Cramer Yöntemi” (Bir lineer denklem çözüm yöntemidir) ile çözülürse, tahmin ediciler aşağıdaki gibi olacaktır;

![7](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/eebf3a4e-5272-48cf-a547-1a2b424d0ff5)


Artık X ve Y değişkenlerini kullanarak, hata terimlerini minimum yapan sabit ve eğim parametrelerini bulabiliriz. Çünkü çözüm denklemine artık sahibiz.

Bu denklem bir çok istatistiksel paket programları, yazılım dilleri kütüphaneleri içerisinde gömülü olarak mevcuttur. Ayrıca Excel'de "Solver" eklentisi ile rahatlıkla kullanılabilir.

Biz Excel ile eklenti olmadan bu matematiği kullanarak küçük bir örnek yapacağız.

İlk olarak excel sütunlarına verilerimizi ve ihtiyacımız olan yapıları tanımlayalım;

![image](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/cb4854de-9d9f-4dc7-b258-b9b5c3924dd8)


Daha sonra aşağıdaki formülleri kullanarak sonuçları hesaplayalım;

![image](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/f37369cc-8648-4331-a43e-bc3cbfedfeea)

![image](https://github.com/AnlasEkonomi/EnKucukKarelerYontemi/assets/173607120/3bf36c07-5a46-4d46-b2f3-edbe5596a6b1)

α değerimizi -234,38
β değerimizi 7,8833 olarak bulduk.

O zaman regresyon modelimizi yazabiliriz değil mi?

Y = -234,38 + 7,8833X  

Yani X değişkenimiz sıfır olduğu varsayımında Y değişkenimiz -234,38 değerini alırken, X değişkenimiz bir birim arttığında Y değişkenimiz 7,88 birim artacaktır.

Burada yaptığımız şey en basit hali ile bir bağımlı bir de bağımsız değişken arasındaki doğrusal ilişkiyi kullanarak hataları minimize eden denklem sistemi ile tahmin etmek oldu.

Tabi ki bu işlem tamamen örnek amaçlıdır. En küçük kareler yöntemi varsayımlarının test edilmesi, güven aralığında model ve parametre anlamlılıkları hipotez testleri ile sınanması gerekmektedir.

Saygılarımla...

