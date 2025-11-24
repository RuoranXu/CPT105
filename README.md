## CPT105 Java 编程期末复习资料 (知识点 + 代码示例)

这份资料旨在帮助你系统地复习 CPT105 Java 编程课程的核心知识点，并提供相应的代码示例，以便于理解和实践。

---

### 第一部分：Java 基础语法与控制流

#### 1. 变量与数据类型

*   **基本数据类型**: `byte`, `short`, `int`, `long`, `float`, `double`, `boolean`, `char`
*   **引用数据类型**: `String`, 数组, 对象 (类)
*   **类型转换 (Casting)**:
    *   **自动类型提升**: 小类型到大类型 (如 `int` 到 `double`)，不需要显式声明。
    *   **强制类型转换**: 大类型到小类型 (如 `double` 到 `int`)，需要显式声明，可能会丢失精度。

**代码示例**:

```java
// 变量声明与初始化
int age = 25;
double salary = 50000.50;
boolean isActive = true;
char grade = 'A';

// 自动类型提升
int count = 10;
double total = count * 1.5; // count (int) 自动提升为 double

// 强制类型转换
double price = 99.99;
int wholePrice = (int) price; // 丢失小数部分，wholePrice = 99

// char 示例
char initial = 'J';
char numberChar = '5'; // 字符 '5'
char unicodeChar = '\u2764'; // Unicode 心形符号 ❤
System.out.println("Unicode heart: " + unicodeChar);
```

#### 2. 控制流：条件语句

*   **`if` 语句**: 根据布尔表达式的值来决定是否执行代码块。
*   **`if-else` 语句**: 根据布尔表达式的值，选择执行两个代码块中的一个。
*   **`if-else if-else` 链**: 处理多个条件分支。
*   **嵌套 `if` 语句**: 在 `if` 语句的代码块内包含另一个 `if` 语句。
*   **条件运算符 `? :` (三元运算符)**: 简洁的 `if-else` 表达。

**代码示例**:

```java
// if 语句
int score = 75;
if (score >= 60) {
    System.out.println("Passed!");
}

// if-else 语句
int temperature = 15;
if (temperature > 25) {
    System.out.println("Hot weather.");
} else {
    System.out.println("Moderate weather.");
}

// if-else if-else 链 (等级评定)
int percentage = 85;
String degreeClass;
if (percentage >= 70) {
    degreeClass = "First Class";
} else if (percentage >= 60) {
    degreeClass = "Upper Second Class";
} else if (percentage >= 50) {
    degreeClass = "Lower Second Class";
} else if (percentage >= 40) {
    degreeClass = "Third Class";
} else {
    degreeClass = "Fail";
}
System.out.println("Degree Class: " + degreeClass);

// 条件运算符
int x = 10, y = 20;
int max = (x > y) ? x : y; // 如果 x > y，max 为 x，否则为 y
System.out.println("Maximum is: " + max);
```

#### 3. 控制流：循环语句

*   **`while` 循环**: 当布尔表达式为 `true` 时，重复执行代码块。需要手动更新条件变量，以避免无限循环。
*   **`do-while` 循环**: 至少执行一次代码块，然后根据布尔表达式的值决定是否继续循环。
*   **`for` 循环**: 适用于已知循环次数的情况，包含初始化、条件判断和更新三个部分。
*   **嵌套 `for` 循环**: 在一个 `for` 循环内部嵌套另一个 `for` 循环，常用于处理二维数据结构或打印模式。
*   **增强型 `for` 循环 (for-each)**: 简化对数组或集合元素的遍历。
*   **无限循环**: 当循环条件永远为 `true` 时发生，需要谨慎使用或在内部通过 `break` 退出。
*   **逻辑错误**: "差一错误" (off-by-one bug)，循环次数多或少一次。

**代码示例**:

```java
// while 循环 (倒计时)
int count = 5;
while (count > 0) {
    System.out.println(count + "...");
    count--; // 更新条件变量
}
System.out.println("Liftoff!");

// do-while 循环 (至少执行一次)
int diceRoll;
do {
    diceRoll = (int)(Math.random() * 6) + 1; // 模拟掷骰子
    System.out.println("Rolled: " + diceRoll);
} while (diceRoll != 6);
System.out.println("You rolled a 6!");

// for 循环 (打印 1 到 10)
for (int i = 1; i <= 10; i++) {
    System.out.print(i + " ");
}
System.out.println();

// 嵌套 for 循环 (打印星形金字塔)
int rows = 5;
for (int i = 1; i <= rows; i++) { // 控制行
    for (int j = 1; j <= rows - i; j++) { // 打印空格
        System.out.print(" ");
    }
    for (int k = 1; k <= 2 * i - 1; k++) { // 打印星号
        System.out.print("*");
    }
    System.out.println(); // 换行
}

// 增强型 for 循环 (遍历数组)
int[] numbers = {10, 20, 30, 40, 50};
for (int num : numbers) {
    System.out.println(num);
}

// 无限循环 (需要 break 退出)
int counter = 0;
while (true) {
    System.out.println("Looping...");
    counter++;
    if (counter > 3) {
        break; // 退出循环
    }
}
```

