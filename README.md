# Static Keyword


تعتبر كلمة مفتاحية مشهورة جداً في لغة البرمجه ومن ضمنهم لغة Dart، هذه الكلمة تُستخدم بكثرة في لغة Dart في أوساط المبتدئين و المحترفين على حد سواء. و لكن الإستخدامات الخاطئة لمفهوم static كثيرة جداً و مشهورة. ربما يرجع ذلك لقلة المعرفة عن أهمية الكلمة static و لماذا تستخدم، لذى سوف نتعرف على مفهوم Static Keyword


تؤدي Static Keyword مهمة رائعة جداً فيما يتعلق بالذاكرة، فهي تساعد المبرمج على إنشاء نظام فعال في إستخدام الذاكرة، أي يقلل من إستخدام الذاكرة. و ذلك لأن كل متغير أو دالة أو غيره تم تعريفه بأنه static فذلك يعني أن هذا المتغير سيتم حجز مكانه في الذاكرة لمرة واحدة فقط.
كما هو من المهم جداً أن تعرف أن المتغيرات و الدوال التي يتم تعريفها على انها static هي تتبع الى class نفسه و ليس الى object. و هذا يعني أن كل متغير عرّفتهُ بأنه static فبإمكانك الوصول إليه دون أن تُنشئ object عن طريق class.

استخدم هذا Syntax للانشاء

     static kind name = value;

استخدم هذا Syntax للاستدعاء 

    classname.StaticElementName;

لتتضح الصوره سوف نلاحظ في المثال التالي تم أنشاء Class كما تعلمنا في الدروس السابقه يحتوي على بعض attributes وبعض Methods 



     class BankAccount {
        String accountName = "";
        num accountBalance = 0.0;
        int accountNumber = 0;
       BankAccount(this.accountName,this.accountBalance,this.accountNumber);
    
        displayBalance()
        {
           print("Name: $accountName");
           print("Current balance is $accountBalance");
        }
    }

في Class الذي تم إنشاء في الاعلى سوف يتم انشاء منه اكثر من Object ونريد تعريف متغير للاشاره على اسم البنك لذى سوف نظيف اسم `static String nameBank`


     class BankAccount {
     static String nameBank = "Tuwaiq Bank";
        String accountName = "";
        num accountBalance = 0.0;
        int accountNumber = 0;
       BankAccount(this.accountName,this.accountBalance,this.accountNumber);
      
       
        displayBalance()
        {
           print("Name: $accountName");
           print("Current balance is $accountBalance");
        }
    }

ويتم الاشاره على ان هذا المتغير هو خاص في Class لا يتم التعامل معه وقت انشاء Object لذى لو ادنا طباعة الاسم الخاص في البنك الموجود داخل Class سوف يتم كتابة اسم Class مع اسم المتغير الذي تم كتابة Static قبله كما في الشكل التالي :


     class BankAccount {
     static String nameBank = "Tuwaiq Bank";
        String accountName = "";
        num accountBalance = 0.0;
        int accountNumber = 0;
       BankAccount(this.accountName,this.accountBalance,this.accountNumber);
      
       
        displayBalance()
        {
           print("Name: $accountName");
           print("Current balance is $accountBalance");
        }
    }
    
    void main(){
      
      BankAccount ob1 = BankAccount("Fahad",14.58,1);
      BankAccount ob2 = BankAccount("Saleh",41.5,2);
      print(BankAccount.nameBank);
    }


نلاحظ إنشائنا اكثر من Object لاكن عندما اردنا معرفة اسم البنك تم استدعاء المتغير nameBank مع اسم Class
 
 المخرجات:
 

     Tuwaiq Bank


ملاحظه: لا يتم الوصول للمتغير  من نوع Static عن طريق Object 




## إجراء تغييرات على متغير static

لتحديث المتغير الذي تم تعريفه static امر بسيط ويتم كما يتم تغير اي قيمه خاصه في متغير اخرى عادي 

