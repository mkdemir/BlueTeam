# Blue Team: Incident Handler

## İçerik

1. Siber güvenlik ekiplerini ve görevlerini, kuruluş amaçlarını ve ayrımlarını ele alacağız.
2. Blue Team ekibi ve görevlerini, kuruluş amaçlarını ve ayrımlarını ele alacağız.
    * Incident Response, Threat Hunting, Malware Analysis, Threat Intelligence, SOC, Digital Forensic, Network Defense, Software Security ekiplerinin görevlerini, kuruluş prensiplerini ve işleyişlerini ele alacağız.
3. Threat Hunter ekiplerini ve Threat Hunting prensiplerini; Threat Hunting prosedürlerini ve işleyişini ele alarak olası anomalilerde hunting taktikleri ile keşfi ele alacağız.
4. Incident Response ekibini ve IR prensiplerini ele alacağız.
5. Cyber Kill Chain adımlarını ve bu adımları engelleme/tespit etme taktiklerini inceleyeceğiz.
6. Kurumsal Savunma hattı oluşturmayı ve savunma prensiplerini;
    * Defense in Depth'i full spektrum ile ele alarak incelemeyi sağlayacağız.
7. Hunting Lab ortamı dizaynını ve geliştirilmesini;
    * Open Source Host based IDS ve Network based IDS dizaynı, alarm aştırılmasını sağlayacağız
    * SIEM dizayn ve alarm geliştirilmesini sağlayacağız.
    * Saldırı Simülasyonlarıyla testler yapacağız ve analizler tespit edip alarm açtıracağız.
    * Lab ortamının geliştirilmesini sağlayacağız
8. Ve birçok blue team teorik ve pratik konularını ele alacağız.

## Bölüm 1: Understanding the Blue Team Methodology

### ÖZET

Bu eğitimin genelindeki Siber güvenlik sektöründe, özellikle Blue Team alanında sahip olmanız gereken enterprise defense yaklaşımları, prensipleri ve metodolojileri üzerinde duracağız. Blue team alanında ilerlemenin ve başarılı olmanın en önemli anahtarı, bu noktalarda uzmanlaşmak ve bütünü görerek hareket etmek önemlidir.

Kariyeriniz boyunca kullandığınız araçlar ve markalar ne kadar değişse de öğrendiğiniz prensipler ve metodolojiler sayesinde onlara adapte olma ve yeni teknolojileri kavrama açısından o kadar hızlı olacaktır. Burada göreceğiniz öğretiler, çünkü markalar ve araçlar her bir kurumda sürekli değişebilir. Veya farklı bir kuruma geçtiğinizde değişebilir. Bunlara bağlı kalmamanız gerekmektedir. Ve bunun arkasındaki teknolojileri ve enterprise security'de yarattıkları etkileri öğrenmek.

Yeni bir şey öğrenmek, bir puzzle çözmek gibi olur. Çok hızlı adapte olursunuz. Bir daha baktığınızda çok çabuk çözebilirsiniz. Arkasındaki teknolojileri, prensiplerini ve nedenlerini öğrenmek sizi her zaman bir adım öne çıkaracaktır. Karşınıza gelecek sonraki puzzle'da her şeyi nasıl yerli yerine yerleştireceğinizi çok rahat öğreneceksiniz.

### Introduction: Incident Handler

**Incident Handler: Olayın yönetimi ve olayı ele alış, olaya ilk başta kontrol sahibi olup sürdürme ve bu olayı sonuçlandırmaya doğru götürme.**

Bir SOC ekibinde çalışan Tier 3 olarak çalışan threat hunting pozisyonunda çalışan birinin teorik ve yarı pratik bilgilerini edinmiş olacağız. (Yarı pratik: Tamamı siz bir şeyleri aramadıkça kurcalamadıkça tam bir pratiklik elde edemeyeceksiniz).

En iyi eğitmen, insanın kendisi ne kadar araştırır ne kadar kurgular ne kadar pratik bilgiler edinirse o kadar çok kendisi öğrenir.

> Mavi hapı alırsan hikaye biter. Yatağında uyanır ve istediğin şeye inanırsın. Kırmızı hapı alırsan Mucize Ülkesinde kalırsın ve sana tavşan deliğinin ne kadar derin olduğunu gösteririm. Unutma! Sana gerçeği öneriyorum. O kadar. (Morpheus)

### Chapter 1: Cyber Security Teams

Siber güvenlik perspektifinden bakarak blue team metodolojilerini anlamamız gerekiyor. Öğrenme sürecimizde bu metodolojilere odaklanacağız ve onları anlamaya çalışacağız.

### Cyber Security Teams

Siber güvenlikteki alt ekipler.

Bütün teknolojik konuda olduğu gibi siber güvenlikte de kendi içerisinde alt ekiplere ayrılmıştır.

* Bu grupların ne olduğu bilmenin başlıca nedenleri arasında ekip içi görev ayrılığı ilkesi **SOD (separation of duties)**.
  * Uzmanlıklara göre gruplara ayrılmak büyük bir kurum ve kuruluşlarda bilgi güvenliği altyapısının operasyonunu yönetimini kolaylaştırıyor.
  * Bir yetenekle uzmanlaşmış bir insanı işe alımını ve ondan faydalanmayı da daha kolay hale getiriyor.

Renklere göre bir dağılım ve ayrım var.

1. **Yellow Team:** Yazılım çözümlerinin yaratıcılarında oluşan bir ekip (Software coders and Architects "The Builders" olarak geçiyor). Bu ekip aslında yazılım geliştirmek test etmek ve dağıtımdan sorumlular.

    * Bu ekibin genel amacı, temel olarak aslında siber güvenlik ekibi ile ortak çalışan developerlar ve siber güvenlik ekibinin dokunduğu noktalardaki developerları da bu işin içerisinde dahil edebilirsiniz. Bunlar genelde siber güvenlik ekibi için yazılım geliştiren ekiplerden de oluşabilir. Veya diğer yazılım ekiplerine ve siber güvenlik ekibine katkı sağlayan ekiplerde olabilir.

2. **Green Team:** Birincil ekiplerin nasıl etkileşime girdiğini rehberlik eden politika ve frameworkleri formüle eden ekiptir. **"Enhance secuirty and automation with design and code"** kısmına da kendileri el atıyorlar.

