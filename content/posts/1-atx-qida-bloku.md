---
author: ["Orxan Əmiraslan"]
title: 'ATX Kompüter qida blokundan stolüstü qida blokunun hazırlanması'
date: 2014-09-19
description: "ATX qida lokunda stolüstü qida blokunu hazırlanması."
summary: "Bu proyektdə kompüter qida blokundan istifadə edərək  +12, +5, +3.3, -5 və -12 V çıxış gərginlikləri olan stolüstü qida bloku hazırlayacam."
tags: ["ATX", "hacking", "qida-bloku", "elektronika"]
categories: ["hacking", "lab", "layihələr"]
#series: ["Lab alətləri"]
ShowToc: true
TocOpen: true

cover:
    image: "images/1-atx/1-1-atx.jpg" 
    alt: "ATX qida bloku" # alt text
    caption: "ATX Qida Bloku" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: false # only hide on current single page
    responsiveImages: true
    linkFullImages: true

draft : false


---

# Giriş

Salam, əziz MakerLog oxucusu. Bu mənim ilk postumdur. Ümid edirəm, bütün oxuculara maraqlı olacaq. İrad və təklifləriniz varsa, zəhmət olmasa şərh bölməsinə qeyd edin.
Başlayaq!

Bu proyektdə kompüter [qida blokundan](https://az.wikipedia.org/wiki/Qida_bloku) istifadə edərək  **+12, +5, +3.3, -5 və -12V** çıxış gərginlikləri olan stolüstü qida bloku hazırlayacam. İlk öncə bildirim ki, internetdə Azərbaycan dilində məlumatın azlığından bəzi texniki terminlərin adını  mötərizə içərisində ingiliscə görəcəksiniz. Bu terminlərdən istifadə edib daha ətraflı məlumatlar axtarıb,  tapa bilərsiniz.
İstər hobbi, istərsə də peşəkar hər bir elektrik/elektronik mühəndisin iş masasında qurğuların işini ölçmə və yoxlama aparmaq məqsədilə müxtəlif çıxış nominallı qida blokunun olması vacibdir. Bu yaxınlarda mənə Litium-Polimer (Li-Po) batareyalarını yükləmək üçün yüksək güclü **(>50 Vatt)** qida bloku lazım oldu və bu cür qida bloklarının qiyməti baha olduğundan, əlimdə olan ikinci əl  kompüter qida blokunu  şəxsi istifadəm üçün modifikasiya edib istifadə etmək qərarına gəldim.

Sabit cərəyan qida bloku (*ing.* [DC Power Supply](http://en.wikipedia.org/wiki/Power_supply)) nədir və necə işləyir? – Qida bloku dəyişən cərəyanı aşağı gərginlikli sabit cərəyana çevirir və dövrədə olan qurğuları gərginliyi satabil saxlamaqla sabit cərəyanla təmin edir. Qida blokunun sadə iş prinsipini aşağıdakı sxemdən görə bilərsiniz.

[![CircuitLab Schematic 86uqw5](https://www.circuitlab.com/circuit/86uqw5/screenshot/540x405/)](https://www.circuitlab.com/circuit/86uqw5/voltage-converter/)

Sxemdə transformatorun girişinə verilən ~220V gərginlik çıxışda bizə lazım olan gərginlik intervalına qədər azaldılır. Bu azalma transformatorun dolaq nisbətindən asılı olaraq dəyişir. Daha sonra aşağı gərginlikli dəyişən cərəyan diod körpüdə düzləndirilərək sabit cərəyana çevrilir. Daha sonra gərginlik filter tutumları vasitəsilə küylərdən azad edilir. Daha da stabil forma alan gərginlik (məs. +12V) xətti gərginlik tənzimləyicisi (Linear voltage regulator) vasitəsilə aşağı gərginliklərə qədər azaldılaraq (məs. +5V) müxtəlif cihazlar üçün qida mənbəyi olaraq istifadə oluna bilər. Tənzimləyici giriş və çıxışındakı tutumlar ani yük dəyişmələri zamanı gərginliyi maksimal dərəcədə stabil saxmalağa yardım edir.

<!-- ![Warning](/images/1-atx/1-2-warning.jpg)-->


# Təhlükəsizlik xəbərdarlığı ⚠️

**⚡ Diqqət, yüksək gərginlik‼️**

Qurğunu hack etməyə başlamadan öncə, bir neçə dəfə elektrik şoku almış birisi olaraq xəbərdarlıq etmək istərdim ki, elektriklə işləyərkən hər zaman ehtiyyatlı olun. Qurğunun dövrəyə qoşulu olmadığına əmin olun. Hətta, qida bloku dövrəyə qoşulu olmadıqda belə, qoruyucu qapağı açıq əllə açmağa cəhd etməyin, çünki blokun içində olan böyük filter tutumlarında sağlamlığa ciddi zərər verəcək qədər yüksək gərginlikli cərəyan toplanmış olur. Bu səbəbdən, yaxşı olar ki, izolyasiya əlcəklərindən istifadə edəsiniz və blokun qutusunu açdıqdan sonra 15-20 sm uzunluğunda ucları kəsik, izolyaisya olunmuş qalın elastik kabel vasitasilə bütün tutumları boşaldasınız. Bunu etmək üçün, sadəcə tutumun əlaqələndirici ucluqlarını dövrədə tapıb, qısa qapasanız kifayət edər (Ani boşalma zamanı qığılcımlar sizi qorxutmasın). Xətti gərginlik tənzimləyiciləri artıq olan gərginliyi istilik şəklində hasil etdiklərindən effektiv deyil. Buna misal üzərində baxaq, məsələn çıxışda 1A yük olduqda, onda çıxışda istifadə olunan güc 5V*1A = 5W, girişdə isə 12V*1A = 12W, arada itən 7W isə tənzimləyici tərəfindən istilik şəklində ayrılır. Kompüterdə istifadə olunan qida blokları isə impuls rejimli (Switching-mode Power Supply) olduqlarından yüksək effektivliyə malikdirlər.

**Lazımi materiallar:**

- İşlənmiş və ya yeni kompütər qida bloku (PSU)
- 4 əd. güc müqaviməti (dummy load resistors)
- 2 əd. müxtəlif rəngli LED (göy və qırmızı)
- 2 əd. 330 Om, 0.25 Watt müqavimət
- Elektrik Açarı (SPST/SPDT, Toggle switch)
- 4mm diametrli çıxış konnektorları (Banana Plug Sockets 8x)
- Yığılan izolyatorlar (Heat shrink) və ya izolent
- Prototipləşdirmə lövhəsi

**Lazımi alətlər:**

- Plastik yapışdırıcı (Hot glue gun)
- Kabel kəsici kəlbətin
- Nazik uclu kəlbətin
- Drel
- Vintaçan
- Lehim (solder)
- Lehimləyici (soldering iron)

> Qeyd: Xatırladım ki, bütün bu sadalanan komponentləri tapmaqda çətinlik çəksəniz [**hazır modulunu** ](https://makerstore.az/product/atx-qida-bloku-cevirici-adapter-modulu/)alıb, istifadə edə bilərsiniz.

[![ATX Adapter Modulu](https://live.staticflickr.com/65535/53804871815_2df0eb20a4_b_d.jpg)](https://makerstore.az/product/atx-qida-bloku-cevirici-adapter-modulu/ "ATX Adapter Modulu")

# Hazırlanma prosesi
Kompüter qida bloklarının müxtəlif model və formaları mövcuddur. Əsas göstərici olaraq çıxış kanallarının güclərinin cəmi götürülür. Əlimdə olan qida blokunda bu göstərici 350 Watt-a bərabərdir.


![350W ATX qida bloku](https://live.staticflickr.com/3938/15369545598_fb84040ee6_b_d.jpg "350W ATX qida bloku")



Qida bloklarının üzərindəki etiketlərdə ümumi güc və ayrılıqda hər bir çıxış kanalının maksimal gücü və cərəyan qiyməti göstərilir. Köhnə kompüterlərin ana plataları əsasən 5V gərginlikli rəqəmsal dövrələrdən təşkil olunduqları üçün qida bloklarının da +5V kanalı ən böyük çıxış gücünə sahib olur. Həmçinin, köhnə qida bloklarında -5V çıxışı da mövcuddur. Lakin yeni qida blokların +12V çıxışı daha böyük cərəyanla təmin etmə gücünə malikdir və onlarda -5V çıxışı mövcud deyil.


<!-- 
![ATX Konnektor tipləri](https://live.staticflickr.com/3928/15369670387_1b89f8b60a_o_d.gif "ATX Konnektor tipləri")
-->

<p align="center">
  <img src="https://live.staticflickr.com/3928/15369670387_1b89f8b60a_o_d.gif" title="ATX Konnektor tipləri" alt="ATX Konnektor tipləri"/>
</p>


Bunu konnektordakı pinlərin sayına baxıb müəyyən etmək olar. Köhnə qida bloklarında adətən 20 pinli, yenilərində isə 24 pinli konnektorlar olur.

![Çıxış kanallarının güc göstəricisi](https://live.staticflickr.com/5611/15369669607_8fb9d41fda_b_d.jpg "Çıxış kanallarının güc göstəricisi")

Bloku hack etməzdən əvvəl əlimizəki qida blokunun köhnə və ya yeni model olduğunu müəyyənləşdirməyimiz bizə güc müqavimətinin seçimi zamanı çox yardımçı olacaq. Kompüter qida blokları impuls rejimli (Switching-mode Power Supply) olduqlarından normal iş rejimini təmin etmək üçün blokun çıxışında daim müəyyən qədər yük (dummy load) olmalıdır (təxm. 2-4 Watt). Bəzi qida bloklarının içərisində belə yük artıq mövcuddur, lakin hər ehtimala qarşı bunu etməkdə fayda var.


Çıxışda maksimal güc hansı kanaldadırsa yük də həmin kanala əlavə olunmalıdır. Əgər bu kanal +5V-dursa onda müqaviməti 10 Om, gücü isə minimum 10 Watt olan resistordan istifadə etməliyik. Maksimal güc +12V-dursa o zaman, 22 Om, 10Watt olan müqavimətdən istifadə etmək lazımdır.

<p align="center">
  <img src="https://live.staticflickr.com/3939/15370046340_42342de77a_o_d.jpg" title="10 Om 10W Keramik güc müqaviməti" alt="10 Om 10W Keramik güc müqaviməti"/>
</p>


Qida bloklarının bir çoxunun strukturu bənzər olduğundan, oxşar mənzərə ilə qarşılaşırıq. Aşağıdakı şəkilə diqqət yetirək.


![ATX qida blokunun daxili görünüşü](https://live.staticflickr.com/3934/15369669907_269fa1e9dd_b_d.jpg "ATX qida blokunun daxili görünüşü")

Girişə verilən sabit cərəyan dolaqlar (coil/inductor) və tutumlar vasitəsilə filterləndikdən sonra, körpü düzləndiricisi vəsitəsilə yüksək gərginlikli sabit cərəyana (HVDC High Voltage DC) çevrilir. Şəkildə gördüyümüz iki böyük filtr tutumları isə bu sabit cərəyanı daha da stabilləşdirmək üçün istifadə olunur. Daha sonra HVDC güc tranzistorlari vasitəsilə yenidən tezlik intervalı  50-60 KHz olan dəyişən cərəyana çevrilir. Bu ona görə edilir ki, yüksək tezliklərdə kiçik transformator istifadə edilərək daha effektiv dövrələr yığmaq mümkün olur. Daha sonra transformatorun çıxışında müxtəlif nominallı dəyişən gərginliklər şotki diodlar vasitəsilə düzləndirilir və induktiv filtrlənmədən keçərək, çıxışa verilir. Bununla yanaşı, ATX qida bloklarında çox vaxt dövrədəki inteqral mikrosxemlərin işini təmin etmək üçün əlavə (standby) az güclü qida dövrəsi olur. Bənövşəyi rəngli kabeldə olan gərginlik (+5V, max. 2A) bu dövrə hesabına yaradılan gərginlikdir.

# Kabellərin rəng kodu


- Sarı &rarr; +12 V
- Sarı (qara zolaqla) &rarr; +12 V ( yeni PSU-larda) prosessor üçün, 4pin konnektor
- Qırmızı &rarr; +5 V
- Çəhrayı &rarr; +5 V Sense (yeni PSU-larda) çıxışı tənzimləmək üçün
- Narıncı &rarr; +3.3 V
- Qəhvəyi &rarr; +3.3 V Sense –  aşağı gərginlik yüksək cərəyan olduqda gərginlik itkisinin qarşısını almaq üçün əks əlaqə (feedback loop)
- Qara &rarr; Torpaq (GND)
- Ağ &rarr; -5 V
- Göy &rarr; -12 V
- Yaşıl &rarr; GND-a (Power ON) qoşulduqda qida blokunu aktivləşdirir
- Boz (külrəngi) &rarr; Qida bloku aktivləşdirildikdən 0.1-0.5 san sonra +5V olur (Power Good), çıxış lazımi intervaldadırsa, çıxış aktivdir indikatoru üçün istifade olunub
- Bənövşəyi &rarr; +5 V Standby(max. ~2 A), çıxış aktiv olmadıqda belə bu kanal aktivdir, led indikator (standby) kimi istifade olunub

Yekun dövrədə kabelləşmənin necə aparıldığını aşağıdakı sxemdən aydın şəkildə görə bilərsiniz.

![Kabelləşmə sxemi](https://live.staticflickr.com/3932/15369669417_07dbf77805_b_d.jpg "Kabelləşmə sxemi")

Ilk novbədə elektrik açarını daha sonra isə LED lamlarını 330 Om muqavimətlərlə dövrəyə qoşuruq.

![Açar](https://live.staticflickr.com/3932/15531974446_3a047daf14_d.jpg "Açar")

![LED](https://live.staticflickr.com/5599/14935507863_2b6a7bca23_d.jpg "LED")

İndi isə növbə çıxış yük müqavimətindədir. İlk öncə planım 10 Om 10 Wattlıq 1 ədəd güc müqaviməti işlətmək idi, amma təcrübələr onu göstərdi ki, məndə olan keramik 10 Wattlıq keramik müqavimətlər hətta 2.5Watt enerji istifadəsi zamanı həddən artıq qızır (ucuz Çin mallarında bu hal təəccüblü deyil). Buna görə də müqavimətlərin ardıcıl-paralel kombinasiyasından istifade etdim. Yekun müqavimət 10 Om, maksimal güc isə 40Wattdır. 5V gərginlik altında ayrılıqda hər müqavimət 0.625 Watt ümumilikdə isə 2.5 Watt enerji işlədilir. Bu enerji boş yerə sərf olunurmuş olsa da, qida blokunun sabit və uzunmüddətli işimim təminatçısıdır.

![Güc rezistoru](https://live.staticflickr.com/3936/14935508893_0262f25546_d.jpg "Güc rezistoru")
![Güc rezistoru 2](https://live.staticflickr.com/3931/15555689155_08fee827fb_d.jpg "Güc rezistoru 2")

![Dummy load](https://live.staticflickr.com/5597/15553006651_0aebb032d8_d.jpg "Dummy load")
![Dummy load 2](https://live.staticflickr.com/3946/15556521212_ded198c3c3_d.jpg "Dummy load 2")


Lehimləmədən öncə yığılan izəlyatorları kabellərə uyğun ölçüdə keçirib, sonra lehimləmə aparırıq. Daha sonra çıxış konnektorlarını da sxemdə göstərildiyi kimi əlaqələndiririk.

![Çıxış GND kabelləri](https://live.staticflickr.com/3947/15555688505_086b8f1eca_c_d.jpg "Çıxış GND kabelləri")

![Kabel əlaqələri 1](https://live.staticflickr.com/5597/14935507623_da264f7362_c_d.jpg "Kabel əlaqələri 2")
![Kabel əlaqələri 2](https://live.staticflickr.com/3950/15370047180_c1e9f48f79_b_d.jpg "Kabel əlaqələri 3")
![Kabel əlaqələri 3](https://live.staticflickr.com/3930/15555687715_86972cc59f_b_d.jpg "Kabel əlaqələri 4")
![Kabel əlaqələri 4]( "GND")
![Kabel əlaqələri 5](https://live.staticflickr.com/3934/15369669907_269fa1e9dd_b_d.jpg "Kabel əlaqələri 5")

Aşağı gərginlikli çıxış kanallarında cərəyan istifadəsi yüksək olduqda gərginlik düşküsü daha çox olur, bunu aradan qaldırmaq üçün qida bloklarında əks-əlaqə (sense wire – feedback loop) kabelləri olur və bunun vasitəsilə kabellərdə olan gərginlik düşgüsü kompensasiya olunur. Məndə olan qida blokunda +3.3V Sense kabeli olduğundan onu birbaşa +3.3V kanaləna qoşuruq.Aşağı gərginlikli çıxış kanallarında cərəyan istifadəsi yüksək olduqda gərginlik düşküsü daha çox olur, bunu aradan qaldırmaq üçün qida bloklarında əks-əlaqə (sense wire – feedback loop) kabelləri olur və bunun vasitəsilə kabellərdə olan gərginlik düşgüsü kompensasiya olunur. Məndə olan qida blokunda +3.3V Sense kabeli olduğundan onu birbaşa +3.3V kanalına qoşuruq.


![Sense xətti](https://live.staticflickr.com/3932/15369061969_8cac4755cf_b_d.jpg "Sense xətti")

Bütün açıqda olan lehim nöqtələrinin tam izəlyasiya edilməsi mütləqdir. Bir çox qida bloklarının əsas çıxış kanallarında ifrat-cərəyan qoruyucusu (overcurrent protection) olur, bu isə nominaldan artıq cərəyan işlədildiyi və ya qısa-qapanmalar zamanı dövrəni qorumaq üçündür. Bununla belə kabellər qızıb, əriyə və digər dəyişən cərəyan dövrə elementləri ilə qısa-qapanmaya səbəb ola bilər. Buna görə də kabellərin tam izolyasiyası mütləqdir.


![Kabel izolyasiyası](https://live.staticflickr.com/3955/15556520082_6e799c51c5_b_d.jpg "Kabel izolyasiyası")

# Nəticə

Kabelləşməni apardıqdan ilk dəfə qurğunu test edib heç bir qısa qapanmanın olmadığına və elektrik açarının açıq olduğuna əmin olduqdan sonra dövrəyə qoşub yoxlayırıq. İlk olaraq qırmızı LED yanaraq qida blokunun qoşulmağa hazır olduğunu göstərir, açarı qapadıqda isə mavi LED yanaraq sistemin tam işlək vəziyyətdə olmasını göstərir. Bundan sonra multimetr vasitəsilə hər bir kanalın təmin etdiyi gərginliyi ölçürük. Əgər hər hansısa kanalda göstərici nominaldan çox fərqlənirsə onda problemin səbəbi ya qida blokunun nasaz olmasından, ya kabelləşmənin düzgün aparılmamasından və ya çıxışda olan yük müqavimətinin kifayət qədər enerji sərf etməməsindən ola bilər.  Kompüter qida bloklarının gücləri artdıqca çıxışda tələb olunan minimal güc sərfiyyatı da arta bilər (3-5 Watt). Buna görə istifadə etməli olduğumuz yük reziztorlarını daha aşağı müqavimətdə, lakin böyük gücdə seçmək lazımdır. Əgər əlinizdə güc müqaviməti yoxdursa, müvəqqəti olaraq avtomobil lampalarından isfitadə edə bilərsiniz. Bu zaman israf olunan cərəyan təxminən 4-5 amper, enerji isə 20-25 Watta qədər qalxa bilər.

![ATX Qida Bloku (qapalı)](https://live.staticflickr.com/3942/14935508173_26316e865e_b_d.jpg "ATX Qida Bloku (qapalı)")
![ATX Qida Bloku (açıq)](https://live.staticflickr.com/5598/15555688775_2765583ae2_b_d.jpg "ATX Qida Bloku (açıq)")

Layihənin məqalədə yerləşdirilən və əlavə bütün şəkillərinə Flickr qalareyadan göz gəzdirə bilərsiniz.

Qaranlıq qalan hansısa məqam olsa [bizə](https://linktr.ee/makerspaceAZ) yaza bilərsiniz. Oxuduğunuz üçün təşəkkür edirəm. Hər kəsə uğurlar!

<a data-flickr-embed="true" href="https://www.flickr.com/photos/orkhan/albums/72157648806147212" title="ATX to Lab Bench power supply"><img src="https://live.staticflickr.com/3932/15369061969_8cac4755cf_b.jpg" width="1024" height="768" alt="ATX to Lab Bench power supply"/></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>