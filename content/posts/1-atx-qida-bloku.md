---
author: ["Orxan Əmiraslan"]
title: 'ATX Kompüter qida blokundan stolüstü qida blokunun hazırlanması'
date: 2014-09-19
description: "ATX qida lokunda stolüstü qida blokunu hazırlanması."
summary: "Bu proyektdə kompüter qida blokundan istifadə edərək  +12, +5, +3.3, -5 və -12 V çıxış gərginlikləri olan stolüstü qida bloku hazırlayacam."
tags: ["atx", "hackin", "qida-bloku", "elektronika"]
categories: ["hacking", "lab"]
series: ["Lab alətləri"]
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

![Warning](/images/1-atx/1-2-warning.jpg)

Qurğunu hack etməyə başlamadan öncə, bir neçə dəfə elektrik şoku almış birisi olaraq xəbərdarlıq etmək istərdim ki, elektriklə işləyərkən hər zaman ehtiyyatlı olun. Qurğunun dövrəyə qoşulu olmadığına əmin olun. Hətta, qida bloku dövrəyə qoşulu olmadıqda belə, qoruyucu qapağı açıq əllə açmağa cəhd etməyin, çünki blokun içində olan böyük filter tutumlarında sağlamlığa ciddi zərər verəcək qədər yüksək gərginlikli cərəyan toplanmış olur. Bu səbəbdən, yaxşı olar ki, izolyasiya əlcəklərindən istifadə edəsiniz və blokun qutusunu açdıqdan sonra 15-20 sm uzunluğunda ucları kəsik, izolyaisya olunmuş qalın elastik kabel vasitasilə bütün tutumları boşaldasınız. Bunu etmək üçün, sadəcə tutumun əlaqələndirici ucluqlarını dövrədə tapıb, qısa qapasanız kifayət edər (Ani boşalma zamanı qığılcımlar sizi qorxutmasın). Xətti gərginlik tənzimləyiciləri artıq olan gərginliyi istilik şəklində hasil etdiklərindən effektiv deyil. Buna misal üzərində baxaq, məsələn çıxışda 1A yük olduqda, onda çıxışda istifadə olunan güc 5V*1A = 5W, girişdə isə 12V*1A = 12W, arada itən 7W isə tənzimləyici tərəfindən istilik şəklində ayrılır. Kompüterdə istifadə olunan qida blokları isə impuls rejimli (Switching-mode Power Supply) olduqlarından yüksək effektivliyə malikdirlər.

