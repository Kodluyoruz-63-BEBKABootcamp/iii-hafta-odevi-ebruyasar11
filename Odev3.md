## **Ödev 3**
### **.Net kodu nedir ve nasıl derlenir?**
NET platformu, Microsoft tarafından geliştirilmiş ve platformdan bağımsız bir şekilde
uygulama geliştirilmesini sağlayan bir ortamdır. Sağladığı çoklu dil desteği sayesinde
programcıların tek bir dile bağımlı kalmadan (hatta farklı dilleri bir arada kullanmasını
sağlayarak) değişik tipte uygulamalar geliştirmelerine olanak sağlar. Masaüstü (Windows, konsol), web, mobil, web servisi, windows servisi, remoting söz konusu uygulama
çeşitlerinden bazılarıdır.

CIL(Ortak Ara Dil) herhangi bir platform-özel direktif setini yerine geçmiştir. Seçilen .Net tabanlı dilin hangisi olduğundan bağımsız, ilgili derleyici CIL direktifleri üretir. C# derleyicisi ile kaynak kod dosyası derlendiğinde CIL direktifleri, manifest ve sınıfların her ayrıntısını tanımlayan metadata bilgisi içeren single-file bir .exe assembly elde edilir.  .NET assembly’leri platforma
özel kod yerine CIL içerdiğinden dolayı kullanılmadan önce makine koduna
derlenmelidirler. CIL’i uygulamanın çalıştığı makine için anlamlı talimatlara dönüştüren
derleyiciye **just-in-time compiler** (tam zamanında derleyici) adı verilir.  .NET çalışma zamanı ortamı, her biri üzerinde çalıştığı
işletim sistemi için optimize edilmiş, her CPU için bir JIT derleyicisi kullanır ve bu
optimizasyonu otomatik yapar.

### **Roslyn compiler nedir?**
.NET Derleyici Platformunun (Roslyn) temel görevi; C# ve Visual Basic derleyicilerini açmak ve araçların ve geliştiricilerin, derleyicilerin programlar hakkında sahip oldukları zengin bilgileri paylaşmalarına izin vermektir. Kod analiz araçları, kod kalitesini iyileştirir ve kod oluşturucular uygulama oluşturmaya yardımcı olur. Araçlar daha akıllı hale geldikçe, yalnızca derleyicilerin sahip olduğu derin kod bilgilerine giderek daha fazla erişmeye ihtiyaç duyarlar. Opak çevirmenler (kaynak kodu giriş ve nesne kodu çıkışı) olmak yerine, Roslyn derleyicileri araçlarınızda ve uygulamalarınızda kodla ilgili görevler için kullanabileceğiniz API'ler sunar.

### **Restful servisler nasıl çalışır? Alternatifleri nelerdir?**
REST(Representational State Transfer), servis yönelimli mimari üzerine oluşturulan yazılımlarda kullanılan bir veri transfer yöntemidir. HTTP üzerinde çalışır ve diğer alternatiflere göre daha basittir, minimum içerikle veri alıp gönderdiği için de daha hızlıdır. İstemci ve sunucu arasında XML veya JSON verilerini taşıyarak uygulamaların haberleşmesini sağlar. REST standartlarına uygun yazılan web servislerine Restful servisler denir.

Alternatifleri:
- GraphQL
- Falcor
- gRPC
- JSON-Pure
- oData

[Kaynak](https://leapgraph.com/rest-api-alternatives)

### **Extension method nedir? Nasıl yazılır?**
Extension metod, yeni türetilmiş türler oluşturma ihtiyacını ortadan yöntemler ekleyerek mevcut türlerin işlevselliğini genişletmek için kullanılan bir yöntemdir. Extension metodla çalışmak için mevcut sınıfların alt sınıflarını oluşturmak, mevcut sınıfları yeniden derlemek veya değiştirmek gerekmez. Extension metodlar kodun okunabilirliğini geliştirirken aynı zamanda mevcut türlerin işlevselliğinin genişletilmesine olanak tanır.

Extension metodun tanımlandığı sınıf 'static class' olmalı ve metodun çağrılması istenilen parametresinin önünde 'this' anahtar kelimesi olmalıdır. Örnek aşağıdaki kodda mevcuttur.

```
public static class StringExtensions
{
    public static bool IsNumeric(this string str)
    {
        double output;
        return double.TryParse(str, out output);
    }
}
static void Main(string[] args)
{
    string str = "100";

    if (str.IsNumeric())
        Console.WriteLine("The string object named str contains numeric value.");
    Console.Read();
}
```
### **MVC'nin alternatifleri nelerdir?**
- HMVC(Hierarchical Model-View-Controller)
- MVVM(Model-View-ViewModel)
- MVP(Model View Presenter)
- MVA(Model View Adapter)
- PAC(Presentation Abstraction Control)
- RMR(Resource-Method-Representation)
- ADR(Action-Domain-Responder)

[Kaynak](https://blog.ircmaxell.com/2014/11/alternatives-to-mvc.html)

### **Architectural pattern nedir? Neden ihtiyaç duyuyoruz?**
Mimari desen, bir yazılım mimarisinin bazı temel bütünleşik unsurlarını çözen ve tasvir eden bir kavramdır. Bir mimari desen, bir sistemin görüntüsünü taşısa da, bir mimari değildir. Belirli bir bağlamda yazılım mimarisinde yaygın olarak ortaya çıkan bir soruna genel, yeniden kullanılabilir bir çözümdür. Mimari modeller, yazılım tasarım modellerine benzer ancak daha geniş bir kapsama sahiptir. Bilgisayar donanımı performans sınırlamaları, yüksek kullanılabilirlik ve bir iş riskinin en aza indirilmesi gibi yazılım mühendisliğindeki çeşitli sorunları ele alır.

### **ViewData, ViewBag, TempData farkları nelerdir?**
ViewBag, ViewData ve TempData'nın tümü ASP .NET MVC'deki nesnelerdir ve bunlar çeşitli senaryolarda verileri aktarmak için kullanılır.

**ViewBag:**

Verileri Controller'dan View'a aktarmak için dinamik bir nesnedir ve verileri ViewBag nesnesinin bir özelliği olarak iletir.

Controller
```
Public ActionResult Index()  
{  
    ViewBag.Title = "Welcome";  
    return View();  
}  
```
View
```
<h2>@ViewBag.Title</h2> 
```
**ViewData:**

Verilerin Controller'dan View'a key-value çifti biçiminde iletildiği bir dictionary nesnesidir. Veriler karmaşıksa ve null istisnalarını önlemek için null kontrolü sağlamamız gerekiyorsa, verileri View'da okumak için typecasting gereklidir. ViewData'nın kapsamı ViewBag'e benzer ve mevcut istekle sınırlıdır ve ViewData'nın değeri yeniden yönlendirme sırasında boş olacaktır.

Contoller
```
Public ActionResult Index()  
{  
    ViewData["Title"] = "Welcome";  
    return View();  
}  
```
View
```
<h2>@ViewData[“Title”]</h2> 
```
**TempData:**

Verileri aynı veya farklı Controller'daki bir eylemden başka bir eyleme geçirmek için kullanılan bir dictionary nesnesidir. TempData nesnesi genellikle session nesnesinde saklanır.

Contoller
```
Public ActionResult Index()  
{  
    TempData[”Data”] = “I am from Index action”;  
    return View();  
}  

Public string Get()  
{  
    return TempData[”Data”] ;  
}  
```