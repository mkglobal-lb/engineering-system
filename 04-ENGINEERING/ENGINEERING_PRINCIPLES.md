# Engineering Principles — مبادئ الهندسة

These are long-lived defaults, not rigid laws.

1. **Correctness before convenience.**  
   الصحة قبل السرعة والسهولة.

2. **Fix causes, not only symptoms.**  
   أصلح السبب الحقيقي، لا العرض فقط.

3. **Evidence over claims.**  
   الدليل أهم من "تم".

4. **Source of truth must be explicit.**  
   لا تخترع business rule من UI أو اسم متغير.

5. **Preserve working behavior intentionally.**  
   لا تغيّر behavior خارج المطلوب بلا سبب.

6. **Prefer the simplest design that satisfies real requirements.**  
   لا overengineering ولا premature architecture.

7. **Separate reversible from irreversible decisions.**  
   القرار القابل للرجوع ليس كالـ migration المدمّر.

8. **Data integrity is a product requirement.**  
   صحة البيانات ليست تفصيل backend.

9. **Authorization is resource/action-specific.**  
   كون المستخدم logged in لا يعني أنه مسموح له كل شيء.

10. **Automate repeatable checks when the value justifies it.**  
    لا تعتمد على الذاكرة في الأشياء المتكررة المهمة.

11. **Measure before performance optimization.**  
    PROFILE قبل optimization.

12. **Make failure modes explicit.**  
    فكر ماذا يحدث عند partial failure، retry، timeout، duplicate.

13. **Avoid duplicated business logic.**  
    القاعدة الأساسية يجب أن يكون لها canonical implementation/source.

14. **Documentation records durable knowledge, not code narration.**  
    وثّق القرارات والعقود والقواعد، لا كل سطر كود.

15. **Professional engineering is risk-based.**  
    لا تعامل typo مثل payment migration.
