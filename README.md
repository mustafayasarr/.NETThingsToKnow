**C# VE .NET BİLİNMESİ GEREKENLER**

-   **Coalescing Operator Nedir?**

Bir değişkenin null olması durumunda eğer Coalescing Operatör'ün ne
olduğunu bilmiyorsak alttaki gibi bir kontrol ve null olması durumunda
gerekli işlemleri yaparız. Örnek olarak alttaki gibi.



var name = null;

if (name == null) {

name = "Varsayılan Ad";

}



Ama alttaki gibi kolayca Coalescing Operatör'ü kullanılarak tek satırda
null check ve varsayılan değer atama işlemini yapabiliriz.

```csharp

var name = null;

name = name ?? "Varsayılan Ad";

```

-   **C# Struct ile Class Arasındaki Farklar Nelerdir?**

Temelde classlar structların yapabildiği herşeyi yapabilmekte. Peki
aradaki temel fark nedir? Bu sorunun cevabı OOP mimarisinde yatmaktadır.
struct ile classların arasındaki en büyük fark (OOP'un en güçlü
özelliği) kalıtımdır. structlar kalıtımı desteklememektedir. Bu sorunun
kısaca cevabı budur. Bu cevaptan sonra diyebilirsiniz ki classlar
structların bütün özelliklerini yerine getirebiliyorlarsa o zaman C#'ta
structlar neden var derseniz, structlar daha performanslıdır. Yüksek
performas gerektiren bazı özel durumlarda class yerine struct tercih
edilebilir. Böylece classların referans özelliğinden kaynaklı ek
işlemlerin olmamasıyla performans artacaktır.

-   **Abstract class ile Interface Arasındaki Farklar Nelerdir?**


-   Interface ve abstract class'lar new anahtar sözcüğü ile
    oluşturulamazlar.

-   Bir sınıf birden fazla interface'i kalıtım olarak alınabilir ama bir
    sınıfa bir tane abstract class kalıtım alınabilir.

-   Interface içerisinde boş metodlar tanımlanabilir ama abstract
    class'larda hem boş metodlar tanımlanabilir hemde içi dolu metodlar
    tanımlabilir.

-   Abstract sınıflar içerisinde metod gövdeleri tanımlanıp özellik
    değerleri ayarlandığı için genellikle sonradan geliştirilmek için
    kullanılıır ama interface ise body ve değer set edilemediği için
    tamamen interface üzerinden tüm üyeleri implemente edilerek
    geliştirmelere yapılması gereken durumlarda kullanılır.

-   Abstract class'lar içerisinde sadece abstract olarak işaretlenmiş
    metod ve özellikler implement edilmek zorundadır fakat interface
    içerisindeki tüm özellik ve metodlar implement edilmek zorundadır.

-   Bir class bir tane abstract class'ı kalıtım olarak alabilir ama bir
    class istenilen sayıda interface'i kalıtım olarak alabilir.

-   Interface içerisinde özellik ve metodlarda erişim belirleyiciler
    kullanılmaz herşey public olarak kabul edilir fakat abstract
    sınıflarda kullanılabilir.

-   Abstract sınıflara diğer sınıf ve interface'ler kalıtım olarak
    geçilebilir fakat interface'e herhangi bir yapı kalıtım olarak
    geçilemez.


-   **C#'da Class'a Farklı Bir Interface Birde Class Inherit Etmem
    Gerekiyor Sırası Önemli mi?**

Evet önemli çünkü bir class'a en fazla bir tane class inherit
edilebiliyor ama istenilen sayıda interface inherit edilebiliyor bu
durumda eğer class ve interface inherit edecekseniz öncelikle class
virgül ile ayırarak diğer interface'lerinizi eklemelisiniz.

Örnek verecek olursak alttaki gibi bir kullanımda "Error CS1722 Base
class 'A' must come before any interfaces" hatası alacaksınız. Bu
hatanın nedenini zaten bir üstteki paragrafta söylemiştik inherit
durumunda önce class sonrasında diğer interface'leriniz eklenmelidir.

```csharp

public class A { }

public interface B { }

public abstract class C : B, A { }

```

Yani olması gereken sözdizimi şu şekildedir.