3. **Orange Team:** (Facilitate interaction and education) Kolaylaştırma ve eğitimler ile ilgileniyor. Bunlar kurum içerisindeki eğitimler olabilir. Kurum için interaction'lar olabilir. "Security Evanescence" konuları ile de ilgilenebilirler.

    * Not: Türkiye genelinde Information Security ekipleri var. Bu ekipler aslında hem orange team'in el attığı konuları hem de bu kısımda white team'nin el attığı konularına dahil oluyorlar. Bir noktada green team'e de dokunuyorlar. Security'nin politika ve prosedürlerine dokunulması kısmında.

4. **White Team:** (Analysts Compliance Logistics Management) Aslında tüm renklerin birleşimi olan ortada yer alan kısım. Bu ekip aslında yönetimi idaredeki insanlardan oluşuyorlar. Daha çok management ve compliance konularına el atıyorlar.

5. **Red Team:** (Offensive security) En iyi savunma saldırıdır. Red team aslında offensive security ekibinden oluşan bir ekip.

    * Red Team'in "Red Teaming" Red Team olarak vurgulandığı bir kısım var.

    * Red Team, offensive securtiy olarak vurgulanması daha mantıklı ve kendi içerisinde birçok kola ayrılıyor. Ve birçok kolda değerlendiriliyor.

        * Kurumdaki böyle yapıların ve sistemlerin, siber güvenlik perspektifinde testlerinin ve hatta "kontrol denetimlerini" yapan ekip Red Team

        * Bu kontrol denetimleri neyden oluşabilir örneğin, bir business logic ortamındaki transactionların veya tamamen bir depodaki yürütülen işlerin bu ekip tarafından bir kontrol edilip sosyal mühendislik açısından da denetlenmesi gerekir. Bu nedenle aslında "kontrol denetimleri yapan bir ekip" olarak da rol alabilir.

        * Red teaming testlerini gerçekleştirirken elde edilen sonuçların böyle iyileştirilmesi için ekiplere eskalasyonu da sağlarlar (Diğer ekiplerle de çok etkileşimde bulunan bir ekip).

        * Çoğu konuda red team'in personeli siber güvenlik ekibinde bulunan bazı kurumlarda danışmanlıklar aracılığıyla faydalanabiliyorlar.

            * Red Teaming tarzındaki faliyetlerini aslında pentesting faaliyetlerini danışmanlıklardan alıyorlar.

    * Red team denildiğinde, red teaming veya pentesting faaliyetleri içine sıkıştırılırsa bu ekip o zaman işte tamamen hatalı bir sonuca gidiyoruz.

    * Red teaming aslında çoğu konuda olduğu gibi siber güvenlik ekibinde bulunuyor. Bazı kurumlarda danışmanlıklardan faydalanıyorlar nedeni pentesting ve red teaming olarak görmeleri.

        * Red Team sadece application securtiy, red teaming veya vulnerability management'tan oluşmuyor. Aslında bunların hepsinin birleşiminden oluşan bir ekip.

        * Bir testin yapılma amacı ana kuruluşların red teamlerin artta gelen pentesing ve red teaming faaliyetlerinin yapılma amacı aslında kurum envanter ve süreçlerini iyileştirmek.

        * Bir pentest'in sonuçları ne çıkar.

            1. Kurumunuzun sahip olduğu yanlış dizayn edilmiş kontrol mekanizmaları.
            2. Zafiyetli olan sistemler ortaya çıkar.
            3. Zafiyetli olan süreçler ortaya çıkar.
            4. Zafiyetli olan yazılımlar ortaya çıkar.

            * Bunların her birinin takip edilip, iyileştirilmesi gerekiyor.

        * Raporların kurum içinde iyileştirilmesi 6 ay'dan 1 yıla kadar sürebiliyor. Bir değişiklik yapmanız örneğin: sunucularda bulunan bir zafiyetin iyileştirilmesi için pacing yapılması gerektiğinde biri bu pacing hemen yapılamıyor. Neden çünkü business'taki etkisine bakılıyor. Business flow'daki neyi sekteye uğratacak mı ona bakılıyor. Business continuity planning'e bakılıyor(Business tamamen devam ettirilmesi, sürdürülmesi aşamasında nereye etki edebilir. Hangi noktada neyi duraksatabilir) bunlara bakılıyor. Development ekiplerinin Security ACNC konularında eğitimler verilmesi.