#### 4. 数组

*   **定义与创建**: 声明数组变量，并使用 `new` 关键字创建数组对象。
*   **初始化**:
    *   声明时直接初始化 `{}`。
    *   `new` 关键字后指定大小，元素会被默认初始化（数值为 0，`boolean` 为 `false`）。
*   **访问**: 使用索引（从 0 开始）访问数组元素，如 `array[index]`。
*   **长度**: 通过 `array.length` 获取数组长度（注意不是方法调用）。
*   **多维数组**: 如二维数组 `int[][] matrix = new int[rows][cols];`，用于表示表格或矩阵。

**代码示例**:

```java
// 声明和初始化数组
int[] scores = {90, 85, 92, 78, 88}; // 声明并初始化

// 创建数组并指定大小，默认值
double[] prices = new double[5]; // 元素默认为 0.0

// 访问数组元素
System.out.println("First score: " + scores[0]);
prices[2] = 10.50; // 赋值

// 获取数组长度
System.out.println("Number of scores: " + scores.length);

// 遍历数组 (普通 for 循环)
for (int i = 0; i < scores.length; i++) {
    System.out.println("Score at index " + i + ": " + scores[i]);
}

// 遍历数组 (增强型 for 循环)
for (int score : scores) {
    System.out.println("Score: " + score);
}

// 二维数组 (矩阵)
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// 访问二维数组元素
System.out.println("Element at row 1, column 2: " + matrix[1][2]); // 6

// 遍历二维数组
for (int i = 0; i < matrix.length; i++) { // 遍历行
    for (int j = 0; j < matrix[i].length; j++) { // 遍历列
        System.out.print(matrix[i][j] + "\t");
    }
    System.out.println();
}
```

#### 5. 静态方法 (`static methods`)

*   **作用**: 将代码组织成可重用、独立的代码块，避免代码重复。
*   **定义**: 使用 `static` 关键字修饰，放在类内部，方法名后跟括号 `()`，可以有参数列表和返回值。
*   **调用**: `ClassName.methodName(arguments);`。
*   **返回值**: 使用 `return` 语句返回方法的结果。`void` 方法不返回值。
*   **参数**: 方法的输入，按照顺序传递。
*   **应用**: `Math` 类中的方法，如 `Math.abs()`, `Math.max()`。

**代码示例**:

```java
public class MethodExamples {

    // 静态方法：计算两个整数的较大值
    public static int findMax(int num1, int num2) {
        if (num1 > num2) {
            return num1;
        } else {
            return num2;
        }
    }

    // 静态方法：计算一个字符串的长度 (虽然 String.length() 已有，作为示例)
    public static int getStringLength(String str) {
        return str.length();
    }

    // 静态方法：累加一个数组中的所有元素
    public static int sumArray(int[] arr) {
        int totalSum = 0;
        for (int element : arr) {
            totalSum += element;
        }
        return totalSum;
    }

    public static void main(String[] args) {
        // 调用静态方法
        int maxNum = findMax(15, 25);
        System.out.println("The maximum is: " + maxNum);

        String message = "Hello Java";
        int length = getStringLength(message);
        System.out.println("The length of '" + message + "' is: " + length);

        int[] data = {1, 2, 3, 4, 5};
        int arraySum = sumArray(data);
        System.out.println("The sum of the array is: " + arraySum);
    }
}
```

---

### 第二部分：字符串 (Strings)

#### 1. 字符串的本质与创建

*   **`String` 是引用类型**: `String` 在 Java 中是一个类（对象），而不是基本数据类型。
*   **不可变性**: `String` 对象一旦创建，其内容就不能被修改。每次对 `String` 进行修改（如拼接）都会创建一个新的 `String` 对象。
*   **创建方式**:
    *   **字符串字面量 (String Literal)**: `String str = "hello";`。Java 会将字面量放入字符串常量池，如果存在相同的字面量，则复用。
    *   **`new` 关键字**: `String str = new String("hello");`。每次使用 `new` 都会创建一个新的 `String` 对象，即使内容相同。

**代码示例**:

```java
// 字符串字面量
String literal1 = "CPT105";
String literal2 = "CPT105";
System.out.println("Literal 1 == Literal 2: " + (literal1 == literal2)); // true (共用字符串常量池中的对象)

// 使用 new 关键字
String newString1 = new String("CPT105");
String newString2 = new String("CPT105");
System.out.println("New 1 == New 2: " + (newString1 == newString2));     // false (创建了两个不同的 String 对象)
System.out.println("New 1 equals Literal 1: " + newString1.equals(literal1)); // true (值相等)
```

