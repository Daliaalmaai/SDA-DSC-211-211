# بطاقة قرارك — Tamweel Lite

**الحالة:** جاهزة للمراجعة؛ لا تعني اعتمادًا أو درجة
**مصدر الأرقام:** LIVE · **الاستراتيجية:** weighted · **الصفوف:** 5,039 OOF

**المهمة:** الفئة الموجبة `default_within_90d=1` تعني حدث تعثر اصطناعي خلال90 يومًا بعد الطلب. كل طية تحقق طلبات لاحقة، وتستبعد عملاءها من التدريب وتشترط نضج نتيجة التدريب قبل بدايتها. المعرّفات والتاريخ خارج المدخلات.

| الدليل | القيمة |
|---|---:|
| العتبة المقيدة، بالقيمة الكاملة | 0.6583471436014694 |
| عتبة أقل خسارة دون قيد | 0.44863935722081005 |
| Recall | 40.89% |
| Precision | 29.85% |
| AP مجمع منOOF | 0.3100 |
| الإشارات | 526 من 5,039 |
| FN / FP | 227 / 369 |
| الخسارة التعليمية | 2639 وحدة |
| خسارة0.5 | 2403 وحدة؛ ضمن السعة: False |
| التغير عن0.5 | +236 وحدة؛ الموجب زيادة |
| خسارة لكل10,000 طلب، تطبيع حسابي | 5237.15 وحدة |
| فجوة معدل الإنذار الخاطئ بين المناطق | 0.648 نقطة مئوية |

**القاعدة:** درجة ≥ 0.6583471436014694 تعني إشارة مراجعة داخل التمرين؛ غير ذلك بلا إشارة. لا تتخذ موافقة أو رفض تمويل حقيقي. احفظ الدقة الكاملة؛ تقريب العتبة قد يغيّر حجم الطابور.

**السياسة:** FN=10 وFP=1 وحدات تعليمية، وسعة 12% لكل فترة بعد التقريب لأسفل. ليست ريالات فعلية أو رسوم أدوات أو خصمًا من الدرجة.

**دليل السعة:** الفترة 1: 137/195, الفترة 2: 183/200, الفترة 3: 206/207.

## لماذا اخترت هذه العتبة؟
I selected the threshold of approximately 0.6583 because it minimized observed OOF loss among thresholds satisfying the 12% review capacity in every validation period. It flagged 526 requests with a loss of 2639 educational units. The exact threshold is preserved in the export.

## الخسارة والسعة
At threshold 0.5, the model flagged 1005 requests with loss 2403, but exceeded capacity. The constrained threshold reduced flags to 526 while increasing loss by 236 units and reducing recall from 57.81% to 40.89%. Period flags were 137/195, 183/200 and 206/207 of capacity. The displayed threshold and flag count remained unchanged for FN costs of 8, 10 and 12, with FP cost fixed at 1.

## فرق المناطق وما يحتاج إلى مراجعة
Regional false-positive rates were approximately 8.09% for central, 8.29% for western, 7.72% for eastern and 7.64% for other. The maximum-minus-minimum gap was approximately 0.648 percentage points. All regions exceeded the low-support cutoff. These descriptive results require review of group outcomes and denominators; the small gap does not establish fairness or statistical significance.

## حدود النتيجة
The data are synthetic. Threshold selection and loss estimation use the same development OOF labels, so this is not an independent final test. OOF covers 5039 requests, representing 50.39% of all training rows and 100% of eligible rows; 4961 warm-up rows have no OOF predictions. Weighted scores are not established as calibrated probabilities. The simplified loss policy omits review cost and effectiveness. Historical capacity compliance and unchanged decisions in the tested cost scenarios do not guarantee future performance or capacity.

OOF تغطي 50.39% من التدريب و100% من الصفوف المؤهلة؛ 4,961 صفًا تمهيديًا بلا تنبؤ. اختيار العتبة وتقدير خسارتها هنا يستخدمان أهدافOOF نفسها؛ هذه نتيجة تطوير لا اختبار نهائي. لم نستخدم التحدي. المقارنة الجغرافية وصفية وليست شهادة عدالة، والأوزان لا تضمن معايرة الدرجات.

## سؤالك الأول: لماذا قد تخدعكAccuracy؟
Only approximately 7.62% of the eligible requests defaulted. Flagging nobody achieved 92.38% accuracy but zero recall, missing all 384 defaults and producing loss of 3840 units. Accuracy alone therefore hides failure to identify the minority class. I also consider AP, recall, precision, loss and capacity.

## سؤالك الثاني: لماذا تختار علىOOF؟
Each OOF score comes from a model that did not train on that request. The forward folds also exclude validation customers from training and require training labels to mature before validation begins. This reduces leakage and training optimism. Challenge data remain closed. However, choosing the threshold using OOF labels still makes these development results rather than an independent final evaluation.

أدلتك في `artifacts/threshold_metrics.json` و`day3_period_capacity.csv` و`day3_region_audit.csv` و`day3_cost_sensitivity.csv` و`cost_curve.png`. الحساسية سيناريوهات ±20% لخسارةFN، وليست فترات ثقة. راجع السعة والمعايرة عند تغير البيانات؛ لا تفترض ثباتهما مستقبلًا.