لناخذ المثال السابق كما التالي :


     class BankAccount {
     static String nameBank = "Tuwaiq Bank";
        String accountName = "";
        num accountBalance = 0.0;
        int accountNumber = 0;
       BankAccount(this.accountName,this.accountBalance,this.accountNumber);
      
       
        displayBalance()
        {
           print("Name: $accountName");
           print("Current balance is $accountBalance");
        }
    }
    
    void main(){
      
      BankAccount ob1 = BankAccount("Fahad",14.58,1);
      BankAccount ob2 = BankAccount("Saleh",41.5,2);
      print(BankAccount.nameBank);
    }

لو اردنا تحديث قيمة nameBank الى  `Tuwaiq acadimacy Bank`   سوف يتم بالشكل التالي :


     
     class BankAccount {
     static String nameBank = "Tuwaiq Bank";
        String accountName = "";
        num accountBalance = 0.0;
        int accountNumber = 0;
       BankAccount(this.accountName,this.accountBalance,this.accountNumber);
      
       
        displayBalance()
        {
           print("Name: $accountName");
           print("Current balance is $accountBalance");
        }
    }
    
    void main(){
      
      BankAccount ob1 = BankAccount("Fahad",14.58,1);
      BankAccount ob2 = BankAccount("Saleh",41.5,2);
      
      BankAccount.nameBank = "Tuwaiq acadimacy Bank";
      print(BankAccount.nameBank);
    }

المخرجات:

    Tuwaiq acadimacy Bank

في المخرجات تم تحديث القيمه بستخدام عملية الاسناد وسناد قيمة جديده للمتغير عن طريق استدعاء اسم Class ثم اسم المتغير Static  وعطائه القيمه الجديده ثم طباعتها 



## إنشاء Methods من نوع static

لا يختلف الامر كثيرا في انشاء Methods عباره عن  Static Method فهو نفس الفكره والمفهوم ولا كن فقط يتم تطبيقه على الدوال  في حال اردنا انشاء داله يتم اتسخدامها على مستوى الكلاس  وليس عن طريق الاوبجكت 

استخدم هذا Syntax للانشاء

     static nameMethod(){
    }

استخدم هذا Syntax للاستدعاء 

      nameClass.nameMethod();

لناخذ مثال لتوضيح الفكره 
كما في الامثله السابقه تعلمنا انشاء كلاس خاص في البنك ونشائنا static خاص في اسم البنك لو ادنا انشاء رساله ترحيبيه خاصه في البنك فاحتاج انشاء ميثود خاص في هذه الرساله تكون من نوع static كما في التالي :

    
     class BankAccount {
     static String nameBank = "Tuwaiq Bank";
        String accountName = "";
        num accountBalance = 0.0;
        int accountNumber = 0;
       BankAccount(this.accountName,this.accountBalance,this.accountNumber);
      
       
        displayBalance()
        {
           print("Name: $accountName");
           print("Current balance is $accountBalance");
        }
       
       static displayMsg()
        {
           print("Welcome to the application example of Tuwaiq Bank");
        }
    }
    
    void main(){
      
      BankAccount ob1 = BankAccount("Fahad",14.58,1);
      BankAccount ob2 = BankAccount("Saleh",41.5,2);
      
      BankAccount.nameBank = "Tuwaiq acadimacy Bank";
      print(BankAccount.nameBank);
    
    }

ويتم استدعاء الداله بشكل التالي :

    
     class BankAccount {
     static String nameBank = "Tuwaiq Bank";
        String accountName = "";
        num accountBalance = 0.0;
        int accountNumber = 0;
       BankAccount(this.accountName,this.accountBalance,this.accountNumber);
      
       
        displayBalance()
        {
           print("Name: $accountName");
           print("Current balance is $accountBalance");
        }
       
       static displayMsg()
        {
           print("Welcome to the application example of Tuwaiq Bank");
        }
    }
    
    void main(){
      
      BankAccount ob1 = BankAccount("Fahad",14.58,1);
      BankAccount ob2 = BankAccount("Saleh",41.5,2);
      
      BankAccount.nameBank = "Tuwaiq acadimacy Bank";
      print(BankAccount.nameBank);
      BankAccount.displayMsg();
    }