#### 2. 字符串拼接 (Concatenation)

*   **`+` 运算符**: 最常用的拼接方式，可以与其他类型（如 `char`, `int`）拼接，会将其他类型转换为字符串。
*   **`concat()` 方法**: `string1.concat(string2)`，只能拼接字符串。
*   **`String.format()`**: 格式化字符串，类似于 C 语言的 `sprintf`。

**代码示例**:

```java
String firstName = "Alice";
String lastName = "Smith";
int year = 2023;

// 使用 + 运算符
String fullName = firstName + " " + lastName;
System.out.println(fullName); // Alice Smith

String info = "Student: " + fullName + ", Year: " + year;
System.out.println(info); // Student: Alice Smith, Year: 2023

// 使用 concat() 方法 (仅限 String)
String greeting = "Hello".concat(" ").concat("World!");
System.out.println(greeting); // Hello World!

// 使用 String.format()
String formattedString = String.format("%s - %d", fullName, year);
System.out.println(formattedString); // Alice Smith - 2023
```

#### 3. 字符串比较

*   **`==`**: 比较引用（内存地址），对于字符串字面量可能返回 `true` (因为共用池)，但对于 `new String()` 创建的对象，通常返回 `false`。**不推荐用于比较字符串内容。**
*   **`equals(String anotherString)`**: 比较字符串的内容是否相等，区分大小写。
*   **`equalsIgnoreCase(String anotherString)`**: 比较字符串的内容是否相等，忽略大小写。
*   **`compareTo(String anotherString)`**: 比较两个字符串的字典顺序。
    *   返回 0：表示相等。
    *   返回负值：当前字符串在字典顺序上小于另一个字符串。
    *   返回正值：当前字符串在字典顺序上大于另一个字符串。
*   **`compareToIgnoreCase(String anotherString)`**: 忽略大小写进行比较。

**代码示例**:

```java
String s1 = "Java";
String s2 = new String("Java");
String s3 = "java";

System.out.println("s1 == s2: " + (s1 == s2));             // false
System.out.println("s1.equals(s2): " + s1.equals(s2));       // true
System.out.println("s1.equalsIgnoreCase(s3): " + s1.equalsIgnoreCase(s3)); // true
System.out.println("s1.compareTo(s3): " + s1.compareTo(s3)); // -32 (因为 'J' 和 'j' 的 ASCII 值差)
```

#### 4. 字符串索引与子字符串

*   **`indexOf(char ch)` / `indexOf(String str)`**: 返回指定字符或子字符串第一次出现的索引。如果不存在，返回 -1。
*   **`lastIndexOf(char ch)` / `lastIndexOf(String str)`**: 返回指定字符或子字符串最后一次出现的索引。
*   **`charAt(int index)`**: 返回指定索引处的字符。
*   **`substring(int beginIndex)`**: 返回从 `beginIndex` 开始到字符串末尾的子字符串。
*   **`substring(int beginIndex, int endIndex)`**: 返回从 `beginIndex` 开始到 `endIndex` (不包含) 的子字符串。
*   **`split(String regex)`**: 使用正则表达式将字符串分割成子字符串数组。
*   **`String.join(CharSequence delimiter, CharSequence... elements)`**: 将数组或集合中的元素连接成一个字符串，并用指定的分隔符隔开。

**代码示例**:

```java
String text = "Programming is fun!";

// 查找索引
System.out.println("Index of 'g': " + text.indexOf('g'));     // 3
System.out.println("Index of 'is': " + text.indexOf("is"));   // 12
System.out.println("Last index of 'g': " + text.lastIndexOf('g')); // 9

// 获取字符
System.out.println("Character at index 0: " + text.charAt(0)); // P

// 获取子字符串
System.out.println("Substring from index 12: " + text.substring(12)); // is fun!
System.out.println("Substring from 0 to 11: " + text.substring(0, 11)); // Programming

// 分割字符串
String dataString = "apple,banana,cherry";
String[] fruits = dataString.split(",");
for (String fruit : fruits) {
    System.out.println("Fruit: " + fruit);
}

// 连接字符串
String[] names = {"Alice", "Bob", "Charlie"};
String commaSeparatedNames = String.join(", ", names);
System.out.println(commaSeparatedNames); // Alice, Bob, Charlie
```

#### 5. 字符串替换与空白处理

*   **`replace(char oldChar, char newChar)`**: 替换所有匹配的字符。
*   **`replace(CharSequence target, CharSequence replacement)`**: 替换所有匹配的子字符串。
*   **`replaceFirst(String regex, String replacement)`**: 替换第一个匹配正则表达式的子字符串。
*   **`replaceAll(String regex, String replacement)`**: 替换所有匹配正则表达式的子字符串。
*   **`trim()`**: 移除字符串开头和结尾的空格（`\u0020`）。
*   **`strip()` (Java 11+)**: 移除字符串开头和结尾的所有空白字符（Unicode aware）。
*   **`stripLeading()`**: 移除字符串开头的空白字符。
*   **`stripTrailing()`**: 移除字符串结尾的空白字符。

