# Inheritance
في هذا الدرس ان شاءالله راح نتعلم على واحد من أهم المفاهيم  في البرمجة كائنية التوجه او الـ object oriented programming  وهو مفهوم اinheratance او الوراثة

# المفهوم | Concept

الوراثة تعني inheritance وفي البرمجة تعني أن ترث صفات وأفعال من class محدد. 
مفهوم الوراثة يتيح لك أن تعيد استخدام class بدون أن تعيد انشائه من الصفر
ملاحظة: يرث class من class واحد وايضاً يمكن  أن يورّث Class  اكثر من class ويسمى أول class في التسلسل الوراثي base class او super Class

![Derived Class (child) -  هو class  parent اللذي يرث من الـ  Base Class (parent) - هو class اللذي يورث](https://paper-attachments.dropbox.com/s_8E9EF3802D29B5FF299CEA84504B6FE1923FFBF6EEF82F33958CACEAF581152F_1626188552487_Capture2.PNG)



لاحظ في الرسمة التالية بأن class B يرث من class A, وكل من class C و class D يرثان من class B


![User-uploaded image: Screen+Shot+1442-09-13+at+2.13.08+PM.png](https://paper-attachments.dropbox.com/s_6DB43611255FEB5D95F3A3AFA097D69F41EE068F9FA63453E2854A824FC3CB17_1619349200698_Screen+Shot+1442-09-13+at+2.13.08+PM.png)


ملاحظة جانبية: يسمى أول class في التسلسل الهرمي للوراثة superClass وتسمى class المتفرعة sub class


**نقاط مهمة:** 

- عند عمل الوراثه يتم وراثة من superClass جميع الخصائص والدوال ما عدا دالة البناء constructor الخاصه في superClass.
- لا تدعم Dart أيضًا الوراثة المتعددة.
- يتم استخدام كلمة extends لعمل الوراثه 

لناخذ مثال يوضح فكرة الوراثه في لغة dart :


    class Human {
      String name;
      int yearOfBirth;
      Human(this.name, this.yearOfBirth);
      displayInfo() {
        print("Name: $name");
        print("Year of birth is $yearOfBirth");
      }
    }
    void main() {
      Human object1 = Human("Fahad", 1994);
      object1.displayInfo();
    }

المخرجات :

    Name: Fahad
    Year of birth is 1994

في المثال في الاعلى نلاحظ انه يوجد Class باسم Human فيه بعض الخصائص والدوال بداخله هي موجوده في كل انسان 

لو اردنا انشاء Class اخر خاص في الطلاب يرث من Class Human  لان الصفات التي يحملها الطالب موجوده في Class Human فكل طالب لديه اسم وايضا لديه سنة ميلاد سوف يتم بالشكل التالي :


     class Human {
      String name;
      int yearOfBirth;
      Human(this.name, this.yearOfBirth);
      displayInfo() {
        print("Name: $name");
        print("Year of birth is $yearOfBirth");
      }
    }
    class Person extends Human{
      
    }
    void main() {
      Human object1 = Human("Fahad", 1994);
      object1.displayInfo();
    }

نلاحظ تم انشاء Class  باسم Person واضافة extends ثم اسم Class الذي سوف يتم عمل الوراثه منه وهو Human

بهذا الشكل سوف نجد ان الكلاس Person  يشير الى ان هناك خطاء في هذه الحاله لان Class الذي يرث منه وهو Class Human  لديه دالة بناء تطلب بعض المدخلات وهي الاسم وتاريخ الميلاد فيتم اسناد دالة بناء باسم Class يتم اعطائها القيم الذي يطلبها كلاس الاب (Class Human) ويتم بستخدام كلمة super للاشاره للمتغيرات الموجوده في Class الاب  كما في الشكل التالي :

      Person(super.name, super.birthday);

سوف يصبح الكود بهذا الشكل :


    class Human {
      String name;
      int birthday;
      Human(this.name, this.birthday);
      displayInfo() {
        print("Name: $name");
        print("Date of birth is $birthday");
      }
    }
    class Person extends Human{
      Person(super.name, super.birthday);
    }
    void main() {
      Human object1 = Human("Fahad", 1994);
      object1.displayInfo();
    }
    

الان اصبح  Class Person يرث من Class Human  جميع الخصائص والدوال ولو تم انشاء اوبجكت من Class Person نستطيع الوصول الى جميع محتويات الموجوده في Class Human كما في المثال التالي :


     class Human {
      String name;
      int birthday;
      Human(this.name, this.birthday);
      displayInfo() {
        print("Name: $name");
        print("Date of birth is $birthday");
      }
    }
    class Person extends Human {
      Person(super.name, super.birthday);
    }
    void main() {
      Person object = Person("Saleh", 1994);
      print(object.name);
      object.displayInfo();
    }

المخرجات :


    Saleh
    Name: Saleh
    Date of birth is 1994



## **مفهوم Overriding :** 

عند استخدام الوراثة ،اذا كنا نريد استخدام دالة موجودة في superclass ولكن نحتاج لتعديل على هذه الدالة للتوافق مع مانحتاجة، من الممكن ان نستدعي الداله  ولكن نغير فعلها في subclass يسمى هذا المفهوم override 
قبل البدء في مثال ، هناك ثلاث قواعد يجب اتباعها عند استخدام override . 

- أولاً ، يجب أن تأخذ الدالة بنفس عدد المدخلات في الدالة الموجودة في superclass ,
- ثانيًا ، يجب أن يكون لدالة الجديدة نفس نوع الإرجاع مثل الدالة الأصلية. 


في  Human class لدينا ، لدينا دالة تسمى displayInfo والتي تعرض اسم الحساب وسنة الميلاد . في  Person class الخاصة بنا ، قد نرغب أيضًا في طباعةالتفاصيل بطريقه مختلفه. لتحقيق ذلك ، نعلن ببساطة عن إصدار جديد من دالة  displayInfo في Human  الخاصة بنا ، مسبوقة بالكلمة الأساسية override:


    class Human {
      String name;
      int birthday;
      Human(this.name, this.birthday);
      displayInfo() {
        print("Name: $name");
        print("Date of birth is $birthday");
      }
    }
    class Student extends Human {
      Student(super.name, super.birthday);
      @override
      displayInfo() {
        print("my name is ${super.name} and my Date of birth is ${super.birthday}");
      }
    }
    void main() {
      Student object = Student("Saleh", 1994);
      print(object.name);
      object.displayInfo();
    }
    

ولكن قبل استخدام دالة displayInfo داخل Person class  يفضل علينا استخدام @override قبل الداله : 

المخرجات :

    Saleh
    my name is Saleh and my Date of birth is 1994

في المثال اعلاه تم استخدام الدالةdisplayInfo في subclass مع إضافة بعض التعديلات . 

