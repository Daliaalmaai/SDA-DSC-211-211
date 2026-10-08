# Tamweel Lite | مشروعك النهائي

## الملخص التنفيذي
اخترت Logistic Regression مفرداً بمتوسط AP=0.39166 عبر ثلاث طيات أمامية؛ لم يجتز أي تجميع بوابة الجدوى. ثبتُّ النموذج ومعايرة sigmoid وعتبة 0.12225843144286948، وصدرت 2500 تنبؤ مع 300 إشارة مراجعة تعليمية. المعايرة لم تحسن مقاييس عينة تعلمها، والتحدي غير موسوم، فلا أدعي أداءه أو عدالته. صيغ هذا التفسير بمساعدة Codex ويحتاج مراجعة المتدربة وفهمها.

## Executive summary
KEEP SINGLE: Logistic Regression achieved mean forward-fold AP 0.39166 (SD 0.02981). No ensemble passed the predefined gate. The frozen model and sigmoid mapping scored all 2500 challenge requests, with 300 simulated review flags after one full-batch 12% cap. Calibration-fit Brier and ECE worsened, so improvement is not claimed. Challenge labels are unavailable. Codex assisted with this draft; learner review and understanding remain required.

Decision: KEEP SINGLE / Logistic. Full-batch flags: 300/2500.

اقرأ reports/MODEL_CARD.md والسياسة في artifacts/final_policy.json. الحزمة للتدريب؛ ليست نتيجة تقييم نهائية أو إثبات تسليم. ادمج أدلة أيامك السابقة واحفظ الدفتر المنفذ والعرض.
