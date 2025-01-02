# Cyber Security Blue Team: Incident Responder Series - Part 1

## Splunk SPL Language and Rule Development - SPL

Splunk Processing Language - SPL

Main Component Commands;

- search
- fields
- table
- rename
- sort
- dedup
- stats
- eval
- where
- head

### Splunk Search Language Example

!["SQL Example"](/assets/spl_example.png)

search: Bir sorgu ile eşleşen olayları arar.

- `search error` 

fields: Belirli alanları ekler ve kaldırır.

- `fields + user_id, action`

table: Sonuçları kolon formatında gösterir.

- `table user_id, action`

rename: Alan adlarını yeniden adlandırır.

- `rename user_id as UserID`
- `...| rename AS new_field_name`
- `...| rename userlD AS User_lD`
- `...| rename old-field1 AS new-field1, old-field2 AS new-field2`
- `...| rename firstName AS first-name, lastName AS last-name `
- `...| eval new_field_name = old_field_name | rename new_field_name AS desired_field_name`

sort: Sonuçları belirli bir veya daha fazla alanlara göre sıralamak için kullanılır.

- `| sort field_name`
    - `| sort price`
- `| sort -field_name`
    - `| sort -price`
- `| sort -field1, field2`
    - `| sort category, -price`
- `| sort limit=10 -field_name`
    - `| sort limit=5 -price` 

dedup: Tekrar eden olayları kaldırarak veri kümesini sadeleştirmek için kullanılır.

- `| dedup field_Name`
    - `| dedup userID`
- `| dedup field1, field2`
    - `| dedup userID, action`
- `| dedup field_name sortby=-another_field`
    - `| dedup userID sortby=-score`: en yüksek score değerini korumak isterseniz.

stats: veri üzerinde istatiksel hesaplamalar yapmak için oldukça güçlü bir araçtır.

- `| stats count by field_name`
    - `| stats count by action`
- `| stats sum(field_name) by another_field`
    - `| stats sum(purchaseAmount) by userID`
- `| stats count, avg(field_name), max(another_field) by yet_another_field ` 
    - `| stats count, avg(price), max(price) by product` 
- `| stats count by field1 ,field2`
    - `| stats count by product, region`

eval: veri üzerinde hesaplamalar yapmak için yeni alanlar oluşturmak veya mevcut alanları değiştirmek için kullanılır.

1. `| eval new_field = field1 + field2`
    - `| eval total_price = price + tax`
2. `| eval discount_price = price * 0.9`
3. `| eval status = if(score > 90, "Excellent", "Good)`
4. `| eval full_name = first_name . " " . last_name`
5. `| eval rounded_price = round(price)`
6. `| eval price = price *0.8`
7. `| eval field_name = coalesce(field_name, "default_value")` // field name null ise değeri default_value ile doldurulur.
8. `| eval readable_date = strftime(_time, "%y-%m-%d")` // Tarih ve saat işlemlerini gösterilir.

where:

1. `| where field_name > vaule`
    - `| where price > 100`
2. `| where field1 = value1 AND field2 = value2`
    - `| where status = "active" AND age > 30`
3. `| where field1 = value1 OR field2 = value2`
    - `| where category = "electronics" OR category = "books"`
4. `| where isnull(field_name)`
    - `| where isnull(email)`
    - `| where isnotnull(email)`
5. `| where (price * 0.9) > 50` 

head:

1. `| head 10`
2. `| head`
3. `| sort - _time | head 5`
4. `| search category = "electronics" | head 3`

tail:

1. `| tail 10`
2. `| tail`
3. `| sort _time | tail 5`
4. `| search category="electroincs" | tail 3`

Characters and Structures

