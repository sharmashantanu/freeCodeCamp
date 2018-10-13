---
title: Python Integers
localeTitle: بايثون الاعداد الصحيحه
---
المجال النظري للأعداد الصحيحة في python هو إنفيني سلبي إلى ما لا نهاية. في الممارسة العملية ، يتم تحديد القيم الصحيحة بواسطة مقدار الذاكرة المتوفرة.

في Python 2 ، كان هناك تمييز بين **`int`** ، والأرقام التي تتناسب مع 32 أو 64 بت _C_ **`long`** ، وأرقام **`long`** محدودة بالذاكرة المتوفرة. بيثون 3 توحد بين نوعين في **`int`** فقط ، مزيد من المعلومات في [PEP 237](https://www.python.org/dev/peps/pep-0237/) .

**إنشاء `int` باستخدام حرفية عدد صحيح**

[عدد صحيح](https://docs.python.org/3/reference/lexical_analysis.html#integer-literals)

يمكن إنشاء _كائنات عدد صحيح_ باستخدام استخدام عدد صحيح من القيم الحرفية. الأرقام غير المزينة بدون الكسور العشرية هي عدد صحيح من القيم الحرفية:

 `>>> 1234567890           # Unadorned numbers are integer literals 
 1234567890 
 >>> type(1234567890) 
 <class 'int'> 
` 

لا تحتوي القيم الحرفية الرقمية على إشارة ، ولكن إنشاء _كائنات صحيحة_ سالبة ممكن عن طريق البدء بمعامِل وحيد `-` (ناقص) بدون فراغ قبل الحرفية:

 `>>> -1234567890 
 -1234567890 
 >>> type(-1234567890) 
 <class 'int'> 
` 

وبالمثل ، يمكن إنشاء كائنات صحيحة موجبة عن طريق بدء تشغيل عامل `+` (زائد) أحادي بدون فراغ قبل الأرقام. عادة ما يكون `+` هو:

 `>>> +1234 
 1234 
` 

يمكن إنشاء الأعداد الصحيحة ثنائية (قاعدة 2 ، البادئة: `0b` أو `0B` ) ، ثماني (قاعدة 8 ، البادئة: `0o` أو `0O` ) ، `0O` السداسية العشرية (الأساس 16 ، البادئة: `0x` أو `0X` ) باستخدام القيم الحرفية الصحيحة:

 `>>> 0b1, 0b10, 0b11 
 (1, 2, 3) 
 >>> 0o1, 0o10, 0o11 
 (1, 8, 9) 
 >>> 0x1, 0x10, 0x11 
 (1, 16, 17) 
` 

تجدر الإشارة إلى أنه **لا يُسمح بترك** 0 من القيم الحرفية الصحيحة غير الصفرية:

 `>>> 0     # Zero by itself is okay. 
 0 
 >>> 01    # Leading zero(s) cause SyntaxError. 
  File "<stdin>", line 1 
    01 
     ^ 
 SyntaxError: invalid token 
` 

[المنشئ](https://docs.python.org/3/library/functions.html#int) `int` طريقة أخرى لإنشاء _كائنات عدد صحيح_ .

 `class int(x=0) 
 class int(x, base=10) 
` 

يفضل إنشاء _كائنات صحيحة_ ذات قيم حرفية صحيحة عند الإمكان:

 `>>> a = 1         # Prefer integer literal when possible. 
 >>> type(a) 
 <class 'int'> 
 >>> b = int(1)    # Works but unnecessary. 
 >>> type(b) 
 <class 'int'> 
` 

ومع ذلك ، يسمح المُنشئ بإنشاء _كائنات صحيحة_ من أنواع الأعداد الأخرى:

 `>>> a = 1.123 
 >>> type(a) 
 <class 'float'> 
 >>> print(a) 
 1.123 
 >>> b = int(1.123) 
 >>> type(b) 
 <class 'int'> 
 >>> print(b) 
 1 
` 

باستخدام `int` المنشئ لأرقام النقطة العائمة سيتم اقتطاع الرقم باتجاه صفر:

 `>>> int(-1.23) 
 -1 
 >>> int(1.23) 
 1 
` 

الثوابت `boolean` المضمنة هي مثيلات من فئة `bool` ، وهي فئات فرعية لفئة `int` ، مما يجعلها نوعًا من النوع العددي:

 `>>> type(True) 
 <class 'bool'> 
 >>> issubclass(bool, int) 
 True 
` 

إذا كان ذلك غير منطقي بالنسبة لك ، فلا تقلق. الآن فقط تذكر أن استدعاء منشئ int مع كائنات `boolean` سيتم إرجاع _كائنات عدد صحيح_ :

 `>>> int(True) 
 1 
 >>> int(False) 
 0 
` 

سيقوم منشئ `int` أيضًا بإنشاء _كائنات صحيحة_ من السلاسل:

 `>>> a = "10" 
 >>> type(a) 
 <class 'str'> 
 >>> b = int("10") 
 >>> type(b) 
 <class 'int'> 
` 

يجب أن تمثل _سلاسل_ منشئ `int` عددًا صحيحًا حرفيًا:

المعلمة الثانية من `int` هي تحديد أساس (الافتراضي: 10). القواعد الصالحة هي 0 و236.

إذا تم توفير قاعدة صريحة يجب أن تكون الوسيطة الأولى عبارة عن سلسلة.

 `>>> int("111", 2) 
 7 
 >>> int(111, 2) 
 Traceback (most recent call last): 
  File "<stdin>", line 1, in <module> 
 TypeError: int() can't convert non-string with explicit base 
` 

يجب أن تكون السلسلة المستخدمة منشئ `int` مع قاعدة صريحة حاصية عدد صحيح صالحة لهذه القاعدة:

 `>>> int('11', 2) 
 3 
 >>> int('12', 2) 
 Traceback (most recent call last): 
  File "<stdin>", line 1, in <module> 
 ValueError: invalid literal for int() with base 2: '12' 
` 

يمكن استخدام كل من السلاسل البادئة وغير المسبوقة من القيم الحرفية الصحيحة ، في حالة استخدامها ، يجب أن تتطابق البادئة مع القاعدة المقدمة.

 `>>> int('1101', 2) 
 13 
 >>> int('0b1101', 2) 
 13 
 >>> int('0x1101', 2) 
 Traceback (most recent call last): 
  File "<stdin>", line 1, in <module> 
 ValueError: invalid literal for int() with base 2: '0x1101' 
` 

إذا تم استخدام سلسلة مسبوقة والبقاعدة 0 ، فسيستخدم الكائن الصحيح الذي تم إنشاؤه الأساس المحدد بواسطة البادئة. إذا لم يتم استخدام البادئة ، فسيتم افتراض الأساس 10

 `>>> int('100', 0) 
 100 
 >>> int('0b100', 0) 
 4 
 >>> int('0o100', 0) 
 64 
`