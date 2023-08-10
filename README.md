سنورت: هو نظام مفتوح المصدر لاكتشاف اختراق الشبكة وايضا نظام لمنع التطفل من اهم مميزاته مراقب حركة مرور الشبكة في الوقت الفعلي ايضا يمكن تخصيصه ليوافق متطلبات امان الشبكة الخاصة بك عن طريق وضع القواعد الصحيحة.

لدى (سنورت) أكثر من وضع للاستخدام:

اولا "Packet logging" :
يستخدم لتسجيل حركة مرور الشبكة.

ثانيا "Packet sniffing" :
يستخدم الالتقاط الحزم وتحليل حركة مرور الشبكة.

ثالثا "Intrusion detection system (IDS)" :
يستخدم لرصد الأنشطة المشبوهة لحركة مرور الشبكة.

كيفية كتابة قاعدتك الخاصة؟ لكتابة قاعدتك الخاصة في (سنورت)، يمكنك اتباع الخطوات التالية:

قم بفتح ملف القواعد المخصص "local.rules" باستخدام محرر النصوص المفضل لديك. يمكن استخدام الأمر التالي في Vim لفتح الملف:

                                                                               sudo vim /etc/snort/rules/local.rules

بعد فتح الملف، يمكنك كتابة قاعدتك الخاصة. تتكون القواعد في Snort من عدة أجزاء، بما في ذلك:
• الرأس (Header): يحدد نوع القاعدة ومعلومات أخرى مثل الأولوية والتصنيف.

• الشرط (Condition): يحدد الشروط التي يجب تحقيقها لتنفيذ القاعدة.

• الإجراء (Action): يحدد الإجراء الذي يتخذه Snort عند تطابق الحزمة مع الشرط.

بعد كتابة القاعدة، قم بحفظ التغييرات في الملف.

قم بإعادة تشغيل "Snort". يمكن استخدام الأمر التالي:

                                                                                              sudo service snort restart

بعد ذلك، يجب أن تبدأ قاعدتك الخاصة في العمل وفقًا للشروط المحددة فيها.

![259416393-65e60195-5986-4a2e-becd-0eceb7b1625f](https://github.com/MuhannadImamu/Muannad/assets/141940683/ad3accbe-4710-4559-b1c4-47bc5b73e143)


سنستخدم هذا الأمر لبدء نظام كشف التسلل (IDS) باستخدام "Snort":

                                                          sudo snort -A console -c /etc/snort/snort.conf

امر"Sudo" :
هو امر التشغيل الأمر التالي مع صلاحيات إدارية.

امر"snort" :
هو الأمر الفعلي لبدء نظام كشف التسلل.


امر"A- console" :
يجب أن يصدر تنبيهات إلى وحدة التحكم.


امر"q-" :
العمل في وضع هادئ.


امر"c /etc/snort/snort.conf-” :
يحدد موقع (conf file) الذي يجب أن يستخدمه Snort. في هذه الحالة، يوجد (conf file) في "/etc/snort/snort.conf".

لمحاكاة الهجوم، استخدمنا هذي الاداتين: Nmap وhping3:

اولا "Nmap" :
وهي أداة مجانية ومفتوحة المصدر يمكن استخدامها لفحص المنافذ على مضيف الهدف. يمكنه تحديد المنافذ المفتوحة، وتحديد نظام التشغيل للمضيف الهدف، واكتشاف نقاط الضعف الأمنية المختلفة.

ثانيا "hping3" :
هي أداة مجانية ومفتوحة لإنشاء حزم البيانات المخصصة التي يمكن إرسالها إلى جهاز الهدف. يمكن استخدامها لاختبار اتصال الشبكة لجهاز الهدف، وقياس وقت الاستجابة لاتصال الشبكة، وإرسال هجمات إنكار الخدمة (Denial-of-Service (DoS)) .

لاكتشاف ومراقبة حركة مرور الشبكة، استخدمنا "Snort"، وهو نظام كشف التسلل (IDS) مفتوح المصدر مجاني. يمكن لـ "Snort" اكتشاف مجموعة متنوعة من الهجمات، بما في ذلك هجمات فحص المنافذ، وهجمات DoS، وبرامج الفدية.

يستخدم هذا الامر Nmap IP :
لتشغيل فحص Nmap على عنوان عن طريق تشغيل هذا الأمر، سيبدأ Nmap مسح عنوان الهدف وسيحاول تحديد المنافذ المفتوحة والخدمات التي تعمل على النظام.

يستخدم هذا الامر hping3 -c 5 -I 10 IP :
لإرسال 5 حزم طلب ICMP إلى عنوان. IP

هذا الأمر لتشغيل الاداه "hping3".

هذا الامر يحدد عدد الحزم المراد إرسالها "c- 5".
هذا الامر يحدد الفاصل الزمني بين الحزم بالملي ثانية "I-10".
اما IP عنوان الهدف الذي سيتم إرسال الحزم إليه.

نظام (IPS - System Prevention Intrusion) :
هو نظام الوقاية من الاختراق في Snort هو عبارة عن وظيفة إضافية يمكن تكوينها ف Snort لتحويله من نظام كشف الاختراق (System Detection Intrusion IDS) إلى نظام يمكنه منع الهجمات أو تقليل تأثيراتها.

وضع inline يعني ان الحزم Packets تمر عبر snort بدال من تحويلها الى snort وفهذا الوضع يمكن snort اسقاط packets واحباط محاولات الاستغلال الوقت في الوقت الفعلي في هذا الوضع يعمل snort كنظام IPS.

ولتفعيل نظام inline في Snort

اذهب الى "snort/etc/"

وابحث عن ملف conf.snort" "وعدل على

                                                                                                     "Config daq: afpacket"

تأكد من حذف علامة "Config daq_mode:inline"

عندما يعمل Snort كنظام IPS، فإنه يقوم بتحليل الشبكة بناء على قواعد محددة مسبق. إذا تم اكتشاف هجوم محتمل أو سلوك غير مرغوب فيه، Snort يتخذ إجراءات فورية لمنع الهجوم أو تقليل تأثيراته.