6. **Blue Team:** (Defensive security "The Defenders")

    * Kurumunuzdaki yapıların, sistemlerin, süreçlerin önem derecelerini öncellikle ardından erişe bilirlik durumlarına, dışarıya açık mı içeriye açık mı, nasıl erişiliyor, bir IPsec ile mi giriliyor gibi konular bunların hepsini ile ilgilenir ve kritiklik düzeyi, bu hedeflenen bir yapının veya sistemin bir iş sürekliliğini sağlaması konusunda bir noktaya gelirse ne kadar bu sistem offline kalabilir. Ve ne kadar bu süreç durabilir gibisinden durumların hepsini analiz edilerek siber savunma hatlarını oluşturulmasını sağlayan. Bu hatları ve ilgili yapıları, sistemleri ve sürekli monitör ederek kurum savunması sürdüren ekip. Bu nedenle bu ekip bir kurumun sahip olduğu envanteri takip edecek ve olası bir incident durumunda olaya el atacak. Ve gözetleyecek bir SOC ekibinden oluşması gerekiyor.

    * Threat Intelligent Uzmanları: Kurum içi ve dışında elde edilen bilgileri işleyip bu bilgileri belli metriklerle size bulgu verecek veya hatırlatacak bir şekilde bir yapıya ulaşabilirseniz. Ve bu dışarıdan gelecek istihbaratları değerlendirebilecek bir ortam sağladınız anda bunlarla ilgilenen kişilere denir (Bir kurumun maruz kaldığı ve kalacağı veya kalabileceği durumları analiz etmek ve bu durumlara yönelik kurumun bilgilendirilmesini sağlamak, kurumda bir bilgi havuzu oluşturmayı sağlayan uzmanlardan oluşuyor).

    * Threat Hunting: Kurum için envanterlerden planlı olarak belirli özel bir noktayı hedefleyerek

        * örneğin ben bugün ağ topolojisindeki Intrusion Prevention System (IPS)'in heat durumlarına bakacağım. Diyen veya bunları gözlemleyen, işleyen ekip olarak threat hunting uzmanlarından oluşan bir ekip olabiliyor.

        * Bu kişiler aslında anomali keşfine çıkabiliyor kurum içerisinde.

        * SOC ekibinde çalışan insanlar "threat hunting'e" fazla vakit ayıramıyorlar. Çünkü olası zaten belirlenmiş tetiklenen alarmları inceliyorlar. Bu alarmlar haricinde hunt'a çıktıklarında tekrardan bir alarm geleceği için yarım kalabiliyor veya bu şüphelendikleri durum üzerinden yoğunlaşıp inceleyemiyorlar veya sadece bir durum veya özne içerisinde inceleyebiliyorlar.

        * Kurum içerisinde beli bir plan ve prosedüre bağlı olarak belli noktaları devamlı araştırıp eden bu kısımlardaki anonimleri aslında derinlemesine inceleyen uzananlardan oluşuyor.

    * Malware Analysts: Olası bir zararlı yazılım keşfi sonrası incelemeler sağlayıp saldırganların belki de bir kurum hakkındaki hedeflediği bir zero day keşfederek ortaya çıkmasını sağlayan bir malware analiz uzmanlarından oluşuyorlar.

        * Bir zararlı bulaşıp mevcut kullandığı EDR, EPP, anti virüs, XDR ve IPS ürünün keşfedememesi sonrası bu zararlı yazılımı bulduktan sonra IoC'lerini bu araçlara ekleyerek silinmesini sağlar. Ama bu ilgili zararlının analizini tamamıyla bu IoC'sine eklediği kullandığı zararlı yazılımların tamamen ekiplerine bırakır. Ama gelişmiş bir siber güvenlik hattı oluşturan bir kurumda bu tarz bilindik IoC'lerin olmadığı ve doğrudan sizin kurumunuzu hedeflediği gözüken spesifik bir saldırıyı siz analiz etmek zorundasınız.

            * Örnek sizin mail security gapinizi bulup oradan nasıl ilerleyeceğini keşfeden bir saldırgan olabilir.

            * Veya ürettim hattında çalışan bir firma olduğunuzu düşünün sizin içerde çalıştırdığınız bir skada sisteminiz var. Dışarıya tamamen kapalı içeriden bir şekilde bilgi sızıyor. Envanteri hedefleyecek bir zararlı yazılım olabilir bunları zararlı yazılım uzmanları tarafından analiz edilerek ortaya çıkarılabilir.

            * Veya sizi bir apt (Gelişmiş saldırganları nitelendiren bir kısaltmadır) faktöründen koruyacaktır.

    * DFIR Digital Forensic Team (Adli Analiz Uzmanları): Tamamen olası bir durumda incident olduğu bir incident sonucunda belirli makineler veya sistemler compromise oldu bu makinelerin ve envanterlerin adli analizini sağlayacak legal ekiplerle ve bağlı bulunduğunuz regülasyonlar dolayısıyla sorumlu olduğunuz firmalara belirli kanıtları sunabilecek bu envanteri üzerinde adli analizler yapıp raporlandırma sağlayacak. Bu bahsedilen yükümlü olduğumuz bildirim yapmamız gereken kuruluşlara bildirim yaparken vereceğimiz raporları hazırlayacak kişilerden oluşan Adli analiz uzmanlarından oluşuyor.

7. **Purple Team:** Hem read team'in hem de blue team'in bir araya gelmesiyle oluşan. Bu iki ekibi koordineli olarak çalışmasını sağlayan bir ekipten oluşuyor.

    * Hem saldırı hem de savunma hatlarında uzman olmuş insanlardan oluşsa da purple team'in amacı bir kurumdaki hem savunma hatlarının hem de yapılan sistemlerdeki tatbikatların ölçümlenip savunma hatlarının sistemdeki tatbikatlarla ya da yapılan red teaming faaliyetleri ile ne kadar etkileşimde olduğu ve iyileştirilmeye gidildiğini bizi bilgilendiriyor.

### BLUE TEAM'in ALT EKİPLERİN DEĞERLENDİRİLMESİ

İlk olaya el atanlar SOC ekiplerinden uzmanlar oluyor.

* Örnek bir alarm tetiklendi bu alarm yurt dışından bir IP'nin kurumumuzun dış envanterine bağlı olan bir makinemiz var DMZ'de bulunan bu makinenin RDP portu açık olarak unutulmuş. Yurt dışından bir ip bu RDP portuna bağlantı sağlıyor. Bu durumda SOC ekibi ilk olarak bunu karşılıyor.

Ne Yapıyor:

* Yurt dışından, IPSec tünelleri ve farklı etkileşimde olan IP'leri hedeflenmeden farklı IP'lerden gelen bir RDP bağlantısı sonrasında direk alarm üreten bir yapımız olduğunu varsayın (IDS, SIEM veya Gelişmiş Log Yönetim Sisteminde), SOC ekibi el atıyor. SOC ekibi incident handler olarak olaya ilk el atıyor. Bir incident ilk karşılayan ekip oluyor.

* İlk olarak bir kontrol mekanizmasından geçiyor.

* Alarm doğru tetiklendi mi false pozitif mi? (Bir bağlantı olmuş, firewall logunu kontrol ediyor ilgili bağlantı allow almış (false) değil veya teardown değil ya da yarıda kesilmiş bir bağlantıda değil (allow almış)) Tamamen bu bağlantı kurulmuş ve ilgili IP bu bağlantıya geçiyor olarak gözüküyor.

* SOC Ekibi aslında burada 2'ye ayrılan binr ekip olabilir.