1. Piping: |

    a. index=weblogs status=200 | sort - _time | head 10 // - en yeniden en eskiye doğru

    b. index=sales | search category="electronics" | stats sum(sales) as total_sales by product | sort - total_sales | head 5

    c.index=weblogs | eval response_time_ms = response_time * 1000 | top response_time_ms

    d index=weblogs | where response_time > 2 | stats count by status_code

    e. index=weblogs earliest-"2023-08-01 00:00:00" latest="2023-08-02 00:00:00" | stats count by user_agent

2. Subsearch: [...]

    a. index=weblogs [ search index=threats threat_type="malicious" | fields src_ip ]
    
    b. index=weblogs [ search index=weblogs | top limit=10 user | fields user ]
    
    c. index=weblogs [ search index=weblogs earliest=-1h@h latest=now status=500 | fields request-id ]

3. Macros: [...]

a. Macro Defining:
    i. In the splunk web ui, you can define a new macro by going to Settings > Advanced search > Search Macros.

b. An example macro definition:
    i. Macro Name: my_example_macro
    ii. Definition: index=weblogs sourcetype=access_logs
    iii. Arguments: []

c. Macro Usage:
    i. `my_example_macro` | stats count by status
MITRE ATT&CK Framework, siber güvenlikte saldırı tekniklerini ve taktiklerini anlamak ve sınıflandırmak için kullanılan kapsamlı bir bilgi tabanıdır. MITRE Corporation tarafından geliştirilmiş olan bu framework, siber saldırıların yaşam döngüsünü anlamayı ve savunma stratejilerini optimize etmeyi amaçlar.

### MITRE ATT&CK Framework'ün Ana Bileşenleri:

1. **Taktikler (Tactics):** Saldırganın belirli bir hedefe ulaşmak için gerçekleştirdiği genel amaçlar. Örneğin, "Initial Access" (Başlangıç Erişimi) bir taktik olabilir.

2. **Teknikler (Techniques):** Taktiklerin uygulanma yolları. Her teknik, belirli bir taktiği gerçekleştirmek için kullanılabilir. Örneğin, "Phishing" (Oltalama) tekniği "Initial Access" taktiğinin bir parçasıdır.

3. **Alt Teknikler (Sub-Techniques):** Tekniklerin daha detaylı seviyelerde incelenmiş halleri. Örneğin, "Phishing" tekniğinin altında "Spear Phishing Attachment" gibi alt teknikler bulunabilir.

4. **Prosedürler (Procedures):** Saldırganların belirli teknikleri nasıl kullandıklap

5. **Mitigations (Önlemler):** Belirli tekniklere karşı alınabilecek savunma önlemleri. Örneğin, "Multi-Factor Authentication" (Çok Faktörlü Kimlik Doğrulama) gibi.

6. **Indicators (Göstergeler):** Saldırıların izlenmesi ve tespiti için kullanılabilecek izler ve göstergeler.

### MITRE ATT&CK Framework'ün Kullanım Alanları:

- **Saldırı Simülasyonları ve Testleri:** Organizasyonlar, güvenlik sistemlerini ve süreçlerini test etmek için framework'ü kullanabilirler.
- **Tehdit İstihbaratı:** Framework, tehdit istihbaratı raporlarının analizi ve korelasyonu için bir referans sağlar.
- **Savunma Stratejileri:** Savunma stratejileri geliştirmek ve iyileştirmek için kullanılır.
- **Güvenlik Farkındalığı ve Eğitim:** Güvenlik ekiplerinin eğitiminde ve farkındalık artırmada kullanılır.

MITRE ATT&CK Framework, sürekli güncellenmekte ve genişletilmektedir, bu da onu siber güvenlik dünyasında kritik bir kaynak haline getirir. Siber güvenlik uzmanları, bu framework'ü kullanarak daha iyi savunma stratejileri geliştirebilir ve potansiyel saldırıları daha etkili bir şekilde tespit edebilirler.

**Reconnaissance:** Kötü niyetli aktörlerin bir hedefe saldırı başlatmadan önce bilgi toplama sürecini tanımlar.
