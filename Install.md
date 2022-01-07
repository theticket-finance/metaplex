# Bağımlılıklar

Proje için aşağıdaki paketler kurulu olmalı. 

Canvas: 
https://github.com/Automattic/node-canvas 

Rust Lang: 
https://www.rust-lang.org/tools/install

npx ts-node:
npm install -g ts-node
(MacOS'da npm i ts-node ile kurdum.) 

# İhtiyaçlar: 
Bir wallet'a ihtiyacınız var. Wallet'da fee'leri ödeyebilecek kadar sol (0.5 yeterli) olmalı. 
Phantom App tavsiye ederim: 

https://chrome.google.com/webstore/detail/phantom/bfnaelmomeimhlpmgjnjophhpkkoljpa?hl=en

Kurulum bilgileri readme içinde mevcut. 

Kurulumu şu versiyonlarda yapabildim:

Node: v16.11.1 

Yarn: 1.22.17 

npx ts-node -v: v10.4.0


Kurulum tamamlandıktan sonra .env klasörüne eklemenizi isteyecek bir bilgi var. Onu kopyalamayı unutmayın. Not alın. 


js/packages/web/.env içine bunu yapıştırıp; diğer iki satırı da şu şekilde düzenleyin: 

SPL_TOKEN_MINTS=AymKzSDznoLT7Vhsb4wSRnCj1gjcG3zkgYFY8fxsHHer

CG_SPL_TOKEN_IDS=ticket


SPL_TOKEN_MINTS: Hangi Token ile satış yapılabileceğini belirtebiliyoruz. Virgüllerle USDC veya farklı tokenlar da eklenebilir. SOL default olarak var. 

CG_SPL_TOKEN_IDS: Bu nedir bilmiyorum. İlk kurulumda isimlerini gördüğüm için, ticket yazdım ve satın alımlarda veya satışta token olarak "TICKET" seçiliyor.

# NFT Oluşturma:
- Cüzdanınız ile bağlanın
- Sağ üstte cüzdana tıklayıp "Create" seçin 
- Açılan ekranda NFT tipini seçmeniz istenecektir. Image, Video, Audio, AR/3D ve HTML Asset destekleniyor. 
- Tip seçtikten sonra Upload ekranına geleceksiniz. Dosyayı Seçin ve devam edin.
- NFT detaylarını tanımlayacağımız ekran açılacak. Bunlar;
- - Title: NFT adı. Sonlarına #1, #2 gibi sayılar giriliyor. Bunun bir anlamı olmalı. araştırmalıyız. 
- - Symbol: NFT Sembolü. Ben TCKT giriyorum. Bu sembol kısalma gibi düşünülmemelidir. 
- - Description: NFT açıklaması. 
- - Maximum Suppy: Maximum arz sayısı (test için 1 giriyorum) 
- - Properties (Özellikler) alanı da key-value ve display type diye 3 alan alıyor. display_type opsiyonel ve "Date" ile unix zaman damgası girildiği yazıyor. Detaylar https://medium.com/metaplex/metaplex-metadata-standard-45af3d04b541 adresinde.  Bilgileri girdikten sonra devam. 
- Telif Hakları: Bir NFT'nin ilk üreticisi, telif hakkını koruyabiliyor. Bir NFT ilk üreten, telif yüzdesi belirtirse, ilk satış sonrası her el değiştirdiğinde satıştan belirttiği %'lik kadar komisyon alabilir. Bunu test için sıfır yapalım.. 
- NFT pay edilebiliyor. Birden fazla cüzdanın yüzde kaç hakkı olduğunu belirtebiliyoruz. Şimdilik test için tek cüzdana %100 hakkı veriyoruz. Bu ortaklaşa bir nft almak üzere mi kurgulanmış acaba? Satışta her iki cüzdanın da onayı gerekeceği kesin. Araştırmaya devam ediyorum. Bilgileri girdikten sonra devam
- Ödeme ekranı: NFT oluşturanın maaliyeti vardır. Bu bana her zaman 0.0071 SOL olarak geliyor. Account ücreti, transaction ücreti etc. hepsi içinde. Ödeme yaptıktan sonra adım adım progress işliyor. Progress'de 2 defa onaylamanız gereken işlem var. İlki account create etme ve transaction ücreti iken, ikincisi hesabımıza NFT'yi yükleme ve onun transaction ücretidir. İşlemler bittikten sonra cüzdanınızda NFT'yi görmeye başlarsınız. Hayırlı olsun.


# Oluşturulan NFT'yi satışa koyma
NFT'leri 5 farklı şekilde satışa sunabilirsiniz. Biz yukarıda bir tane oluşturduğumuz için, "Mevcut NFT Satışı" seçtik. Ama burada farklı işlemler de var. NFY'yi satın aldıkça o an üretip de teslim eden, sınırlı sayıda üretilmesine izin veren (Mesela 100 tane 1st class gibi. Satın alındıkça ödemeyi alır ve NFT verir. 100. adet satıldıktan sonra satışlara kapanır), Açık arttırma ile (belli zaman aralığı ve her tekif arası belli zaman ve minimum artış oranı bilgileri ile) ilk 3'e NFT'yi (3 farklı nft oluyor) verir. Diğer katılımcılara da ücretleri iade edilir. (Komisyonlar katılımcılardan kesiliyor). 
Bunlar detaylıca test edilmeye devam ediliyor. 
Mevcut NFT satışı ile satış yapıldığında: 
- NFT store'a gidiyor. 
- Kullanıcı store'dan (belirttiğimiz miktar ve belirttiğimiz token veya sol ile) satın alabiliyor. 
- NFT kullanıcıya ulaşıyor. 
- Kullanıcıdan belirtilen miktarda token alınıyor. 
- **SORUN:** Kullanıcıdan alınan token satıcıya gitmiyor bi türlü. Bu adımda tıknadık. 


## Anında Satış | Instant Sale
## Sınırlı Sayıda Satış | Limited Edition
## Açık Sürüm (Sınırsız) | Open Edition
## Açık Arttırma | Tiered Auction
## Mevcut NFT Satışı | Sale an Existing Item