1. Incident Response Team: Incident Response ele alan bir Tierless yapıdan oluşan bir SOC ekibi olabilir veya genel anlamda şu anda biraz daha old school olan tiered mekanizmadan oluşan bir ekip olabilir. Bu tier mekanizmadaki ilk ekip SOC analistteki arkadaşlar bu olayı direk eskale ediyorlar eskale ettikten sonra da ilgili tier 2'deki arkadaşlara geliyor. Tier 2'deki arkadaşlar aslında incident response ekibinden oluşan kişilerden oluyor. Bu incident response'daki arkadaşlar

    * ilk olarak olayı bir analiz etmek durumunda identify etmek zorunda

    * Olay'a bakıyorlar cidden doğru bir olay dışarıdan bir IP erişmiş bu IP'nin erişimleri devam ediyor. Bu noktada direk response vermeleri gerekiyor.

    * Response vermeden önce kendi ekiplerindeki sistem ekibindeki arkadaşlarla görünmeliler. İlgili makinedeki port neden açıktı ve bu portun kapatılması gerekiyor mu business etkilenecek mi kapatıldığında bunları kontrol etmek gerek. Business etkilemiyor yanlışlıkla açık unutulmuş bir durum hemen sistem ekipleri göz attıktan sonra ilgili olaydaki makinedeki RDP kapatılıyor. Kapatıldıktan sonra ilgili RDP yapıldıktan sonra o makineye yapıldığı için o makinenin bir containment'ta alınması gerekiyor. Yani bu makinenin izole bir ortama tanışıp incelenmesi gerekiyor.

    * İlgili makinenin izole bir ortama alındığı anda business etkileyecek mi bunu bir soruşturmak gerekiyor. Etkilemediğini göz atarsak artık o makina incelenmesi gerekiyor. Bu makine üzerine baktığımız anda ne yapılmış bu makine üzerinde bir dosya çalıştırılmış bu dosya çalıştırıldıktan sonra birçok makineye doğru bir port taraması gerçekleştirmiş artık incident response ekibi yapılan taramalar doğrultusundaki elindeki alarmları topluyor. O makine ile ilgili ve o makinedeki, containment'a aldığından dolayı o makinede yapılan çalışılan containment’daki bir dosyadaki örnekleri de alınması gerekecek. Artık bu noktada incident response ekibi alanında uzman kişilere gitmesi gerek.

    Özet Aşamalar:

    * Indentify
    * Response
    * Improvement

    Sahip Olunması Gerek Özellikler:

    * Bir EDR üzerindeki veya kurumdaki bir security araçları üzerindeki detection sağlayan security araçları üzerindeki log okumaları veya ilgili bildirimleri alarmları okumalarını çok iyi bir şekilde sağlamaları gerekiyor. Bu bir EDR olabilir NDR olabilir bu gibi araçlardan gelecek veya kendimizin dizayn ettiği SIEM üzerinde dizayn ettiğimiz alarmalar bunların her birini analiz edip iyice bir göz atmaları ve doğrulamaları gerekiyor. SOC ekibinde bu ekip içerisinde var olabilir.

    * Bu ekip bir incident geliştiği anda o incident'ı tanımlamak o incident'ı ilk durumda ele alıp doğru şekilde eskale etmek zorunda.

2. Malware Analysis Team: Zararlı yazılımlar konusunda uzman bir ekipteki arkadaşlardan oluşuyor. Bu analizdeki arkadaşlarımızın öncellikle containment'a aldığımız makinede:

    * EDR yüklü mü diye kontrol ediyoruz. Genelde kurumların çoğunda bir EDR veya uzaktan bir tekrardan terminale bağlanacak ilgili makinede containment'a alacak bir yazılım bulunuyor.

    * İlgili zararlı yazılımın kopyalarını alıyorlar. Bunu kontrollü bir biçimde yapıyorlar. Containment'ı aşmayacak şekilde bunu sağlıyorlar.

    Özet Aşamalar:

    * Identification
    * Detect
    * Analysis

    Tamamen ilgili gelen zararlının IoC'lerini incelenmesi, reverse engineering yapılırken ilgili bulunan noktaların değerlendirilmesi hangi process'lerin çalıştırıldığın bulunması, hangi process'lerin fail process ürettiğinin keşfedilmesi veya hangi register key'leri hedef alarak bu işlemlerin gerçekleştirildiğinin bulunması veya bir malware'ın FIN aşamasındaki hangi noktaları tamamen es geçiyor veya değişikliğe neden oluyor. Bu noktaların bulunması hem ilerideki olaylarda alarmlarımızda güçlendirebiliyor.

3. Digital Forensics Team: Bu ilk aşamada bir makineyi tamamen dokunmadan önce de bu makinenin adli olarak bir snapshot'larının alınması, disk imajlarının, ram imajlarının alınması tamamen gerekiyor. Bunlarında alınması da ilk aşamada digital forensics ekibi sağlaması gerekiyor.

    Olaya geri dönecek olursak:

    * İlk aşamada incident response ekibi olayı buldu bildirdi ve makineyi izole etti containment'a aldı ağda acil olarak hızlı bir şekilde response olarak RDP'yi aslında kapattı bu noktada değerlendirecek olursak ilk aşamada RDP'yi kapattırması gerekiyor muydu veya gerekmiyor muydu?

    * Eğer makindeki RDP'yi kapattırmasaydı, belki saldırganının dışında farklı bir makineye de sıçrayacaktı veya daha sonrasında işte o makinenin sıçradıktan sonra artık sıradaki bir makineye geçmiş olacaktı containment'tan sıyırmış olacaktı aslında o nedenle makinedeki RDP'yi kapattırmak business continuity engellemezse bir sıkıntı yok gibi (Bu makineler genelde sanal ortamlarda çalıştıklarından ilgili portların kapatılması ve işlenmesinde izole alınması da hızlıca gerçekleştiriliyor).

    * Tamamen containment alınmış bir makinede izolasyona alınmış bir makinede

    * Digital Forensics ekibindeki arkadaşlarımızı çağırıp ilgili makinenin sistem ekipleri tarafından bir snapshot’larının alınması, ram imajlarının alınması bunları tamamladıktan sonra malware analizdeki arkadaşlarımızın o dosyayı alıp incelemesi gerekiyor. O dosya üzerinde bir tersine mühendislik yapıp veya sandbox'ta (Bir dosyanın tamamen izole ve takip altında olunan bir sistem altında açılıp incelenmesi ve zararlının yapacağı aksiyonlara göz atma) tanımlanan sanal bir ortamda çalıştırıp analiz yapılabilir. Sandbox'ta da incelenebilir. Bir noktada temel IoC'lerinden faydalanarak zararlı yazılım incelenebilir. Hash'ini alarak ve birçok portalda taratarak gibi işlemlerden geçebilir.

    Özet Aşamalar:

    * Preservation
    * Contain
    * Investigation

    * Elimizde bulunan cihazların adli analiz bakımından incelenmesi için delilerin karartılmadan her hangi bir dedil değişikliğine uğramadan nasıl imajların toplandığı, nasıl ilgili dosyalar alındı, makine nasıl Containment alındı, ilgili süreçler nasıl rapolarlandı bu aşamaların aslında bir şekilde oluşturulması gerekiyor.