**代码示例**:

```java
String original = "  Hello   World  \n";

// 替换
System.out.println("Replace 'o' with 'x': " + original.replace('o', 'x'));
System.out.println("Replace 'World' with 'Java': " + original.replace("World", "Java"));

// trim() vs strip()
System.out.println("Trimmed: [" + original.trim() + "]");     // [Hello   World] (注意内部空格)
System.out.println("Strip: [" + original.strip() + "]");       // [Hello   World] (Java 11+，行为类似 trim，内部空格保留)
System.out.println("Strip Leading: [" + original.stripLeading() + "]"); // [Hello   World  ]
System.out.println("Strip Trailing: [" + original.stripTrailing() + "]");// [  Hello   World]
```

#### 6. 字符串测试与大小写转换

*   **`isEmpty()`**: 判断字符串是否为空 (`length() == 0`)。
*   **`isBlank()` (Java 11+)**: 判断字符串是否为空或只包含空白字符。
*   **`contains(CharSequence s)`**: 判断字符串是否包含指定的子序列。
*   **`startsWith(String prefix)`**: 判断字符串是否以指定前缀开始。
*   **`endsWith(String suffix)`**: 判断字符串是否以指定后缀结束。
*   **`toLowerCase()`**: 将字符串转换为小写。
*   **`toUpperCase()`**: 将字符串转换为大写。

**代码示例**:

```java
String testStr = " Hello World ";
String emptyStr = "";
String blankStr = "   ";

System.out.println("Is '" + testStr + "' empty? " + testStr.isEmpty());       // false
System.out.println("Is '" + emptyStr + "' empty? " + emptyStr.isEmpty());     // true
System.out.println("Is '" + blankStr + "' blank? " + blankStr.isBlank());     // true (Java 11+)

System.out.println("Contains 'World': " + testStr.contains("World"));       // true
System.out.println("Starts with ' ': " + testStr.startsWith(" "));        // true
System.out.println("Ends with '!': " + testStr.endsWith("!"));             // false

System.out.println("Lowercase: " + testStr.toLowerCase());         //  hello world
System.out.println("Uppercase: " + testStr.toUpperCase());         //  HELLO WORLD
```

---

### 第三部分：对象 (Objects) 和类 (Classes)

#### 1. 对象与类 (Objects & Classes)

*   **类 (Class)**: 对象的蓝图或模板，定义了对象的属性（变量）和行为（方法）。
*   **对象 (Object)**: 类的实例，拥有类定义的属性和行为。
*   **属性 (Attributes/Instance Variables)**: 描述对象状态的变量。
*   **行为 (Behaviors/Methods)**: 对象能执行的操作。
*   **`new` 关键字**: 用于创建类的实例（对象）。

**代码示例 (Person 类)**:

```java
// Person.java
public class Person {
    // 属性 (Instance Variables)
    private String name;
    private int age;

    // 构造器 (Constructor)
    public Person(String name, int age) {
        this.name = name; // this.name 指向当前对象的 name，name 指向参数
        this.age = age;
    }

    // 行为 (Methods)
    public void greet() {
        System.out.println("Hello, my name is " + name + " and I am " + age + " years old.");
    }

    // Getter 方法 (用于访问私有属性)
    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    // Setter 方法 (用于修改私有属性)
    public void setAge(int age) {
        if (age > 0) { // 可以添加校验逻辑
            this.age = age;
        }
    }

    // toString() 方法 (返回对象的字符串表示)
    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + '}';
    }
}
```

#### 2. 构造器 (Constructors)

*   **作用**: 初始化新创建的对象。
*   **特点**:
    *   方法名与类名完全相同。
    *   没有返回类型（甚至没有 `void`）。
    *   可以有参数，用于接收创建对象时传入的值。
    *   一个类可以有多个构造器（构造器重载）。
*   **`this` 关键字**: 在构造器或方法中，用来区分当前对象的成员变量和同名的局部变量（参数）。
*   **`super` 关键字**: 在子类构造器中，用于调用父类构造器。

#### 3. 封装 (Encapsulation)

*   **`private` 访问修饰符**: 限制属性和方法的访问范围，只能在同一个类内部访问。
*   **Getter 和 Setter 方法**: 提供公共的（`public`）方法来读取（get）和修改（set）私有属性的值。这有助于控制对数据的访问，并在修改时进行数据校验。
*   **优点**:
    *   **数据隐藏 (Data Hiding)**: 保护类内部数据不被外部随意修改。
    *   **提高代码的灵活性和可维护性**: 可以在不改变类接口的情况下，修改类的内部实现。

#### 4. 静态成员 (`static`)