المخرجات سوف تكون :


    Tuwaiq acadimacy Bank
    Welcome to the application example of Tuwaiq Bank

وبهذا الشكل تم انشاء داله من نوع static 


أنقلك الآن إلى الإستخدامات المُفيدة جداً لمفهوم static و التي من أجلها وجدت static، هذه الإستخدامات يجب أن تعرفها. فمثل هذه الإستخدامات هي ما يصنع الفارق في كتابة الاكواد.
‌

1. **إستخدم static لتعريف المتغيرات غير القابلة للتغيير منطقياً**
2. كثيراً ما تجدا متغيرات محددة القيمة داخل Class ومعرفة و لكنها غير معرفة بـ static وفي نفس الوقت قيمتها لن تتغير اطلاقاً طوال حياة البرنامج.  فلماذا لا تجعلهُ مشتركاً و توفر المساحة بالذاكرة و تُظهر احترافيتك.‌
3. **إستخدم static مع الدوال التي من المنطقي إستخدامها قبل إنشاء object**
4. إذا أردت أن تنشئ class لسيارة، فمن الدوال التي يجب أن تضعها static مثلاً الدالة التي تغير وحدات قياس السرعة بين كيلومتر و ميل. فهذه الدالة قد تستخدمها بدون إنشاء الـ class لإجراء أي تغيير، و حتى بدون أن تمتلك سيارة بمعنى آخر، أما الدوال مثل سرعة السيارة الحالية فيجب أن لا تعرف كـ static لأنها متعلقة بكل سيارة لوحدها.‌
5. **لإجراء تغييرات على متغير static، أنشئ دالة static**
6. ليس دائماً، و لكن الشرط هو أن تكون لديك عمليات معقدة تجريها على متغير static، ففي هذه الحالة أنشئ دالة من النوع static حتى تستطيع أن تستدعيها دون أن تنشئ object، فالمتغير الـ static بالإمكان تغييره و إسناد قيمة له و تعديلها دون أن ينشأ أي object.‌
7. **إستخدم static مع المتغيرات المُشتركة بين الـ objects**
8. إبحث دائماً عنن المتغيرات المشتركة بين الـ objects، هذه المتغيرات إذا ما تغير في أحد الـ classes  سوف تتغير في البقية،عند تعريفك لـ class يخص طالب في جامعة، فمن المتغيرات التي يجب أن تعرف بـ static إسم الجامعة و تاريخ إنشاءها، لماذا؟ هذه المتغيرات غير قابلة للتغيير على مستوى الطلاب، فإذا أنشأت عدة objects فلن يتغير إسم الجامعة، أليس كذلك؟ و هنا تأتي فائدة static بأنه مهما كان عدد الـ objects تبقى المساحة المحجوزة للمتغير الخاص بإسم الجامعة واحدة، و لكن المتغيرات مثل إسم الطالب و عمره يتم إنشاءها مع كل object لوحده.‌
9. **إستخدم static مع الدوال غير المتعلقة بالـ object**
10. توجد بعض الدوال التي لا تتعلق بالـ object الذي سيتم إنشاؤه، و لكن يتم إنشاؤها كدوال مساعدة، ليس بالضرورة أن تكون هذه الدوال من النوع  الذي يُستدعى قبل إنشاء الـ object كما ذكرتُ لك سابقاً، بل أي دالة مساعدة غير متعلقة بالـ object إجعلها static لتوفر بعض المساحة بالذاكرة.

هذه 5 أفكار و استخدامات لـ static لتعتمدها أو لتتبناها في طريقة تفكيرك عند إنشاء أي برنامج، و ضمنياً توضح هذه الإستخدامات فوائد و أسباب وجود static في لغة الجافا، إذا أعجبت الأفكار إضغط على  و اكتب إنطباعك عن هذه الأفكار.