4. Network Defence Team: İlgili incident'ımızda belki de RDP'yi kesecek olan ekip belki de ilgili makineyi containment'a alacak ekip aslında network defence ekibinde olabilir.

    Sahip Olunması Gerek Özellikler:

    * Network defence ekibi içince NOC ekibi de bulunabilir. SOC'den ayrı olarak bu ekibin en büyük avantajı, anomali yapmış bir RDP bağlantısı ya da dışarıdaki bir IP'nin external veya internal bir bağlantı oluşturması ve bu DMZ ortamında anormal bir şekilde anormal bir porta giderken oluşturması RDP portuna bu bir şüpe çekebilir bu ekip tarafından yakalanabilir. Bu ekip bu yakaladığı bulgular sonrasında tamamen yok etme aşamasına kadar eradicate sürdürebilir. Ortamını bunları yaparken incident response ekibi ile çalışması gerekiyor.

    Özet Aşamalar:

    * Secure Mitigate
    * Monitor
    * Eradicate

5. Software Security Team: Kendi içerisinde bir güvenlik yazılımı geliştiren bir ekip olabilir. Blue team içerisinde ya da blue team'in kendi yazılımlarını geliştirdiği incident response'da bulunan veya malware analiz team'de bulunan bir arkadaşta olabilir. Bu ekip aslında blue team'in ihtiyaç duyduğu araçları, platformların, tamamen geliştirilmesi ve geliştirilen bu cihazların tamamen kurum içerisinde politika ve prosedürlere yönelik artık uygulanmasını sağlayan bir ekip olabilir. Bunların ilk testlerini yapıp product aşamasına alıp ekipler ile kurgulamaya sürükleyen ardından bir politika ve prosedür dizayn edip hangi durumlarda hangi noktalarda hangi prosedürler izlenerek bu aracın kullanılmasını sağlayacak ekip olabilir. Bu ekip devamlı bir development geliştirerek ilgili süreçlerimizin düzenlememesini ve ihtiyaç duyulan yazılımların kurum içerisinde geliştirilmesini sağlayabilir.

    Özet Aşamalar:

    * Recover
    * Developement
    * Control

6. Cyber Threat Intelligence Team:

    * Malware Analizdeki arkadaşlar, belirli IoC bulmuşlardı

    * Network Team'deki arkadaşlar, bu makineni IP'sini tespit etmişlerdi.

    * Incident Response'daki arkadaşlar, ilgili IP bulup engellemişti.

    * Topladığımız bütün bu IoC'lerin Threat Intelligence'daki arkadaşlarımıza bilgilendiriyoruz aslında biz böyle kaynaklar bulduk bize doğru bir incident geliştirdiler. Bu topladığımız verileri Intelligence’daki arkadaşlarımıza verdiğimizde onların radarına neden takılmadığını bulmaya çalışıyoruz.

    * Mesela bir threat intelligence listelerinden beslenen bir firewall olduğunu düşünün firewall engel kuralımızın acaba neden bu IP'ler bulunmadı veya bu spesifik olarak ayağa kaldırılmış bir makine mi bizi hedefledi gibisinden düşünebilirsiniz. Threat intelligence ekibimizi ilgili konularda bilgilendirip onlardan bir tehdit istihbaratı konusunda araştırma yapmalarını ve belki danışman firmalar aracılığı ile onlara danışarak bulgu toplamalarını rica ediyoruz. Bu konuda kendileri el atabiliyorlar.

    Özet Aşamalar:

    * Managing

    * Supporting

    * Research

    * Bütün ekipler aslında bir araya gelerek "software security team'de" gelebilir. Blue Team içerisinde olan. Burada neyi kaçırdığımızı nasıl iyileştirebileceğimizi neler yapabileceğimizi değerlendireceğimiz. Bir aslında bir ekip "tabletop" oluşturulabilir.

    * Bu tabletop'larda aslında ekibin bir araya gelerek neleri geliştirebileceğimizi, neleri iyileştirebileceğimizi düşünebilecekleri bir ortam olabilir. Bu ortamda değerlendirerek her ekibe söz hakkı vererek kendi görüşlerini ortaya koymasını neden böyle bir incident yaşandığının değerlendirilmesi yapılabilir. Ve mesela bu ekibin toplanmasından önce de mutlaka bir "lesson learning" toplantısı oluyor genelde "lesson learning" toplantılar aslında bir incident'ın gelişmesinden sonra yapılan toplantılar. Neler öğrendik bu konudan bu toplantı sonucunda edindiğimiz bilgileri tabletop'ta inceleyebiliriz daha sonrasında.

    * MISP: Threat Intelligence verilerini toplayan ve bunları işleyen bir platform

### SOC Simplified SOC Tiers

SOC normalde global'de çeşitli kuruluşlarda tier mekanizması ile çalışan bir yapıya sahip bunun belirli artıları olduğu gibi eksileri de var.

SOC (Security Operations Center), Türkiye’deki diğer çevirisi SOME olarak geçiyor. Siber olaylara müdahale ekibi

SOC temel görevleri vardır. Bunların başında aslında tamamıyla şey geçiyor. Bir olaydaki kurumdaki incidentlara ilk müdahalede bulunmak incidentların oluşmasını engellemek, tespit etmek ve oluşan bu incident'ların tamamen kontrol altında bir şeklide eskale etmek ya da çözümlemek.

Göz attığımızda 3 basamaktan oluştuğunu görüyoruz. SOC'nin aslında 4 basamaktan oluşuyor. Son basamak tier 4 olarak dediğimiz SOC Team Lead veya SOC Manager olarak kabul edebiliriz.

Tier'lı olarak incelediğimizde SOC'de genelde, globalde ve Türkiye'de birçok kurumda tier mekanizması var.