*   **静态变量 (Class Variables)**:
    *   所有类的对象共享同一个静态变量。
    *   通过 `ClassName.variableName` 访问。
    *   用于表示类的共有属性（如计数器）。
*   **静态方法 (Static Methods)**:
    *   不依赖于类的任何特定对象，可以直接通过类名调用。
    *   在静态方法中，不能直接访问实例变量（非 `static` 变量），因为静态方法不属于任何特定对象。
    *   `main` 方法是特殊的静态方法，是程序的入口。

**代码示例 (包含静态变量)**:

```java
// Person.java (修改，添加计数器)
public class Person {
    private String name;
    private int age;
    private static int personCount = 0; // 静态变量，记录创建的 Person 对象数量

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
        personCount++; // 每创建一个对象，计数器加一
    }

    public String getName() { return name; }
    public int getAge() { return age; }
    public void setAge(int age) { if (age > 0) this.age = age; }

    // 静态方法，用于获取静态变量的值
    public static int getPersonCount() {
        return personCount;
    }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + '}';
    }
}

// MainProgram.java (使用 Person 类)
public class MainProgram {
    public static void main(String[] args) {
        Person person1 = new Person("Alice", 30);
        Person person2 = new Person("Bob", 25);

        System.out.println(person1);
        person1.greet(); // 调用非静态方法

        System.out.println("Total number of people created: " + Person.getPersonCount()); // 调用静态方法
    }
}
```

#### 5. 对象与数组

*   **对象数组**: 可以创建存储对象的数组，如 `Person[] people = new Person[5];`。
*   **遍历**: 使用普通 `for` 循环或增强型 `for` 循环来访问数组中的每个对象。
*   **`==` vs `.equals()`**:
    *   `==` 比较两个引用是否指向堆内存中的同一个对象（地址）。
    *   `.equals()` (通常需要重写) 比较两个对象的内容是否相等。

**代码示例 (Person 数组)**:

```java
// Person.java (已存在)

// MainProgram.java
public class MainProgram {
    public static void main(String[] args) {
        // 创建对象数组
        Person[] people = new Person[3];
        people[0] = new Person("Alice", 30);
        people[1] = new Person("Bob", 25);
        people[2] = new Person("Charlie", 35);

        // 遍历对象数组并调用方法
        for (Person p : people) {
            System.out.println(p.toString()); // 调用对象的 toString() 方法
            p.greet();
        }

        // 比较对象 (假设 Person 类已重写 equals 方法，或自己写一个比较方法)
        Person p1 = new Person("Alice", 30);
        Person p2 = new Person("Alice", 30);
        // System.out.println("p1 equals p2: " + p1.equals(p2)); // 如果没有重写 equals，则比较的是引用
    }
}
```

---

### 第三部分：继承 (Inheritance)

#### 1. 继承的概念

*   **代码重用**: 子类可以继承父类（超类）的属性和方法。
*   **`extends` 关键字**: 用于声明继承关系 (`class Subclass extends Superclass`)。
*   **is-a 关系**: 子类与父类之间是 "is-a" 的关系（例如，`Student` is a `Person`）。
*   **单继承**: Java 中一个类只能直接继承自一个父类。

#### 2. 子类与父类

*   **子类 (Subclass/Child Class)**: 继承父类的类。
*   **父类 (Superclass/Parent Class)**: 被继承的类。
*   **`super` 关键字**:
    *   在子类构造器中，`super(...)` 用于调用父类构造器，必须是第一条语句。
    *   `super.method()` 用于调用父类的方法。

**代码示例 (Person 和 Student)**:

```java
// Person.java (父类)
public class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() { return name; }
    public int getAge() { return age; }
    public void setAge(int age) { if (age > 0) this.age = age; }

    @Override
    public String toString() {
        return "Person{name='" + name + "', age=" + age + '}';
    }
}

// Student.java (子类)
public class Student extends Person {
    private String major; // Student 特有的属性
    private int studentId;

    // 子类构造器
    public Student(String name, int age, String major, int studentId) {
        super(name, age); // 调用父类 Person 的构造器，必须放在第一行
        this.major = major;
        this.studentId = studentId;
    }

    // Student 特有的方法
    public String getMajor() { return major; }
    public int getStudentId() { return studentId; }

    // 重写父类的 toString() 方法
    @Override
    public String toString() {
        // 调用父类的 toString() 方法，并添加子类特有的信息
        return super.toString() + ", Major: " + major + ", ID: " + studentId;
    }
}

// MainProgram.java
public class MainProgram {
    public static void main(String[] args) {
        Student student1 = new Student("Alice", 20, "Computer Science", 12345);
        System.out.println(student1.toString()); // 调用重写后的 toString()
        System.out.println("Student Name: " + student1.getName()); // 调用继承自 Person 的方法
        System.out.println("Student Major: " + student1.getMajor()); // 调用 Student 特有的方法
    }
}
```

