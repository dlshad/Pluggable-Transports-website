---
layout: single
author_profile: false
permalink: /ar/implement/

excerpt: ""
header:
  overlay_image: /assets/images/Unsplash-7kkqg0eb_ti-ankush-minda.resized.jpg
  caption: "Photo credit: [**Unsplash / Ankush Minda**](https://unsplash.com/@an_ku_sh)"
#  cta_label: "للمزيد من المعلومات"
#  cta_url: "https://unsplash.com"

sidebar:
    nav: "sidenav"

---

*يشرح الجدول التالي الخيارات المتوفرة حالياً لتطبيقات تستخدم النواقل وأنواع النواقل المتوفرة والقابلة للاستخدام على نظم تشغيل مختلفة.*

|                        | *Windows*                                                                                                                           | *OSX*                                                                                                                               | *Linux*                                                                                                                             | *Android*                                                                                                                                                                                                                                       | *iOS*                                                                                                                               |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| *تطبيقات تستخدم نواقل* | [Tor Browser](http://torproject.org/), [Lantern](https://getlantern.org/), [Psiphon 3](https://www.psiphon3.com/)                   | [Tor Browser](http://torproject.org/), [Lantern](https://getlantern.org/),                                                          | [Tor](https://www.torproject.org/docs/tor-doc-unix.html.en), psiphon-tunnel-core                                                    | [Orbot](https://guardianproject.info/apps/orbot/), [Lantern](https://play.google.com/store/apps/details?id=org.getlantern.lantern&hl=en), [Psiphon 3](https://s3.amazonaws.com/0ubz-2q11-gi9y/en.html), [FreeBrowser](https://freebrowser.org/) | [OnionBrowser](https://itunes.apple.com/us/app/onion-browser-secure-anonymous-web-with-tor/id519296448?mt=8)                        |
| *خدمات النواقل*        | [Dispatcher](https://github.com/OperatorFoundation/shapeshifter-dispatcher), [obfs4proxy](https://github.com/Yawning/obfs4),        | [Dispatcher](https://github.com/OperatorFoundation/shapeshifter-dispatcher), [obfs4proxy](https://github.com/Yawning/obfs4),        | [Dispatcher](https://github.com/OperatorFoundation/shapeshifter-dispatcher), [obfs4proxy](https://github.com/Yawning/obfs4),        | [Dispatcher](https://github.com/OperatorFoundation/shapeshifter-dispatcher), [obfs4proxy](https://github.com/Yawning/obfs4),                                                                                                                    | [OnionBrowser custom obfs4proxy](https://github.com/mtigas/iObfs)                                                                   |
| *مكتبات قابلة للدمج*   | PT 2.0 Go API                                                                                                                       | PT 2.0 Go API                                                                                                                       | PT 2.0 Go API                                                                                                                       | [PLUTO](https://github.com/guardianproject/pluto), [NetCipher](https://github.com/guardianproject/NetCipher)                                                                                                                                    | [OnionBrowser custom API](https://github.com/mtigas/OnionBrowser)                                                                   |
| *تطبيقات النواقل*      | [shapeshifter-ipc (Go)](https://github.com/OperatorFoundation/shapeshifter-ipc), [goptlib (Go)](https://github.com/Yawning/goptlib) | [shapeshifter-ipc (Go)](https://github.com/OperatorFoundation/shapeshifter-ipc), [goptlib (Go)](https://github.com/Yawning/goptlib) | [shapeshifter-ipc (Go)](https://github.com/OperatorFoundation/shapeshifter-ipc), [goptlib (Go)](https://github.com/Yawning/goptlib) | [shapeshifter-ipc (Go)](https://github.com/OperatorFoundation/shapeshifter-ipc), [goptlib (Go)](https://github.com/Yawning/goptlib)                                                                                                             | [shapeshifter-ipc (Go)](https://github.com/OperatorFoundation/shapeshifter-ipc), [goptlib (Go)](https://github.com/Yawning/goptlib) |

**الخيارات التطبيقية**

بإمكان المطورين دمج النواقل من الصفر، او استخدام مكتبة توفر IPC Protocol مثل Shapeshifter-ipc او goptlip, كما انه من الممكن كتابة النواقل القابلة للتوصيل بأي لغة برمجة.

تستطيع النواقل التواصل مع التطبيقات بواسطة بروسس داخلي يسمح بالتواصل ما بين الناقل والتطبيق inter-process communication (IPC) protocol المشروح بشكل كامل في مستند المواصفات والخصائص للنواقل القابلة للتوصيل الإصدار الثاني. يوجد العديد من النواقل التي تم كتابتها باللغات التالية: Go, Python, C++ و C.

البديل الأسرع من دمج النواقل من الصفر هي لاستخدام الناقل المكتوب بلغة Go باستخدام [Go API](https://www.pluggabletransports.info/ar/implement/go) المتوفرة في مستند المواصفات والخصائص للنواقل القابلة للتوصيل الإصدار الثاني. في الوقت الحالي، تقتصر هذه العملية من التنفيذ على النواقل المكتوبة بواسطة لغة الـ Go, بالمقابل يوجد فوائد من اتباع هذا الأسلوب من التنفيذ حيث ان التطبيقات المكتوبة بلغة Go تستطيع استخدام جميع النواقل المكتوبة بنفس اللغة و التي تتبع المواصفات والخصائص للنواقل القابلة للتوصيل الإصدار الثاني, متجاوزة في ذلك الجهد الإضافي المتمثل باستخدام IPC, و بدوره يقوم بتبسيط عملية الدمج و التنفيذ كما انها ترفع من سوية عمل التطبيق و أدائه لكونه لم يتم إضافة بروسس اخر للتطبيق.

بالمقابل، قامت مؤسسة Operator Foundation ببناء أداة أسمتها Shapeshifter-Dispatcher والتي تقوم بدورها بتجميع جميع النواقل التي تم كتابتها استنادا المواصفات والخصائص للنواقل القابلة للتوصيل الإصدار الثاني بواسطة Go API, لتوفر بعدها طبقة الـ IPC. يسمح Shapeshifter-Dispatcher للتطبيقات الأخرى المكتوبة بلغات أخرى غير الـ Go ان تستفيد من النواقل بدون أي جهد إضافي او تعديل على التطبيق الأساسي. على سبيل المثال, بإمكان مزودي خدمات الـ VPN استخدام الأداة بدون الحاجة للتعديل على التطبيق الأساسي الخاص بهم.

**ما هو (المرسل) Dispatcher؟**

تتألف العملية ككل من عنصرين، النواقل والمرسل. تقوم النواقل بتوفير عنصر التمويه لمنع عملية الحظر، تم تزويد هذه النواقل كمكتبات مكتوبة بالـ Go و التي من الممكن دمجها بشكل مباشر بالتطبيق, اما المرسل Dispatcher فهو عبارة عن أداة سطر أوامر Command line و التي تلعب دور البروكسي التي تغلف مكتبات النواقل, بالمقابل توفر الأداة عدة طرق للبروكسي كما انها تستطيع استقبال البيانات على شكل TCP او UDP.

إن كنت مطوراً وقمت بكتابة تطبيقك بلغة الـ Go, من الأسهل لك استخدام [مكتبات النواقل](https://github.com/OperatorFoundation/shapeshifter-transports) بشكل مباشر ودمجها في تطبيقك.

في حال كنت مستخدماً يرغب بتجاوز الحظر المفروض على أداة معينة، او مطوراً يرغب بفك الحظر ضد تطبيق مكتوب بلغة مختلفة غير الـ Go, فأنه يتوجب عليك استخدام المرسل Dispatcher. يرجى الأخذ بعين الاعتبار ان استخدام Dispatcher يحتاج خبرة بالتعامل مع سطر الأوامر command line.

الهدف من وجود Dispatcher هو توفير واجهة مختلفة كبروكسي لاستخدام النواقل. بواسطة استخدام البروكسيات تلك, تستطيع التطبيقات المستهدفة دفق البيانات الخاصة بها عبر البروكسي و التي بدورها تسمح بتمرير البيانات عبر قنوات محظورة.

**ماهي الفوارق بين اتصالات النواقل واتصالات الشبكة؟**

من الهام جداً شرح الفرق بين اتصالات النواقل واتصالات الشبكة Transport Connections vs Network Connections. اتصال الناقل هو عبارة عن قناة تواصل بين عميل الناقل transport client وخادم الناقل Transport Server, والتي بدورها تستطيع الاتصال بواسطة البروتوكول المقدم من قبل الناقل. بالمقابل، اتصالات الشبكة، هي عبارة عن اتصال مباشر بين جهازي كومبيوتر والتي بدورها تقوم بتبادل البيانات بشكل مباشر، بواسطة بروتوكولات محددة.

للسهولة، الـ API الخاص بالنواقل يقوم الى حد ما بتقليد الواجهة الخاصة بـ اتصال الشبكة Network connection interface, على سبيل المثال، قد يتعامل تطبيق ما مع الناقل كاتصال لشبكة مستقلة. بالمقابل الخريطة المحددة لكيفية التواصل بين اتصالات الشبكة واتصالات النواقل تعتمد على تصميم الناقل وقد تختلف من ناقل الى اخر. بعض النواقل على سبيل المثال تمتلك اتصال شبكة واحد لكل ناقل، بينما توفر نواقل أخرى إمكانية توزيع بيانات اتصال الناقل الواحد عبر عدة اتصالات للشبكة او عدة اتصالات لعدة نواقل عبر اتصال شبكة واحدة. من الممكن ايضاً ان تتم العملية بدون حتى أي اتصال للشبكة وذلك بواسطة نقل البيانات عبر بدائل بدون اتصال كـUDP .

بالإضافة للسهولة التي يوفرها API النواقل القابلة للتوصيل عبر توفير خيارات عديدة لربط اتصالات الشبكات بالنواقل والعكس، يوفر ايضاً حالات شائعة common case لاتصال ناقل لكل اتصال شبكة. بالتحديد في حال وجد اتصال رئيسي للشبكة خاص باتصال الناقل، فمن الممكن بسهولة استرجاع اتصال الناقل والوصول له بشكل مباشر.

وقد يكون هذا مفيداً بالذات في حالة العمل على اعداد شبكة في مستويات منخفضة Lower-level network configuration مثل اعداد خيارات الشبكة لاتصال معين.

للمزيد، قم بالاطلاع على [المستند التالي](https://github.com/OperatorFoundation/shapeshifter-dispatcher/blob/master/README.md) الذي قام بكتابته Dr. Brandon Wiley حول Dispatcher.