1. Tier 1 amacı yani SOC analistlerinin amacı

    * Tamamen monitoring sağlama

    * Açık olan ticket'ları çözümleme (closes false positives) yani false pozitif olayları kapatma

    * Giriş seviyesi investigation ve mitigation'ları sağlama

    * Tier 1 analistlerinin görevi aslında genel olarak SOC'lerde temeli oluşturan bazı araçlar var.

        * SIEM

        * Log Management, Genelde SIEM'ler log management'a da kabul ediyor ama çoğu kurumda da şey yok tamamen SIEM ürünü yok log management ve open source araçlar ile bunu sağlamaya çalışıyorlar. Bu doğrultuda şey var Graylog  veya kibana aracılığıyla logları alıp bunları bir platforma yansıtıyorlar. Kibanaya veya Graylog 'a gibi ardından belirli manuel olarak da IDS’e yani HIDS'e ve NIDS'e kurallar giriliyor. Sonra bu kurallar tetiklendiği anda Graylog ekranında veya kibana ekranında görüntülenebiliyor. Analiste dağıtılırken de the hive kullanılıyor. Hive'da atanan olaylar analistlere dağıtılıyor. Ve analistler bunları çözümlemeyi sağlıyorlar.

        * Tier 1 incelediğimizde:

            * Monitoring kavramı şu oluşacak incident'ların SIEM ekranında gözlemlenen alertlerin diğer tool'ların tetiklediği alertlerin bunların göz atılıp incelenmesi veya içeride dizayn edilmiş dashboardlar varsa bu dashboardların nazaran dizayn edilen belirli base line'ların artması bir anda kontrol ediyorsunuz mesela belirli IP'lerde portlardan gelen hataları kontrol ediyorsunuz. Bunlar peak yapıp belirli düzeyde arttığı zaman yani bir base line'laştığı zaman o zaman analist bunlarında monitor edip aktiviteye geçebiliyorlar. Araştırabiliyor kontrol edebiliyor. Bunları inceleniyor. Ya da belirli RDP connection'ları onun dışında belirli kerberos ticket'ları bunların artışları veya tekrarlanışları ya da fail durumlarında belirli dashboardlar sayesinde bunları gözlemleyip kontrol edebiliyorlar burada önemli nokta analistin göz atıp tamamıyla dedicated bir şekilde el atması için bir konuyu alarm olması gerekiyor.

            * Dashboard kullanılması ile KPI ölçeklendirilmesi çıkarken bu SOC'de bu ay kaç tane olay kapatıldı kaç tane olaya el atıldı ne kadar case ortaya çıktı bunları incelerken de bir metrikleri bize verecektir. (Burada önemli olan nokta şu false pozitiften ayıklanmış bir alarm mekanizması olmasının olması çok önemli ne kadar çok false pozitif almak analist için durumun o kadar ciddiyetinin kaybetmesine neden oluyor.)

        Özet:

        * Monitoring

        * Open tickets, closes false positives

        * Basic investigation and mitigation

    Dezavantajları:

    * Sürekli kendilerini monitoring ekibi olarak görebiliyor.

2. Tier 2

    * Amacı aslında olayları derinlemesine kontrol etmek T1 tarafından eskale edilen olayların incelemek gerektiğinde bazen T2 katmanındaki kişiler ilgili alarmın düzeltmeler yapabiliyor. Alarmları doğrulanabilir veya false pozitif olayların düzeltilmesinde sağlayabilir veya gelişmiş incident'ların ilk başlangıç noktasına da el atabilir. Incident responder olarak geçen kişiler T2'de oluşabilir.

    Özet:

    * Deep investigations/CSIRT

    * Mitigation/recommends changes