#### 3. 方法重写 (Overriding)

*   **作用**: 子类可以重新定义父类中已经存在的方法，以实现自己的特定行为。
*   **条件**:
    *   方法名、参数列表（签名）必须与父类方法完全相同。
    *   返回类型必须与父类方法兼容（可以是父类返回类型的子类型）。
    *   子类方法不能比父类方法具有更宽松的访问权限（如父类是 `protected`，子类不能是 `public`）。
*   **`@Override` 注解**: 建议加上，用于编译时检查是否真的重写了父类方法，提高代码健壮性。

#### 4. 方法重载 (Overloading)

*   **作用**: 在同一个类中，允许有多个同名的方法，但它们的参数列表（参数数量、类型或顺序）必须不同。
*   **与重写区别**: 重载发生在同一个类，重写发生在子类与父类之间。

**代码示例 (重载)**:

```java
public class Calculator {
    // 方法重载：参数类型不同
    public static int add(int a, int b) {
        return a + b;
    }

    public static double add(double a, double b) {
        return a + b;
    }

    // 方法重载：参数数量不同
    public static int add(int a) {
        return a + 1;
    }

    public static void main(String[] args) {
        System.out.println("Add ints: " + add(5, 10));      // 调用 int add(int, int)
        System.out.println("Add doubles: " + add(5.5, 10.2)); // 调用 double add(double, double)
        System.out.println("Add one int: " + add(5));        // 调用 int add(int)
    }
}
```

#### 5. 多态 (Polymorphism)

*   **概念**: "多种形态"，允许一个父类类型的引用指向不同子类的对象。
*   **上转型 (Upcasting)**: 父类引用指向子类对象，是隐式发生的。
    *   `Person p = new Student(...);`
    *   通过父类引用只能访问父类的方法和继承的方法。
*   **下转型 (Downcasting)**: 将父类引用强制转换为子类引用，需要显式声明。
    *   `Student s = (Student) p;`
    *   需要确保父类引用实际指向的就是该子类对象，否则会抛出 `ClassCastException`。
*   **运行时多态**: 当通过父类引用调用被子类重写的方法时，实际执行的是子类中的那个版本。

**代码示例**:

```java
Person personRef; // 父类引用
Student studentObj = new Student("Charlie", 22, "Physics", 67890);

// 上转型 (隐式)
personRef = studentObj;
System.out.println(personRef.getName()); // 调用 Person 的方法
// System.out.println(personRef.getMajor()); // 编译错误！父类引用无法直接访问子类特有方法

// 下转型 (显式)
if (personRef instanceof Student) { // 检查引用实际指向的对象类型
    Student castedStudent = (Student) personRef;
    System.out.println("Casted Student Major: " + castedStudent.getMajor());
}
```

---

### 第四部分：常用类和工具

#### 1. `Character` 类

*   **作用**: 提供处理 `char` 类型的方法。
*   **常用静态方法**:
    *   `isDigit(char ch)`: 是否是数字。
    *   `isLetter(char ch)`: 是否是字母。
    *   `isLetterOrDigit(char ch)`: 是否是字母或数字。
    *   `isWhitespace(char ch)`: 是否是空白字符。
    *   `toLowerCase(char ch)`: 转换为小写。
    *   `toUpperCase(char ch)`: 转换为大写。

**代码示例**:

```java
char c1 = '7';
char c2 = 'a';
char c3 = ' ';

System.out.println("Is '" + c1 + "' a digit? " + Character.isDigit(c1)); // true
System.out.println("Is '" + c2 + "' a letter? " + Character.isLetter(c2)); // true
System.out.println("Is '" + c3 + "' whitespace? " + Character.isWhitespace(c3)); // true
System.out.println("Lowercase 'A': " + Character.toLowerCase('A')); // a
```

#### 2. `Math` 类

*   **作用**: 提供数学运算的静态方法。
*   **常用方法**:
    *   `abs(double a)`: 绝对值。
    *   `ceil(double a)`: 向上取整。
    *   `floor(double a)`: 向下取整。
    *   `round(double a)`: 四舍五入。
    *   `pow(double a, double b)`: a 的 b 次方。
    *   `sqrt(double a)`: 平方根。
    *   `random()`: 返回 0.0 (包含) 到 1.0 (不包含) 的伪随机 `double` 值。

**代码示例**:

```java
System.out.println("Absolute value of -5.5: " + Math.abs(-5.5)); // 5.5
System.out.println("Ceiling of 5.5: " + Math.ceil(5.5));       // 6.0
System.out.println("Floor of 5.5: " + Math.floor(5.5));         // 5.0
System.out.println("Round of 5.5: " + Math.round(5.5));         // 6
System.out.println("2 to the power of 3: " + Math.pow(2, 3));   // 8.0
System.out.println("Square root of 9: " + Math.sqrt(9));       // 3.0
System.out.println("Random number: " + Math.random());
```