```csharp

public class A { }

public interface B { }

public abstract class C : A, B { }

```

-   **SortedList Nedir?**

Sortedlist verileri key-value(anahtar-deger) olarak saklanmaktadır.
Sortedlist'in farkı içerisindeki verileri sıralı olarak saklamasıdır.
Sıralama key değerine göre asc(a-z) türünde yapılmaktadır. Sıralama
metin yada sayısal değer üzerinden yapılabilmektedir.

-**Virtual, abstract, interface, Sealed ve static keywordlerini
    kısaca açıklayınız.**

**Interface (Arayüz),** İçinde sadece kendisinden türeyen sınıfların
içini doldurmak zorunda olduğu içi boş metot tanımlarının yapıldığı bir
yapıdır.

**Abstract (Soyut),** içerisinde normal yani içi dolu metotların,
değişkenlerin ve interface'lerdeki gibi abstract (boş) metodların
tanımlanabildiği yapılardır.

**Sealed,** Miras(Inheritance) alınmasını istemediğiniz sınıflar için
kullanabileceğiniz bu keyword sayesinde kullanılan class hiçbir şekilde
başka bir class'a miras olarak geçilemez. Özetle Sealed, sınıflar için
kalıtım yapmayı, üyeler için ise override edilmeyi önler.

```csharp

public sealed class A

{

public object Prop1 { get; set; }

}

public class B : A

{

public object Prop2 { get; set; }

}

Üstteki kodu çalıştırdığınızda 'B': cannot derive from sealed type 'A'
hatasını fırlatacaktır. A sealed olarak işaretlendiğinden B'ye miras
olarak geçemedim ama sealed olarak işaretlenmiş bir class'a sealed
olmayan bir class miras olarak geçilebiliyor.

```csharp

public class C

{

public object Prop2 { get; set; }

}

public sealed class D : C

{

public object Prop1 { get; set; }

}

 ```

 

Bu şekilde bir kullanımda herhangi bir sorun çıkmayacaktır.

**Static,** Static olarak tanımlanan üyeler(class, property, field)
ram'de tek seferlik bir tanım yapılması sağlanır ve her okuma işleminde
ram'deki bu kaynaktan doğrudan okunması sağlanır. Class özelinde static
tanımını şöyle yapabiliriz; Bir instance almaya gerek duymadan doğrudan
static olarak tanımlanmış sınıfın üyelerine erişilebilir ve değer
ataması yapılabilir.

**Virtual (Sanal),** Sınıf içerisinde sanallaştırmak istediğimiz yani
çakışma durumunda veya gövdesinin gerçekleştirdiği işlemin uygun
olmadığını düşündüğünüz zaman ezmek istediğimiz metot türleridir.

-   **WCF nedir? Neleri içerir?**

Windows Communication Foundation, .Net framework 3.0'ın çıkartılmasıyla
birlikte, .Net framework ile yazdığınız uygulamaların birbiri ile
konuşmasını sağlayan bir kütüphanedir. .Net Remoting, XML Web
Servisleri, MSMQ, Net pipe, tcp/ip gibi pek çok farklı yöntemi tek bir
çatı altında toplar.

WCF ile geliştirilen servisler, SOAP spesifikasyonu ile HTTP , TCP ,
MSMQ gibi transfer protokolleri üzerinden sunulmaktadır.

-   **.Net Core DI (Dependency Injection) Yapısına Enjekte Edilen Tipler
    için Nesne Yaşam Süreleri (Lifecycle)**

Önceki kısımlarda bahsettiğim gibi kendimize ait tipleri veya harici
kütüphanelerden gelen tipleri de ASP.NET Core'un DI yapısına enjekte
edebiliyoruz. Bu şekilde tip bağımlılıklarını projenin giriş noktası
olan ConfigureServices metodundan yönetmemiz mümkün oluyor.

Yukarıdaki örnekte ILogger tipi için singleton bir nesne oluşturmuştuk.
Singleton ile birlikte Transient ve Scoped olmak üzere nesne yaşam
süresine karar verebileceğimiz 3 farklı yöntem bulunuyor. Aşağıda bu
yöntemleri kısaca açıklamaları bulunuyor:

**-- Transient:** Nesneye yapılan her çağrıda yeni bir nesne
oluşturulur. Stateless nesneye ihtiyaç duyulan durumlarda kullanılır.
AddTransient() metodu aracılığıyla Transient tipinde bağımlılıklar
oluşturabiliriz.

**-- Scoped:** Yapılan her request'te nesne tekrar oluşur ve bir request
içerisinde sadece bir tane nesne kullanılır. Bu yöntem için de
AddScoped() metodu kullanılıyor. Transient ve Scoped kullanım şekilleri
nesne oluşturma zamanları açısından biraz karıştırılabilir. Transient'da
her nesne çağrımında yeni bir instance oluşturulurken, Scoped'da ise
request esnasında yeni bir instance oluşur ve o request sonlanana kadar
aynı nesne kullanılır. Request bazında stateless nesne kullanılması
istenen durumlarda Scoped bağımlılıkları oluşturabiliriz.

**-- Singleton:** ASP.NET Core uygulaması başlatıldığında register
edilen nesneye ait sadece bir tane instance oluşur ve uygulamadaki her
yerden bu referans çağrılır. Uygulama yeniden başlatılana kadar bu nesne
referansı kullanılır, farklı bir nesne referansı ikinci kez
oluşturulmaz. Bu yöntem için de AddSingleton()metodunu kullanıyoruz.

-   **.Net Core'daki Tag Helper nedir?**

.Net Core ile birlikte gelen Tag Helpers (Etiket Yardımcıları), Razor
HTML yardımcıları ile yazılan kodu daha markup diline yakın olarak
yazılmasını ve View'lerin daha okunabilir olmasını sağlar. Dolayısıyla
anlamasını ve geliştirmesini daha kolay hale getirir.

```csharp

