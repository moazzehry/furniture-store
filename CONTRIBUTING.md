# دليل المساهمة في مشروع Furni Store

نرحب بمساهماتكم في تطوير متجر الأثاث! هذا الدليل سيساعدكم على فهم كيفية المساهمة بشكل فعال.

## 📋 جدول المحتويات

- [كيفية المساهمة](#كيفية-المساهمة)
- [الإبلاغ عن الأخطاء](#الإبلاغ-عن-الأخطاء)
- [اقتراح الميزات](#اقتراح-الميزات)
- [إرشادات التطوير](#إرشادات-التطوير)
- [معايير الكود](#معايير-الكود)
- [عملية المراجعة](#عملية-المراجعة)

## 🤝 كيفية المساهمة

### 1. Fork المشروع
```bash
# انقر على زر Fork في GitHub
# ثم استنسخ المشروع المنسوخ
git clone https://github.com/your-username/furni-store.git
cd furni-store
```

### 2. إعداد البيئة المحلية
```bash
# استعادة الحزم
dotnet restore

# تشغيل قاعدة البيانات
dotnet ef database update --project E-LapShop

# تشغيل التطبيق
dotnet run --project E-LapShop
```

### 3. إنشاء Branch جديد
```bash
# إنشاء branch للميزة الجديدة
git checkout -b feature/your-feature-name

# أو للإصلاح
git checkout -b fix/bug-description
```

### 4. تطوير التحسينات
- اكتب كود واضح ومفهوم
- اتبع معايير الكود المحددة
- أضف تعليقات مناسبة
- اكتب اختبارات للكود الجديد

### 5. اختبار التغييرات
```bash
# تشغيل الاختبارات
dotnet test

# تشغيل التطبيق للاختبار اليدوي
dotnet run --project E-LapShop
```

### 6. إرسال Pull Request
```bash
# رفع التغييرات
git add .
git commit -m "Add: وصف واضح للتغيير"
git push origin feature/your-feature-name

# ثم أنشئ Pull Request في GitHub
```

## 🐛 الإبلاغ عن الأخطاء

عند الإبلاغ عن خطأ، يرجى تضمين:

### معلومات البيئة
- نظام التشغيل
- إصدار .NET
- إصدار المتصفح
- إصدار SQL Server

### وصف المشكلة
- وصف واضح للمشكلة
- خطوات إعادة إنتاج المشكلة
- السلوك المتوقع مقابل السلوك الفعلي
- لقطات شاشة إذا أمكن

### مثال على تقرير خطأ
```markdown
**وصف المشكلة**
عربة التسوق لا تحفظ المنتجات بعد تسجيل الخروج

**خطوات إعادة الإنتاج**
1. أضف منتج إلى العربة
2. سجل خروج من الحساب
3. سجل دخول مرة أخرى
4. تحقق من العربة

**السلوك المتوقع**
يجب أن تظهر المنتجات في العربة

**السلوك الفعلي**
العربة فارغة

**البيئة**
- OS: Windows 11
- .NET: 8.0
- Browser: Chrome 120
```

## 💡 اقتراح الميزات

لاقتراح ميزة جديدة:

1. **تحقق من الميزات الموجودة** في Issues
2. **اكتب وصف مفصل** للميزة المقترحة
3. **اشرح الفائدة** من هذه الميزة
4. **قدم أمثلة** على كيفية استخدامها

### مثال على اقتراح ميزة
```markdown
**عنوان الميزة**
إضافة نظام التقييمات للمنتجات

**الوصف**
السماح للعملاء بتقييم المنتجات من 1-5 نجوم وكتابة مراجعات

**الفائدة**
- مساعدة العملاء في اتخاذ قرارات الشراء
- تحسين ثقة العملاء في المنتجات
- تقديم تغذية راجعة للإدارة

**التفاصيل التقنية**
- جدول Reviews في قاعدة البيانات
- واجهة لعرض التقييمات
- نظام منع التقييمات المكررة
```

## 🛠️ إرشادات التطوير

### هيكل المشروع
```
E-Store/
├── DAL/                 # طبقة الوصول للبيانات
├── BLL/                 # طبقة منطق الأعمال
├── E-LapShop/          # طبقة العرض
└── Tests/              # الاختبارات
```

### أنواع المساهمات المرحب بها
- ✅ إصلاح الأخطاء
- ✅ تحسين الأداء
- ✅ إضافة ميزات جديدة
- ✅ تحسين الوثائق
- ✅ كتابة الاختبارات
- ✅ تحسين واجهة المستخدم

### أنواع المساهمات غير المرغوبة
- ❌ تغييرات كبيرة بدون مناقشة
- ❌ كود غير مختبر
- ❌ تغييرات تكسر الوظائف الموجودة
- ❌ كود غير موثق

## 📝 معايير الكود

### C# Guidelines
```csharp
// استخدم PascalCase للكلاسات والميثودز
public class ProductService
{
    public async Task<Product> GetProductAsync(int id)
    {
        // استخدم camelCase للمتغيرات المحلية
        var product = await _repository.GetByIdAsync(id);
        return product;
    }
}

// أضف تعليقات للميثودز المعقدة
/// <summary>
/// حساب السعر النهائي مع الخصم والضريبة
/// </summary>
/// <param name="basePrice">السعر الأساسي</param>
/// <param name="discountPercent">نسبة الخصم</param>
/// <returns>السعر النهائي</returns>
public decimal CalculateFinalPrice(decimal basePrice, decimal discountPercent)
{
    // Implementation
}
```

### HTML/CSS Guidelines
```html
<!-- استخدم semantic HTML -->
<section class="products-section">
    <h2 class="section-title">المنتجات المميزة</h2>
    <div class="products-grid">
        <!-- المحتوى -->
    </div>
</section>

<!-- استخدم classes واضحة -->
<button class="btn btn-primary add-to-cart-btn">
    إضافة للعربة
</button>
```

### JavaScript Guidelines
```javascript
// استخدم const/let بدلاً من var
const addToCart = async (productId) => {
    try {
        const response = await fetch('/Cart/Add', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({ productId })
        });
        
        if (response.ok) {
            showSuccessMessage('تم إضافة المنتج للعربة');
        }
    } catch (error) {
        showErrorMessage('حدث خطأ أثناء إضافة المنتج');
    }
};
```

### قواعد التسمية
- **Controllers**: `ProductController`, `CartController`
- **Services**: `ProductService`, `OrderService`
- **Models**: `Product`, `Order`, `CartItem`
- **DTOs**: `ProductCreateDto`, `OrderReadDto`
- **Views**: `Index.cshtml`, `Create.cshtml`

## 🔍 عملية المراجعة

### معايير قبول Pull Request
1. **الكود يعمل** بدون أخطاء
2. **الاختبارات تمر** جميعها
3. **الكود موثق** بشكل مناسب
4. **يتبع معايير الكود** المحددة
5. **لا يكسر الوظائف الموجودة**

### خطوات المراجعة
1. **مراجعة تلقائية** - CI/CD checks
2. **مراجعة الكود** - Code review
3. **اختبار الوظائف** - Functional testing
4. **مراجعة الأداء** - Performance review
5. **الموافقة والدمج** - Approval & merge

### نصائح للمراجعة السريعة
- اكتب وصف واضح للـ PR
- قسم التغييرات الكبيرة لعدة PRs صغيرة
- أضف screenshots للتغييرات في UI
- اربط PR بـ Issue ذو صلة

## 🎯 أولويات التطوير

### أولوية عالية
- إصلاح الأخطاء الأمنية
- إصلاح الأخطاء الحرجة
- تحسين الأداء

### أولوية متوسطة
- ميزات جديدة مطلوبة
- تحسين واجهة المستخدم
- تحسين الوثائق

### أولوية منخفضة
- تحسينات تجميلية
- إعادة هيكلة الكود
- ميزات اختيارية

## 📞 التواصل

### قنوات التواصل
- **GitHub Issues** - للأخطاء والاقتراحات
- **GitHub Discussions** - للنقاشات العامة
- **Email** - support@furnistore.com

### آداب التواصل
- كن محترماً ومهذباً
- استخدم لغة واضحة ومفهومة
- قدم معلومات كافية
- اشكر المساهمين الآخرين

## 🏆 الاعتراف بالمساهمين

جميع المساهمين سيتم إدراجهم في:
- ملف CONTRIBUTORS.md
- صفحة About في التطبيق
- Release notes

## 📚 موارد مفيدة

### الوثائق
- [ASP.NET Core Documentation](https://docs.microsoft.com/en-us/aspnet/core/)
- [Entity Framework Core](https://docs.microsoft.com/en-us/ef/core/)
- [Bootstrap Documentation](https://getbootstrap.com/docs/)

### الأدوات
- [Visual Studio](https://visualstudio.microsoft.com/)
- [VS Code](https://code.visualstudio.com/)
- [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/)

---

**شكراً لمساهمتكم في تطوير متجر الأثاث! 🙏**

كل مساهمة، مهما كانت صغيرة، تساعد في جعل المشروع أفضل للجميع.