#### 3. `Scanner` 类

*   **作用**: 用于从各种输入源（如标准输入、文件）读取基本数据类型和字符串。
*   **常用方法**:
    *   `nextInt()`: 读取一个 `int`。
    *   `nextDouble()`: 读取一个 `double`。
    *   `next()`: 读取下一个单词（以空格或分隔符为界）。
    *   `nextLine()`: 读取一整行（包括空格），直到换行符。
*   **关闭**: 使用 `scanner.close()` 释放资源。
*   **异常处理**: 当输入与期望类型不匹配时，会抛出 `InputMismatchException`。

**代码示例**:

```java
import java.util.Scanner;
import java.util.InputMismatchException;

public class ScannerExample {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        try {
            System.out.print("Enter your name: ");
            String name = input.nextLine(); // 读取整行

            System.out.print("Enter your age: ");
            int age = input.nextInt(); // 读取一个整数

            System.out.println("Hello, " + name + "! You are " + age + " years old.");

            // 注意：nextInt() 后使用 nextLine() 时，需要处理换行符
            input.nextLine(); // 消耗掉nextInt() 留下的换行符

            System.out.print("Enter your favorite color: ");
            String color = input.nextLine();
            System.out.println("Your favorite color is: " + color);

        } catch (InputMismatchException e) {
            System.err.println("Invalid input. Please enter a number for age.");
            input.nextLine(); // 清除错误输入，防止无限循环
        } finally {
            input.close(); // 总是关闭 Scanner
        }
    }
}
```

#### 4. 异常处理 (`try-catch-finally`)

*   **`try`**: 包含可能抛出异常的代码块。
*   **`catch`**: 捕获特定类型的异常，并执行相应的处理代码。可以有多个 `catch` 块。
*   **`finally`**: 无论是否发生异常，都会执行的代码块，常用于资源释放。
*   **`throw`**: 手动抛出一个异常。
*   **`throws`**: 在方法签名中声明该方法可能抛出的异常。

**代码示例 (计算器中的除法)**:

```java
// 在 StudentManagementSystem.java 或 Calculator.java 中
public static double divide(double numerator, double denominator) {
    if (denominator == 0) {
        throw new ArithmeticException("Division by zero is not allowed.");
    }
    return numerator / denominator;
}

// 在 Main.java 或调用处
public static void main(String[] args) {
    Scanner input = new Scanner(System.in);
    try {
        System.out.print("Enter numerator: ");
        double num = input.nextDouble();
        System.out.print("Enter denominator: ");
        double den = input.nextDouble();

        double result = divide(num, den); // 调用可能抛出异常的方法
        System.out.println("Result: " + result);

    } catch (InputMismatchException e) {
        System.err.println("Invalid input. Please enter numbers.");
        input.nextLine();
    } catch (ArithmeticException e) {
        System.err.println("Error: " + e.getMessage()); // 打印异常信息
    } finally {
        input.close();
        System.out.println("Scanner closed.");
    }
}
```

---

### 第五部分：综合应用与编程题

#### 1. Student ID Validator (根据 Week 5 示例)

*   **需求**: 验证学生 ID 是否符合格式：以 "CPT" 开头，后跟 4 位数字，总长度为 7。
*   **用到的知识**: `String` 的 `startsWith()`, `length()`, `charAt()`, `substring()`, `Character` 的 `isDigit()`, `if` 语句。

**代码示例**:

```java
public class StudentIDValidator {

    public static boolean isValidStudentID(String studentID) {
        // 1. 检查是否为 null
        if (studentID == null) {
            return false;
        }

        // 2. 检查总长度
        if (studentID.length() != 7) {
            return false;
        }

        // 3. 检查是否以 "CPT" 开头
        if (!studentID.startsWith("CPT")) {
            return false;
        }

        // 4. 检查后 4 位是否为数字
        // 提取后 4 位
        String digitsPart = studentID.substring(3); // 从索引 3 到末尾
        for (int i = 0; i < digitsPart.length(); i++) {
            char ch = digitsPart.charAt(i);
            if (!Character.isDigit(ch)) {
                return false; // 发现非数字字符
            }
        }

        // 所有检查都通过
        return true;
    }

    public static void main(String[] args) {
        String[] testIDs = {"CPT1234", "CPT12A4", "CPT123", "CPT12345", "CPT123!", "cpt1234"};
        for (String id : testIDs) {
            System.out.println("ID: " + id + ", Valid: " + isValidStudentID(id));
        }
    }
}
```

#### 2. Student Information Normaliser & Validator (根据 Week 5 示例)

*   **需求**:
    *   **Student ID**: CPT + 4 digits, length 7.
    *   **Name**: Only letters and spaces, two parts (first, last), normalized to "Firstname Lastname".
    *   **Password**: 8-16 chars, upper, lower, digit, symbol, no whitespace.
    *   Input format: `" CPT105: aLiCE smiTh : Pa$$w0rd123"` (带空格，需要处理)