public class AddressTagHelperComponent : TagHelperComponent

{

private readonly string \_printableButton =

"<button type='button' class='btn btn-info\'
onclick=\"window.open("

"'https://binged.it/2AXRRYw\')\">" +

"<span class='glyphicon glyphicon-road'
aria-hidden='true'\></span>" +

"</button>";

public override int Order =\> 3;

public override async Task ProcessAsync(TagHelperContext context,

TagHelperOutput output)

{

if (string.Equals(context.TagName, "address",

StringComparison.OrdinalIgnoreCase) &&

output.Attributes.ContainsName("printable"))

{

var content = await output.GetChildContentAsync();

output.Content.SetHtmlContent(

\$"\<div\>{content.GetContent()}\</div\>{\_printableButton}");

}

}

}

 ```

\<address /\> elementi alttaki gibi kullanılabilir olacaktır.

```csharp

\<address printable\>

One Microsoft Way\<br /\>

Redmond, WA 98052-6399\<br /\>

\<abbr title="Phone"\>P:\</abbr\>

425.555.0100

\</address\>

```

 

-   ![](media/image1.png){width="6.333333333333333in"
    height="3.326388888888889in"}**Yazılım Yaşam Döngüsü Nedir?
    (Software Development Lifecycle)**

Bir yazılım projesinin geliştirilmesi, sadece kodlamadan oluşmamaktadır.
Basitçe bir proje geliştirilirken projenin planlama, analiz, tasarım,
üretim ve test aşamaları yer almaktadır ve almalıdır. Bu aşamalar bir
kere gerçekleştirildikten sonra proje tamamlanmayabilir. Bu aşamaların
bir döngü halinde düşünülmesi gerekmektedir. Proje tamamlandıktan sonra
gelecek istekler, hata düzeltmeleri, projeye eklenecek yeni modüller vs
konular için bu süreç devam etmektedir. Bu döngüye yazılım geliştirme
yaşam döngüsü adı verilmektedir.

-   **SOLID nedir? SOLID başlıklarını kısaca açıklayınız.**

**(S)ingle Responsibility Principle(Tek Sorumluluk Prensibi):** Her
method ve class'ın tek bir sorumluluğu olur örnek olarak database
işlemleri yapan bir class içerisinde log'lama işlemlerini yürüten
işlemler konulmamalı yada loglama class'ımız var ise bu class içerisinde
loglama haricinde başka bir şeylerin dahil edilmemesi gerekiyor ve
metod'lardada aynı şekilde switch/case ile yönlendirmemek gerekiyor her
metodun tek bir sorumluluğu olmalıdır.

**(O)pen/Closed Principle(Açık/Kapalı Prensibi):** Değişime kapalı ama
geliştirmeye açık şekilde kodlamanın kurgulanması gerekiyor mesela bugün
log'lamaları xml'de yapıyorsunuz ama bir karar ile loglamanın artık
xml'de değilde database'de yapılması istendi varolan kodlarınızda
değişiklik değil güncelleme yapılması gerekiyor misal olarak xml
log'laması yapan Single Reponsibility kuralına uymuş olan bir class'ınız
var ve bu class ILogger arayüzünden türetilmiş Database loglaması
yapacak class'ımızda bu arayüzden türetilip metod içerikleri ona göre
yazılır böylelik bu değişiklik değil geliştirme olmuş olur. Kısacası
Uygulama gelişime açık, değişime kapalı olmalıdır. Yani yeni eklenen bir
modül için kodda gereksiz if blokları gibi değişiklikler olmamalıdır.
Bunun yerine kalıtım yoluyla sorun çözülmelidir.

**(L)iskov 's Substitution Principle(Liskov'un yerine geçme prensibi):**
Liskov'un yerine geçme prensibi alt sınıflardan oluşturulan nesnelerin
üst sınıfların nesneleriyle yer değiştirdiklerinde aynı davranışı
göstermek zorunda olduklarını söyler. Yani;türetilen sınıflar, türeyen
sınıfların tüm özelliklerini kullanmak zorundadır. Eğer kullanmaz ise
ortaya işlevsiz, dummy kodlar çıkacaktır. Bu durumda üst sınıfta if else
blokları kullanarak tip kontrolü yapmamız gerekebilir ve böylelikle Açık
Kapalı prensibine de ters düşmüş oluruz. Interface Segregation Prinsiple
kısmında interface'le üzerinden bu konu anlatılırken burada abstract
class'lar üzerindeki kullanımdan bahsediliyor.

**(I)nterface Segregation Principle(Arayüz ayrımı prensibi):** Bir
arayüze gereğinden fazla kullanılmayacak özellik eklenmemelidir.
Kullanılabilecek özellikler, metodlar eklenerek kullanılmalıdır.

**(D)ependency Inversion Principle(Bağımlılığın ters çevrilmesi
prensibi):** Bu prensibe göre de bir sınıf diğer bir sınıfa doğrudan
bağımlı olmamalıdır. Aralarındaki bağ soyut bir kavram üzerinden
sağlanmalıdır. Bu soyut kavram interface de olabilir abstract class da
olabilir.

-   **Nesne ve Sınıf farkı nedir?**

```{=html}
<!-- -->
```
-   Sınıf (class) soyut bir veri tipidir. Nesne (object) ise onun
    somutlaşan bir cismidir.

-   İlk önce sınıf tanımlanır ve kullanılmayı bekler, biz o sınıftan bir
    nesne türetirsek artık o sınıf bir anlam taşımaktadır,

-   Sınıflar genelde şahıs, yer ya da bir nesnenin ismini temsil
    ederler,

-   Sınıflar methodları ile nesnelerin davranışlarını, değişkenleri ile
    ise nesnelerin durumlarını temsil ederler.

-   New operatörü ile daha önce oluşturulan sınıftan bir nesne
    yaratılır,

-   Yaratılan nesne içerisine sınıfımızın bize sağladığı kullanım
    alanlarını kullanarak nesnemizi oluşturup kullanmaya başlayabiliriz,

-   Örnek vermek gerekirse, Ağaç bir sınıftır, alt sınıf ise ne ağacı
    olduğunu belirtebilir, mesela elma ağacı örneği verirsek, mevcut
    sınıfın özelliklerinde meyve olan elmanın özelliklerinden tutunda
    ağacın dal sayısına kadar çeşitli parametreler veya ağacın yıllık
    üretim miktarını hesaplayan metotlar olabilir.

```{=html}
<!-- -->
```
-   **Referance ve Value Type nedir?**

**Value Type,** Bilgileri hafızanın stack bölgesinde direk olarak
saklayan nesnelerdir. Null değer alamazlar. Char, Bool örnek
verilebilir. Çoğu yerde Value Type için eş anlamlı olduğundan Primitive
Type'da denmektedir.

**Referance Type,** Bilgileri hafızanın stack bölgesinde tutar yalnız
heap bölgesinde bir referans değeri tutar. Null değer alabilir. String,
Class örnek verilebilir.

-   **Compiler Nedir?**

Compiler (Derleyici), Herhangi bir programlama dilinde yazılmış kaynak
kodlarını, makine koduna çeviren uygulamadır.

-   **Kısa Kısa Bazı Terimlerin Açıklamaları**

**DNU, DNX, DNVM: DNX (.NET Execution Environment),** yeni nesil .NET
uygulamalarının çalışmasını sağlayan runtime bileşenidir. DNVM (.NET
Version Manager), belirli bir DNX versiyonunun bilgisayara kurulması,
güncellenmesi ve düzenlenmesini sağlayan tool'dur. DNU (.NET Utilities),
DNX dosyasında bulunan bir Package Manager kütüphanesidir.

**Lazy Loading: **Bir kod bloğunun, nesnenin ve ya program parçacığının
sadece ihtiyaç duyulduğunda çalıştırılmasıdır.

**Refactoring:** Kodun yeniden gözden geçirilip iyileştirilmesi.

**Serialization:** Bir nesnenin serileştirilerek byte dizisine
çevrilmesidir bu şekilde programlamada kullanacağımız nesnelerin
veritabanında stream olarak saklamamız mümkün olacaktır.

**Deserialization:** Buda serialization işleminin tersidir
serileştirilmiş bir nesnenin tekrar stream'den nesneye dönüştürülme
işlemidir.

**TDD(Test driven development):** Önce test sonra kod.

**Recursive:** Kendi kendini çağıran metodlar için kullandığımız durum.

**DDD:** Domain Driven Development içerisinde katmanlı mimari olarakda
adlandırılabilecek Presentation Layer, Domain, Layer v.b. layer'ları
kapsayan, refactoring, clean code, repository gibi olayları geliştirmede
ve proje bütününde kullanmayı prensip haline getirmeye çalışan bir
design pattern'dir.

**Monkey Test:** oraya buraya rasgele tıklayıp, değer girip ekran
sapıtıyor mu diye bakmak.

**e2e:(End Two End):** uçtan uca test.

**Overloading: **Overloading yani aşırı yükleme, metot isimlerinin aynı
fakat aldığı parametrelerin tiplerinin ya da sayılarının farklı olduğu
durumlara overloading denir.

**Auto Detect Changes:** Entity Framework içinde performansını artıran
bir mekanizmadır.

**DbSet:** Code First'de veritabanında tablonun tanımlanmasını
sağlayan property'dir.

**DbContext: **EntityFramework için tablolarımıza karşılık gelen DbSet
türündeki proplarımızı tanımlayabildiğimiz, map işlemleri yapabildiğimiz
ve çeşitli veritabanı konfigürasyonları yapabildiğimiz sınıftır.

**API: **Herhangi bir uygulamanın belli işlevlerini diğer
uygulamalarında kullanabilmesi için oluşturulmuş bir modüldür.

**TFS Build and Release Management: **TFS'in içinde bulunan projelerin
test ve sürüm yönetimini yapmamızı sağlayan tool'larıdır.

**Scrum: **Çevik yazılım geliştirme prensiplerini hayata geçiren
yazılımcılardan oluşan küçük guruplara verilen isimdir.

**Agile:** Dünya üzerinde kabul edilen yöntemler arasında en hızlı ve
güvenli proje geliştirme yaklaşımıdır.

**SQL Always On: **Uygulamaların yüksek erişilebilir olması ve sistemde
oluşacak bir hata sonucu sistemin çalışmasının minimum seviyede
aksamasının sağlayan bir SQL teknolojisidir.

**SQL Replication: **Kaynak veri tabanının aynısı, sürekli yenilerek,
başka bilgisayarlarda da tutulma teknolojisidir.

**Performance Tuning: **SQL performans yönetimi teknolojisidir.

**PolyBase: **Yapılandırılmış ve yapılandırılmamış verilerinizi T-SQL'in
basitliğiyle sorgulamanıza olanak tanıyan teknolojidir.

**QueryStore:** SQL Server'de plan değişikliklerinden dolayı yaşanılan
performans problemleri için geliştirilmiş bir teknolojidir.

**Power BI: **Microsoft'un ürettiği bir iş zekası çözümüdür. Görselliği
güçlü, interaktif raporlar-dashboardlar tasarlamamız için üretilmiştir.

**MicroStrategy: **Bir iş zekası şirketidir.

**DataZen:** Raporlama servisidir.

**2FA:** Two Factor Authentication'ın kısaltması olan bu yapı ile üye
girişlerinde güvenliği arttırması amacıyla genellikle mobil uygulamamız
üzerinden push notificaiton yada sms ile gönderilen şifrenin sisteme
girilmesiyle giriş işleminin sağlanabildiği yapıdır.

**ETL: **Extract-Transform-Load, kullanılacak verinin dış kaynaklardan
çıkarılması, verinin iş süreçlerine göre temizlenmesi, birleştirilmesi,
dönüştürülmesi ve yüklenmesi sürecidir.

**SSRS: **SQL Server Reporting Service, adından da anlaşılacağı gibi
raporlama servisidir.

**SSIS: **Microsoft, SQL Server Reporting Services uygulamasını
oluşturarak bir çok raporlamı işlemini kolayca yapabilmeye olanak tanır
durumdadır.

**CMS:** Content Management System, içerik yönetimi sistemlerine verilen
nelen isimdir.

**CRM: **Customer Relationship Management yani Müşteri İlişkileri
Yönetimini; müşteriyi tanımak, müşteri ihtiyacını anlamak, ona uygun
hizmetler ve ürünler geliştirmek ve bu bilginin organizasyon içinde
paylaşılması olarak tanımlanır.

**ERP: **Enterprise Resource Planning yani Kurumsal Kaynak Planlama;
yazılımları, bir işletmenin, satıştan muhasebeye, üretimden insan
kaynaklarına, envanterden CRM'e, aklımıza gelen tüm fonksiyonlarını
kapsayan entegre bilgi sistemleridir.

**Sharepoint: **Büyük ölçekli şirketlerde şirket içerisindeki farklı
farklı depertmanlardaki elemanların birbirleri ile çok rahat bir şekilde
iletişime geçebilmeşerini sağlayan bir yapıdır.

**Sharepoint Farm: **SharePoint sitelerini yayımlayan WSS (Windows
SharePoint Services) sunucular topluluğudur.

**Sharepoint WebPart: **WebPart Portal uygulamalarının yapı taşları ve
içeriğin saklandığı bölümdür.

**XSLT: **Extensible Stylesheet Language Transformations yani
Genişletilebilir Biçimlendirme Dili Dönüşümleri XML tabanlı, XML
dokümanlarını dönüştürmek için kullanılan bir dildir. Orijinal dokümanı
değiştirmeden, yeni bir doküman oluşturmaya olanak sağlar.

**PowerShell: **Microsoft tarafından Windows komut satırı cmd.exe ve
Windows Script Host'a alternatif olarak geliştirilen yeni nesil bir
komut satırı uygulamasıdır.

**Active Directory:** Microsoft ağlarında kullanılan dizin hizmetidir.
Veritabanı, kullanıcılar, bilgisayarlar, mekanlar, yazıcılar gibi
organizasyonun tüm bilgilerini saklar.

**Exchange: ** Microsoft tarafından üretilen bir haberleşme yazılımıdır.

**IIS: **Internet Information Services, Web sayfalarının yayınlanmasını
ve web uygulamalarının çalışmasını sağlayan, istemcilerden HTTP ve FTP
üzerinden gelen talepleri Microsoft Windows sunucu tabanlı işletim
sistemlerinde karşılayan birimdir.

**Application Pool:** Aynı sunucuda bulunan farklı web uygulamalarının
birbirinden farklı havuzlarda tutulmasını yani birbirlerinden izole
edilmesini sağlayan kavramdır.

**SSL: **Secure Sockets Layer, server ile alıcı iletişimi esnasında
verilerin şifrelenerek gönderilmesini sağlayan katmandır.

**FTP:** File Transfer Protocol, bir bilgisayardan bir başka bilgisayar
yada server arasında bağlantı kurma ve dosya paylaşım protokolüdür.

**Real Time Communication:** Real Time Communication eş zamanlı iletişim
kurmak için bir standarttır.

**Heroku: **Bir bulut bilişim (cloud computing) uygulama altyapısı
servis sağlayıcısıdır.

**AJAX**: Asynchronous JavaScript and XML, tüm sayfayı kullanıcıya
tekrar yükletmeden ekrana getiren veya servera gönderen bir çok
programlama dili ile uyumlu çalışan bir tekniktir.

**jQuery: **HTML dokümanların yönetiminde, animasyonların
oluşturulmasında, etkileşimli Web sayfaların hazırlanmasında kullanılan
Javascript kütüphanesidir.

**Angular JS: **Front-end gelirştirmede kullanılan bir Javascript
kütüphanesidir.

**Backbone: **Front-end gelirştirmede kullanılan bir Javascript
kütüphanesidir.

**Node JS: ** Javascript motoru üzerinde çalışan, Event-driven,
nonblocking I/O modeli kullanan, ölçeklenebilir uygulamalar geliştirmek
için dizayn edilmiş bir platformdur.

**Knockout: **Front-end gelirştirmede kullanılan bir
Javascript kütüphanesidir.

**Ember JS: **Front-end gelirştirmede kullanılan bir Javascript
kütüphanesidir.

**Ionic: **Hybrid mobil uygulamalar geliştirmek için Web geliştiricilere
sunulmuş bir front-end framework'üdür.

**Cordova: ** Web tabanlı mobil uygulamalar yazmanızı sağlayan bir
uygulama geliştirme framework'üdür.

**Bootstarp: **Açık kaynak kodlu, ücretsiz bir CSS framework'üdür.

**SubQuery: **SQL'de sorgu içerisine sorgu yazmaktır.

-   **C#'da Exception Handling nasıl uygulanır?**

-   

Exception handling, C# 'da dört anahtar kelime kullanılarak yapılır:

-   **try** : Bir istisnanın kontrol edileceği bir kod bloğu içerir.

-   **catch** : Özel durum işleyicisi yardımıyla bir istisnayı yakalayan
    > bir programdır.

-   **finally**: Bir istisnanın yakalanıp yakalanmadığına bakılmaksızın
    > çalıştırılmak üzere yazılmış bir kod bloğudur.

-   **throw** : Bir sorun oluştuğunda bir istisna atar.

```{=html}
<!-- -->
```
-   **C#'da Access Modifierler nedir?**

Erişim belirleyiciler (access modifiers), koda dışardan yapılmak istenen
müdahalenin sınırlarını belirlemek amacıyla kullanılan anahtar
ifadelerdir.

C# programlama dilinde tanımlanan erişim belirleyiciler:

-   Private: Bir değerin private olarak belirtilmesi, tanımlanan
    değişkene sadece kendi class'ı içinden ulaşılabileceği anlamına
    gelmektedir. Kesinlikle değiştirilmemesi gereken kodlarda
    kullanılmaktadır.

-   Public: Bir değerin public olarak tanımlanması, kod içinde herhangi
    bir yerden erişilebilir durumda olmasını sağlar.\
    Public erişim belirleyici tipinde kısıtlama yoktur.

-   Protected: Kod içinde bir değerin protected olarak tanımlanması;
    bulunduğu class ve o class üzerinden türetilen sınıflar içinden
    erişilebilir olduğunu göstermektedir.\
    Protected; public ve private erişim belirleyicilerinin birleşimi
    olarak görülebilmektedir.

-   Internal: Internal olarak tanımlanan değer; aynı program içerisinden
    erişilebilir fakat farklı program içerisinden erişilemez.\
    Program içerisinde herhangi bir kısıtlaması yoktur.

-   Protected Internal: Protected internal olarak tanımlanmış değer,
    tanımlandığı class ve tanımlanan class içerisinden türetilen
    sınıfların içinden erişilebilir durumdadır.Bu soru, C# mülakat
    soruları listesinde en çok sorulan sorulardan biridir.