3. Tier 3

    * Aslında bir kurumdaki blue team'de yer alan kişi ve uzmanların tier 3'te oluştuğunu gözlemiyoruz.

    * Özet:

    * Advanced Investigations/CSIRT

    * Prevention

    * Threat hunting

    * Forensics

    * Counter-Intelligence (Threat Intelligence'lara yönelik bir uzman olmalı)

    * Malware reverser

### Evolution of SOC

Tier'lı mekanizmanın zaman içerisinde nasıl bir yol aldığını nasıl SOC'yi biçimlendirdiğini inceleyeceğiz.

1. NOC (Network Operations Center) (Before 1995) (Availbility Moitoring):

    * Government, Military

    * Network alerts

    * Devletler ve askeri düzeydeki kurumlardan SOC'ler bu kadar yaygın dı

    * İlgilenilen Konular:

        * Network device management

        * Malicious code analysis

2. NSOC/SOC V1 (Internal SOC) (İlk nesil SOC'lar oluşuyor.) (1996-2000)

    * Goverment, Military, Large Enterprise Banks

    * Gelişmeler:

        * Antivirus

        * IDS

        * Firewall (Black list and white list)

    * Devletler, askeri düzey ve büyük işletmeler ve bankalar.

    * İlgilenilen Konular:

        * Virus Alert (Antivirus)

        * Intrusion detection and response (NIDS) (Reactive Monitoring)

3. SOC V2 (SOC) (2001-2006)

    * Goverment, Military, Large Enterprises Banks

    * Gelişmeler:

        * Vulnerability Management

        * Dynamic Packet Filtering

        * Antispam

        * IPS

    * Devletler, askeri düzey ve büyük işletmeler ve bankalar.

    * İlgilenilen Konular:

        * Compliance

        * Incident Response

    * SOC'den bağımsız bağımsız response elde etme araçlar sayesinde biraz daha güçleniyor.

4. SOC V3 (SOC/MSS) (2007-2013) (Proactive Monitoring)

    * Goverment, Military, Large and Medium Enterprises Banks, Pharma

    * Gelişmeler:

        * DLP

        * Advanced Persistent Threats (APT)

        * SIEM

        * SecOps

    * Devletler, askeri düzey ve büyük ve orta boyuttaki işletmeler, bankalar ve ilaç şirketleri (skada sistemlerinin olduğu kurumlar. Yani üretimin durmamamsı gereken iş akışının bir sekteye uğramaması gereken yerlerin dahil olduğunu görüyoruz).

    * İlgilenilen Konular:

        * Regulatory compliance

        * Log monitoring

        * Malware analysis

5. Next Gen SOC (Hybrid SOC) (2013-2015):

    * Goverment, Military, Banks, All Industries

    * Gelişmeler:

        * CASB

        * Cloud Security

        * UEBA

        * TIP

        * Sandboxing

        * CERT

        * BYOD

    * Devletler, askeri düzey, bankalar ve tüm endüstriler

    * Gelişmeler:

        * Reverse Engineering

        * AL/ML models

        * Threat Intelligence

6. Cyberdefense Center/CFC/CSOC (NDR) (Proctive Montitoring with Automation) (2015-2020):

    * All Industries Internet of Things/IOMT Smart Homes/Vehicles

    * Gelişmeler:

        * Big Data (Data Lake)

        * CWPP/CSPM

        * SOAR

        * Deception (Honeypot veya tespit etmeye yönelik bu aldatma teknolojilerinin devreye girmesi saldırganı aldatıp onu tepki normal bir sistemdeki gibi hareket etmesini olanak sağlayıp yapacağı hareketler sonrasında onu mesela yakalamayı sağlayan teknolojiler).

        * EDR

        * Cloud-Native SIEM

    * Bütün endüstriler, IOT/IOMT, Smart Homes/Vehicles

    * Gelişmeler:

        * Threat hunting

        * Automation

        * Orchestraion

        * Playbooks

        * Analytics

        * External risk scoring (Dışarıdan bir saldırganın bize nasıl ulaşabileceği hakkında bir skorlamaya gidiyoruz).

### SOC Tierless

SOC Engineer'lar oluyor. T2'deki görevleri ve yetkinliklere sahip oluyor. Sürekli bu takıma eğitimler, sertifikasyonlar ve purple team pratikleriyle geliştirdiğinizde bir zaman sonra T1 da başlayan biri T2'deki yetkinliklere sahip olacaktır.

Bu arkadaşlara verilen imkanlar:

1. EDR'da aksiyon alabiliyor.

2. Firewall'da aksiyon alabiliyor.

3. İçeride IPS'de bir şeyleri inceleyip göz atabiliyor.

SOC'nin ilk aşamasında bulunan insanlar tamamen T1 ve T2 düzeyindeki insanlardan oluşuyor.

### Monitoring

Monitoring dediğimiz anda aslında birçok kaynaktan ve birçok noktadan alınan sistemleri data'ları görebiliriz. Bu data'ların her birinin aslında tamamen monitor edilmesi göz atılması belli ölçeklere bağlı bir risk management sonucunda ilgili data kaynağının önemi yani ne kadar riskli müşteri data'sı var mı içersinide bir sağlık verisi var mı informaiton security ekibi ile konuşulup bu data'nın hangi risk matrisinde olduğu öğrenilmeli. İlgili data'nın kritiklik düzeyi öğrenilmeli olası bir durumda sızıldığında risk management'a göre nasıl bir kuruma hasar verebilir. Bunların tamamen ölçeklendirilip göz atılması gerekiyor.

* Örneğin çeşitli ticketing mekanizmalarının monitoring'i burada mesela ticketing mekanizmalarını monitör ederken ve gözlemlerken işte tamamen mesela SOC'ye gönderilen bir USB izin alarmı veya USB izni ne kadar kritik önemli ne kadar sürede çözümlenmesi gerekiyor. SLA nedir

Tetik İnceleme

#### Log Collection

İçeride bulundurduğumuz güvenlik araçlarının sistemlerin windows event loglarının, linux audit loglarının, kendi geliştirdiğimiz application loglarının yine faydanılan ama security dışında hizmet veren uygulamalarının loglarının toolarının loglarının bunların bir şekilde alınıp SIEM üzerinde toparlanmasını gerekiyor. Bunların göz atılıp monitoring edilmesi gerekiyor.

* Bunlar nasıl monitoring ediliyor?

* Gelen log akışları, log kesintilerine göre mesela bir kaynaktan 1 saat log alınamıyor.

* Bir kaynaktan log alımı şu kadar azaldı normalde baseline'ı 1 dk 10 k iken log events iken şu an 1 k event'e düştü

Monitoring Edilmesinde 2 Tane Araç Kullanabilirsiniz:

* Bir dashboard sistemleri kullanarak baseline görebilir artış, inişler ve peak'leri inceleyebilirsiniz.

* Alarmlar kurarak monitoring noktasında bunları devamlı kontrol edebilirsiniz.

#### Reporting

Monitoring ettiğiniz sistemleri gün sonu SOC analistlerinin gün sonu raporları veya inceleme logları veya raporlama mekanizmaları sağlayan içeride araçlar varsa onların da loglarının toplanıp monitor edilmesi gerekiyor.

#### Research & Development

Hangi sistemleri alabiliriz hangi sistemleri monitoring için değerlendirebiliriz.

* Örnek windows event loglarını alıyoruz. Ama syslog yükleyip ekstra şeyi mi daha çok komut satır loglarını mı daha çok almalıyız. Ya da içeriye bir HIDS yükleyip ilgili SIEM'in tespit etmediği noktalar da mı daha fazla loglamalar sağlamalıyız. SIEM'imizde agent yoksa

#### Threat Intelligence ()

Tamamıyla Threat Intelligence kaynaklarından gelen veri akışlarının içeride bir nevi Correlation kısmındaki gibi korele ederek ilgili alarmlarımızdaki bir port taraması oldu dışarıdan bu port taramasındaki threat intelligence ip'leri arasında bulunuyorsa o zaman farklı bir alarm üret veya kritiklik düzeyini değiştir gibi aksiyonlar korelasyonlar üretebiliriz.

#### Knowlege Base

#### Ticketing

#### SIEM

#### Aggregation Correlation

### Log Collections (Logların Toplanması)

Loglar nelere göre ayrıştırılır.

* Bir enterprise yapıda birçok kaynak ve birçok nokta kullanılıyor.

  * Bunlar Neler Olabilir?

    * Web server, İçerde tamamen bir serverların belki dışarıya açık belki sadece içeride sadece kullanılan web serverların bunların loglarının alınması gerekiyor.

      * Bunlar Ne Olabilir?

        * Application uygulamasına girilen input değerlerinin authentication veya authentication aşamasında alınacak loglar etkili olabilir. Belirli kullanıcıların giriş yaptığı sistem varsa loglar alınabilir veya kurumun tamamen doğrudan açık ama işte kurum içerisindekş çalışanların direk erişebildiği bir servis varsa onların application'daki tamamen girdikleri değerlerin loglar alınabilir veya trafik logları alınabilir.

        * End User Devices Log, 2 veya 3 çeşitle alınabiliyor.

        * Bir agent ile alınabiliyor. Bunlar neler olabilir HIDS olabilir (Örnek: Wazuh, ossec).

        * Anti virüs programları, EPP veya EDR kullanılan agent'ler gibi kritik loglar.

        * Windows ise VSS gibi araçlar varsa

    * Wireless, kurum içinde kullanılan guest ağları veya kurum içinde kullanılan wireless ağlarında bağlandığı.

    * Network Devices, network üzerinde yeni bir cihaz network'e katıldı veya yeni bir ağ oluşturuldu veya ağdaki yeni bir cihaz oluşturuldu IP üzerindeki ağdaki bir IP'nin bloğu değiştirildi veya yeni bir blok eklendi.

    * Streaming Log Data, içeride bir stream servisi varsa bunun loglarının toplanması gerekiyor.

    * Servers log, server trafik logları ve server'ın kendi üzerinde OS'un audit loglarını linux ise linux audit loglarını windows ise tamamen windows event loglarının server'ların bağlı olduğu AD yapıları alınmalı bunlar ayrı ayrı tulup korele edilmeli.

    * APIs and Cloud Services, Cloud servislerinde oluşan uyarılarda SIEM ürününüz içerisine alabilirsiniz.

    * Email Filtering, email servis logları, email gateway varsa logları, email security logları şüpheli mailleri fark eden araçların loglarıda olabilir. Bazen mail gruplarının leak olması, mail adreslerinin leak olması.

    * File Logs, sunucuda ağ üzerinde veya AD üzerinde bazı dosyalar üzerinde yapılan değişikliklerin (FIM) loglarının alınması belirli dosyalarının kullanılması onlarından loglarının toplanması.

    * Security Devices, EDR, MDR, EPP, anti virüs var mı?

    * Anti Malware

    * Indentity, EAM varsa  

* Bu loglar genelde local bir log collection veya forwarding araçlarına iletiliyor.

* Bu araçlar genelde, syslog, API Calls, Files/Rsync VMI Other protocols bunlar local log collection veya forwarding araçlarına iletildikten sonra bunlar aslında genel bir logların tutulduğu ve logların işlenip storage edildiği collect edildiği ve incelendiği yapılara gönderiliyor. Burada tamamen ilgili kullandığınız araca bağlı.

### Tickets

Birçok kurumda genelde ticket mekanizmalarını kurumdaki ilgili sistemci arkadaşlar göz atar.

Bu ticketing mekanizmalarının belirli şekilde alınıp incelenmesi önemlidir.

Örnek: Bir bilgisayardan devamlı olarak belirli noktalarda şöyle bir ticket açılabilir kullanıcılılar tarafından ben dosyalarıma erişemiyorum. Dosyalarım bir anda gözükmez oldu gibi bir nokta gelebilir. Bu noktada aslında bu case ilk aşamada IT ekibine gider bir kurumda bu potansiyel bir ransomware'dır. Sistemci arkadaş bunu incelemek istediğinde RDP yaparak o kullanıcıya bağlanmak istediğinde ransomware onun bilgisayarına sıçradı domain hakları olabiliyor ve powershell çalıştırma yetkileri oluyor. Bunun gibi durumlarda çeşitli ticket'ların incellenmesi gerekiyor. ITSM veya servicenow gibi bir sistem kullanıyorsanız veya manageengine gibi birçok farklı tool var.

Bu ticket'ları bir kategorize hale getirmek gerekir.

Örnek: Bir ekipten 5 6 kişi aynı anda USB denetimi istiyorsa bu bir şüphe uyandırmalı

Örnek: Sistem alert'leri olabilir. PRTG'de birden bir anda birçok kullanıcı çok fazla RAM veya CPU tüketebilir bunlarında Ticket'ları genelde sistem ekiplerine düşüyor (Mining zararlısı bulaşmış olabilir.).

Örnek: İçeride PAM ürünü var. Çeşitli Privileged account haraketlerinin kayıtlarını alıyor.

### Threat Hunting

Bir life cycle'dan oluşuyor. Önce bir noktanın hedeflenip threat hunting yapılması (target threat hunting) eğer bir bulgu bulunursa incident response aşamasına geçilmesi ardından tehditlerin yok edilmesi (eradicate threat) 3 basamaklı bir döngüden oluşuyor.

Threat Hunting: Belirli sistemlerin loglarını cidden alınıyor. Denetleniyor ve parse edip normalizasyonun yapılmış olması gerekiyor. Ve daha sonrasında da siz bunun ilgili sistem hakkında bir threat hunt'a giriştiğiniz zaman çeşitli süreçlerini kontrol edeceksiniz.

* Örnek: Bu cihazlarda süreçlerde gelen loglar neler logların kategorizasyonu neler hangi trafikler cihaz üzerinde oluşan engellenmiş.

* Hedefleyerek gitmek en iyisi

Incident Response: Neler yapılması gerekiyor hangi planın adım adım dizayn edilmesi gerekiyor.

* Kurum genelinde bir incident response planınızın development edilmesi gerekiyor. Bu noktada işte ilgili mesela atak vektörünün neler olduğu ve bu atak vektörünü nasıl engellememiz gerektiğini bu atak vektörünün aslında nasıl ortadan kaldırılması

* Bir incident oluştuğu zaman birçok ekibe ortaklaşa çalışmanız gerekiyor. Bu ekiplerle nasıl anlaşacaksınız. Nasıl hareket edeceksiniz

Eradicate Threat: Tespit edilen bu zararlı yazılımı sistemden tamamen atılması.

### Threat Intelligence

Tehdit istihbaratı toplamak için bir ana nedenimiz olması gerekiyor.

Bunlar neler?

* Ben gıda sektöründe çalışıyorum. Gıda sektöründe bulunan firmalara yönelik çıkacak olan threat intelligence'ları toplamak istiyorum. Neden çünkü Gıda sekötrünü hedefleyen çeşitli saldırganları ve vektörleri A kurundaki gıda sektörünü hedefleyen bir zararlının yakında bana da etki edeceğini tahmin edebiliyorum.

* MISP'i kurarak kendi elde ettiğiniz threat intelligents verilerini kategorize ederek burada toplamanız ardından bu dataların her birini işlemden geçirmeniz gerekiyor.

The 5 stages of the threat intelligence lifecycle

* Set goals and objectives

* Collect Data

* Process Data

* Analyze Data

* Report Findings