*   **用到的知识**: `String.split()`, `String.trim()`, `String.substring()`, `Character` 方法, `for` 循环, `if` 语句, `boolean` 逻辑。

**代码示例 (部分核心逻辑)**:

```java
import java.util.ArrayList;
import java.util.List;

public class StudentInfoProcessor {

    // ... (isValidStudentID, isValidName, normaliseName, isStrongPassword 方法) ...

    // Student ID Validation (复用或简化)
    public static boolean isValidStudentID(String studentID) {
        if (studentID == null || studentID.length() != 7) return false;
        if (!studentID.startsWith("CPT")) return false;
        for (int i = 3; i < 7; i++) {
            if (!Character.isDigit(studentID.charAt(i))) return false;
        }
        return true;
    }

    // Name Validation
    public static boolean isValidName(String name) {
        if (name == null || name.trim().isEmpty()) return false;
        String[] parts = name.trim().split("\\s+"); // \\s+ 匹配一个或多个空白字符
        if (parts.length != 2) return false; // 必须是两个部分
        for (String part : parts) {
            if (part.isEmpty()) return false;
            for (char ch : part.toCharArray()) {
                if (!Character.isLetter(ch)) return false; // 只允许字母
            }
        }
        return true;
    }

    // Name Normalization
    public static String normaliseName(String name) {
        if (name == null) return null;
        String trimmedName = name.trim();
        String[] parts = trimmedName.split("\\s+");
        StringBuilder normalized = new StringBuilder();
        for (int i = 0; i < parts.length; i++) {
            String part = parts[i];
            if (!part.isEmpty()) {
                String lowerPart = part.toLowerCase();
                normalized.append(Character.toUpperCase(lowerPart.charAt(0)))
                        .append(lowerPart.substring(1));
                if (i < parts.length - 1) {
                    normalized.append(" ");
                }
            }
        }
        return normalized.toString();
    }

    // Password Validation
    public static boolean isStrongPassword(String password) {
        if (password == null || password.length() < 8 || password.length() > 16) {
            return false;
        }
        boolean hasUpper = false, hasLower = false, hasDigit = false, hasSymbol = false;
        for (char ch : password.toCharArray()) {
            if (Character.isUpperCase(ch)) hasUpper = true;
            else if (Character.isLowerCase(ch)) hasLower = true;
            else if (Character.isDigit(ch)) hasDigit = true;
            else if (!Character.isWhitespace(ch)) hasSymbol = true; // 任何非空白字符都视为符号
        }
        return hasUpper && hasLower && hasDigit && hasSymbol;
    }

    // Overall Validation
    public static boolean isValidStudentInfo(String studentInfo) {
        if (studentInfo == null) return false;
        String[] parts = studentInfo.split(":", 3); // 最多分割 3 部分
        if (parts.length != 3) return false;

        String studentID = parts[0].trim();
        String name = parts[1].trim();
        String password = parts[2].trim();

        return isValidStudentID(studentID) &&
               isValidName(name) &&
               isStrongPassword(password);
    }

    public static void main(String[] args) {
        String input = "   CPT105:   aLiCE   smiTh   : Pa$$w0rd123";
        boolean isValid = isValidStudentInfo(input);
        System.out.println("Input: \"" + input + "\" is valid: " + isValid);

        if (isValid) {
            String[] parts = input.split(":", 3);
            String name = parts[1].trim();
            String normalizedName = normaliseName(name);
            System.out.println("Normalized Name: " + normalizedName);
        }

        // Test cases
        String[] testInputs = {
                "CPT1234: Alice Smith : P@ssw0rd!",
                "CPT5678: Bob Johnson: StrongP@ss1",
                "CPT12345: David Wilson: Short1!", // ID too long
                "CPT123: Eve Davis: NoSymbol1",   // ID too short
                "CPT1234: Frank Miller: noupper1!",// Password no upper
                "CPT1234: Grace Lee: NOLOWER1!",  // Password no lower
                "CPT1234: Henry King:   NoDigit !",// Password no digit
                "CPT1234: InvalidName1: ValidP@ss1", // Name invalid
                "INVALID1234: Ian Scott: ValidP@ss1", // ID invalid
                "CPT1234: Jack White : ValidP@ss1" // Valid
        };

        System.out.println("\n--- Testing Various Inputs ---");
        for (String testInput : testInputs) {
            boolean isValidInput = isValidStudentInfo(testInput);
            System.out.printf("Input: \"%s\" Valid: %b%n", testInput, isValidInput);
            if (isValidInput) {
                String[] parts = testInput.split(":", 3);
                String name = parts[1].trim();
                String normalizedName = normaliseName(name);
                System.out.printf("  Normalized Name: %s%n", normalizedName);
            }
        }
    }
}
```

祝你期末考试顺利！
