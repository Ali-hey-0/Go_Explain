# راهنمای جامع زبان برنامه‌نویسی Go

![لوگوی Go](https://golang.org/doc/gopher/gopherbw.png)

## 📋 فهرست مطالب

- [مقدمه](#مقدمه)
- [نصب](#نصب)
- [شروع به کار](#شروع-به-کار)
  - [برنامه Hello World](#برنامه-hello-world)
  - [راه‌اندازی فضای کاری Go](#راه‌اندازی-فضای-کاری-go)
- [نحو پایه](#نحو-پایه)
  - [متغیرها و ثابت‌ها](#متغیرها-و-ثابت‌ها)
  - [انواع داده](#انواع-داده)
  - [عملگرها](#عملگرها)
- [ساختارهای کنترلی](#ساختارهای-کنترلی)
  - [دستورات شرطی](#دستورات-شرطی)
  - [حلقه‌ها](#حلقه‌ها)
- [توابع](#توابع)
  - [مبانی توابع](#مبانی-توابع)
  - [مقادیر بازگشتی چندگانه](#مقادیر-بازگشتی-چندگانه)
  - [توابع ناشناس و مرتبه بالاتر](#توابع-ناشناس-و-مرتبه-بالاتر)
- [انواع مرکب](#انواع-مرکب)
  - [آرایه‌ها و برش‌ها](#آرایه‌ها-و-برش‌ها)
  - [نقشه‌ها](#نقشه‌ها)
  - [ساختارها](#ساختارها)
- [روش‌ها و رابط‌ها](#روش‌ها-و-رابط‌ها)
  - [روش‌ها](#روش‌ها)
  - [رابط‌ها](#رابط‌ها)
- [همزمانی](#همزمانی)
  - [گوروتین‌ها](#گوروتین‌ها)
  - [کانال‌ها](#کانال‌ها)
  - [دستور Select](#دستور-select)
- [مدیریت خطا](#مدیریت-خطا)
- [بسته‌ها و ماژول‌ها](#بسته‌ها-و-ماژول‌ها)
- [کتابخانه استاندارد](#کتابخانه-استاندارد)
- [آزمون](#آزمون)
- [ابزارها و اکوسیستم](#ابزارها-و-اکوسیستم)
- [بهترین شیوه‌ها](#بهترین-شیوه‌ها)
- [منابع](#منابع)
- [مجوز](#مجوز)

## 🌟 مقدمه

زبان Go، که به عنوان Golang نیز شناخته می‌شود، یک زبان برنامه‌نویسی کامپایل شده و به صورت ایستا تایپ شده است که توسط گوگل طراحی شده است. این زبان به دلیل سادگی، کارایی و پشتیبانی قوی از برنامه‌نویسی همزمان شناخته شده است. Go به طور گسترده برای ساخت سرورهای وب مقیاس‌پذیر، خدمات ابری و سیستم‌های توزیع شده دیگر استفاده می‌شود.

### ویژگی‌های کلیدی Go

- **سادگی:** نحو تمیز و خوانا.
- **کارایی:** زبان کامپایل شده با مدیریت حافظه کارآمد.
- **همزمانی:** پشتیبانی داخلی از برنامه‌نویسی همزمان با گوروتین‌ها و کانال‌ها.
- **کتابخانه استاندارد قوی:** کتابخانه‌های گسترده برای شبکه، ورودی/خروجی و بیشتر.
- **چند سکویی:** کامپایل به باینری‌های بومی برای سیستم‌عامل‌های مختلف.

## 🛠 نصب

برای نصب Go، مراحل زیر را دنبال کنید:

1. **دانلود Go:**
   - به [صفحه دانلود رسمی Go](https://golang.org/dl/) بروید و نصب‌کننده مناسب برای سیستم‌عامل خود را دانلود کنید.

2. **نصب Go:**
   - نصب‌کننده را اجرا کنید و دستورالعمل‌های روی صفحه را دنبال کنید.

3. **تأیید نصب:**
   - یک ترمینال باز کنید و دستور `go version` را تایپ کنید تا تأیید کنید که Go به درستی نصب شده است.

## 🚀 شروع به کار

### برنامه Hello World

بیایید با یک برنامه ساده "Hello, World!" در Go شروع کنیم.

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

- **توضیح:**
  - `package main`: نام بسته را تعریف می‌کند. `main` یک بسته ویژه است که نشان‌دهنده یک برنامه اجرایی است.
  - `import "fmt"`: بسته `fmt` را وارد می‌کند که شامل توابعی برای ورودی/خروجی قالب‌بندی شده است.
  - `func main()`: نقطه ورود برنامه.
  - `fmt.Println("Hello, World!")`: "Hello, World!" را به کنسول چاپ می‌کند.

### راه‌اندازی فضای کاری Go

Go از یک فضای کاری برای مدیریت کد استفاده می‌کند. یک فضای کاری معمولی شامل سه دایرکتوری در ریشه خود است:

- `src`: شامل فایل‌های منبع Go که به صورت بسته‌ها سازماندهی شده‌اند.
- `pkg`: شامل اشیاء بسته.
- `bin`: شامل دستورات اجرایی.

برای راه‌اندازی یک فضای کاری Go:

1. یک دایرکتوری برای فضای کاری خود ایجاد کنید.
2. متغیر محیطی `GOPATH` را تنظیم کنید تا به دایرکتوری فضای کاری شما اشاره کند.
3. از `go get` برای دریافت بسته‌ها و وابستگی‌ها استفاده کنید.

## 📚 نحو پایه

### متغیرها و ثابت‌ها

متغیرها در Go به صورت صریح اعلام می‌شوند و برای ذخیره داده‌ها استفاده می‌شوند.

```go
var name string = "Gopher"
age := 5
```

- **توضیح:**
  - `var name string = "Gopher"`: یک متغیر `name` از نوع `string` اعلام می‌کند.
  - `age := 5`: اعلام کوتاه متغیر، نوع `int` را استنباط می‌کند.

ثابت‌ها مقادیر غیرقابل تغییر هستند که در زمان کامپایل شناخته می‌شوند.

```go
const Pi = 3.14
```

- **توضیح:**
  - `const Pi = 3.14`: یک ثابت `Pi` با مقدار `3.14` اعلام می‌کند.

### انواع داده

Go از چندین نوع داده پایه پشتیبانی می‌کند.

```go
var (
    a bool       // بولین
    b int        // عدد صحیح
    c float64    // عدد اعشاری
    d string     // رشته
)
```

### عملگرها

Go عملگرهای مختلفی برای عملیات‌های حسابی، مقایسه‌ای و منطقی ارائه می‌دهد.

```go
sum := 1 + 2
isEqual := (3 == 3)
```

## 🔄 ساختارهای کنترلی

### دستورات شرطی

#### If-Else

دستورات شرطی در Go.

```go
if age > 18 {
    fmt.Println("Adult")
} else {
    fmt.Println("Minor")
}
```

#### Switch

دستورات Switch برای شرایط متعدد.

```go
switch day {
case "Monday":
    fmt.Println("Start of the week")
case "Friday":
    fmt.Println("End of the week")
default:
    fmt.Println("Midweek")
}
```

### حلقه‌ها

#### For Loops

تنها ساختار حلقه در Go.

```go
for i := 0; i < 5; i++ {
    fmt.Println(i)
}
```

#### Range Loops

تکرار بر روی عناصر در یک مجموعه.

```go
numbers := []int{1, 2, 3, 4, 5}
for index, value := range numbers {
    fmt.Printf("Index: %d, Value: %d\n", index, value)
}
```

## 🔧 توابع

### مبانی توابع

توابع در Go شهروندان درجه یک هستند.

```go
func add(x int, y int) int {
    return x + y
}
```

### مقادیر بازگشتی چندگانه

توابع می‌توانند مقادیر چندگانه بازگردانند.

```go
func swap(x, y string) (string, string) {
    return y, x
}
```

### توابع ناشناس و مرتبه بالاتر

توابعی که توابع دیگر را به عنوان آرگومان می‌پذیرند یا بازمی‌گردانند.

```go
func applyOperation(x, y int, op func(int, int) int) int {
    return op(x, y)
}

result := applyOperation(3, 4, func(a, b int) int {
    return a + b
})
```

## 🏗 انواع مرکب

### آرایه‌ها و برش‌ها

آرایه‌ها دنباله‌های با اندازه ثابت از عناصر هستند، در حالی که برش‌ها به صورت پویا اندازه‌گیری می‌شوند.

```go
var arr [5]int
slice := []int{1, 2, 3, 4, 5}
```

### نقشه‌ها

نقشه‌ها جفت‌های کلید-مقدار هستند.

```go
ages := map[string]int{
    "Alice": 30,
    "Bob":   25,
}
```

### ساختارها

ساختارها انواع داده سفارشی هستند که فیلدها را گروه‌بندی می‌کنند.

```go
type Person struct {
    Name string
    Age  int
}

func (p Person) Greet() {
    fmt.Printf("Hello, my name is %s\n", p.Name)
}
```

## 🔗 روش‌ها و رابط‌ها

### روش‌ها

روش‌ها توابعی با یک آرگومان گیرنده هستند.

```go
func (p Person) Greet() {
    fmt.Printf("Hello, my name is %s\n", p.Name)
}
```

### رابط‌ها

رابط‌ها مجموعه‌ای از امضاهای روش‌ها را تعریف می‌کنند.

```go
type Animal interface {
    Speak() string
}

type Dog struct{}

func (d Dog) Speak() string {
    return "Woof!"
}
```

## ⚙️ همزمانی

### گوروتین‌ها

گوروتین‌ها نخ‌های سبک‌وزنی هستند که توسط زمان‌بند Go مدیریت می‌شوند.

```go
go func() {
    fmt.Println("Running in a goroutine")
}()
```

### کانال‌ها

کانال‌ها برای ارتباط بین گوروتین‌ها استفاده می‌شوند.

```go
ch := make(chan int)
go func() { ch <- 42 }()
fmt.Println(<-ch)
```

### دستور Select

دستور `select` به یک گوروتین اجازه می‌دهد تا بر روی چندین عملیات ارتباطی منتظر بماند.

```go
select {
case msg := <-ch1:
    fmt.Println("Received", msg)
case ch2 <- 42:
    fmt.Println("Sent 42")
default:
    fmt.Println("No communication")
}
```

## 🚨 مدیریت خطا

Go از مدیریت خطای صریح استفاده می‌کند.

```go
func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, fmt.Errorf("cannot divide by zero")
    }
    return a / b, nil
}
```

## 📦 بسته‌ها و ماژول‌ها

Go کد را به صورت بسته‌ها سازماندهی می‌کند و ماژول‌ها مجموعه‌ای از بسته‌های مرتبط هستند.

- **ایجاد یک بسته:**
  - یک دایرکتوری با نام بسته خود ایجاد کنید.
  - فایل‌های منبع Go را با `package <name>` در بالای آن‌ها اضافه کنید.

- **استفاده از ماژول‌ها:**
  - یک ماژول را با `go mod init <module-name>` مقداردهی اولیه کنید.
  - وابستگی‌ها را با `go get` مدیریت کنید.

## 📚 کتابخانه استاندارد

کتابخانه استاندارد Go مجموعه‌ای غنی از بسته‌ها برای وظایف مختلف ارائه می‌دهد، از جمله:

- `fmt`: ورودی/خروجی قالب‌بندی شده
- `net/http`: کلاینت و سرور HTTP
- `os`: عملکرد سیستم‌عامل
- `io`: ابتداییات ورودی و خروجی
- `encoding/json`: کدگذاری و رمزگشایی JSON

## 🧪 آزمون

Go شامل یک چارچوب آزمون داخلی است.

```go
import "testing"

func TestAdd(t *testing.T) {
    result := add(2, 3)
    if result != 5 {
        t.Errorf("Expected 5, got %d", result)
    }
}
```

- آزمون‌ها را با `go test` اجرا کنید.

## 🛠 ابزارها و اکوسیستم

- **ماژول‌های Go:** سیستم مدیریت وابستگی.
- **GoDoc:** ابزار تولید مستندات.
- **GoFmt:** ابزار قالب‌بندی کد.
- **GoLint:** ابزار بررسی کد Go.
- **GoVet:** گزارش سازه‌های مشکوک.

## 🌟 بهترین شیوه‌ها

- **قالب‌بندی کد:** از `gofmt` برای قالب‌بندی کد خود استفاده کنید.
- **مدیریت خطا:** همیشه خطاها را بررسی و مدیریت کنید.
- **همزمانی:** از گوروتین‌ها و کانال‌ها به درستی استفاده کنید.
- **مستندسازی:** کد خود را مستند کنید و از `godoc` برای مستندسازی استفاده کنید.
- **آزمون:** برای کد خود آزمون بنویسید.

## 📚 منابع

- [مستندات رسمی Go](https://golang.org/doc/)
- [Go با مثال](https://gobyexample.com/)
- [کتاب زبان برنامه‌نویسی Go](https://www.gopl.io/)
- [Go موثر](https://golang.org/doc/effective_go.html)
- [ویکی Go](https://github.com/golang/go/wiki)

## 📄 مجوز

این پروژه تحت مجوز MIT منتشر شده است - برای جزئیات به فایل LICENSE مراجعه کنید.

---







توضیحات پروژه:

# راهنمای زبان برنامه‌نویسی Go

## فهرست مطالب
- [مقدمه](#مقدمه)
- [نصب](#نصب)
- [نحو پایه](#نحو-پایه)
- [انواع داده](#انواع-داده)
- [متغیرها](#متغیرها)
- [ثابت‌ها](#ثابت‌ها)
- [ساختارهای کنترلی](#ساختارهای-کنترلی)
- [توابع](#توابع)
- [بسته‌ها](#بسته‌ها)
- [آرایه‌ها و برش‌ها](#آرایه‌ها-و-برش‌ها)
- [نقشه‌ها](#نقشه‌ها)
- [ساختارها](#ساختارها)
- [روش‌ها](#روش‌ها)
- [رابط‌ها](#رابط‌ها)
- [مدیریت خطا](#مدیریت-خطا)
- [همزمانی](#همزمانی)
- [آزمون](#آزمون)
- [بهترین شیوه‌ها](#بهترین-شیوه‌ها)
- [منابع](#منابع)

## مقدمه

Go (که به عنوان Golang نیز شناخته می‌شود) یک زبان برنامه‌نویسی کامپایل شده و به صورت ایستا تایپ شده است که در گوگل توسط رابرت گریسمر، راب پایک و کن تامپسون طراحی شده است. Go به گونه‌ای طراحی شده است که ساده، کارآمد و آسان برای یادگیری باشد، و آن را برای ساخت نرم‌افزارهای قابل اعتماد و کارآمد ایده‌آل می‌کند. ویژگی‌های کلیدی شامل:

- کامپایل سریع
- جمع‌آوری زباله
- تایپ قوی
- پشتیبانی از همزمانی از طریق گوروتین‌ها و کانال‌ها
- سادگی و نحو حداقلی
- کتابخانه استاندارد عالی

## نصب

### دانلود و نصب

1. به وب‌سایت رسمی Go در [golang.org](https://golang.org/dl/) بروید
2. نصب‌کننده مناسب برای سیستم‌عامل خود را دانلود کنید
3. دستورالعمل‌های نصب را دنبال کنید

### تأیید نصب

```bash
go version
```

### راه‌اندازی فضای کاری

Go از یک ساختار فضای کاری خاص استفاده می‌کند:








```bash
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```

## نحو پایه

### مثال Hello World

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

برای اجرا:

```bash
go run hello.go
```

برای ساخت:

```bash
go build hello.go
./hello
```

## انواع داده

Go دارای چندین نوع داده داخلی است:

### انواع پایه

- **bool**: true یا false
- **string**: دنباله‌ای از کاراکترها
- **int**: عدد صحیح (بسته به پلتفرم، 32 یا 64 بیتی)
- **int8/16/32/64**: اعداد صحیح با اندازه خاص
- **uint**: عدد صحیح بدون علامت
- **uint8/16/32/64**: اعداد صحیح بدون علامت با اندازه خاص
- **float32/64**: اعداد اعشاری
- **complex64/128**: اعداد مختلط
- **byte**: نام مستعار برای uint8
- **rune**: نام مستعار برای int32 (نقطه کد یونیکد)

### مثال

```go
package main

import "fmt"

func main() {
    var (
        boolVar     bool    = true
        intVar      int     = 42
        floatVar    float64 = 3.14
        stringVar   string  = "Hello"
        runeVar     rune    = 'A'
        byteVar     byte    = 65
    )
    
    fmt.Printf("انواع و مقادیر: %v %T, %v %T, %v %T, %v %T, %v %T, %v %T\n", 
        boolVar, boolVar, 
        intVar, intVar, 
        floatVar, floatVar, 
        stringVar, stringVar, 
        runeVar, runeVar, 
        byteVar, byteVar)
}
```

## متغیرها

### اعلام متغیر

```go
// روش 1: اعلام با نوع صریح
var name string = "John"

// روش 2: استنباط نوع
var name = "John"

// روش 3: اعلام کوتاه (فقط در داخل توابع)
name := "John"
```

### اعلام چندگانه

```go
var a, b, c int = 1, 2, 3

// یا
var (
    name   string = "John"
    age    int    = 30
    isTrue bool   = true
)
```

## ثابت‌ها

ثابت‌ها با استفاده از کلمه کلیدی `const` اعلام می‌شوند:

```go
const Pi = 3.14159

const (
    StatusOK = 200
    StatusNotFound = 404
)

// استفاده از iota برای شمارش
const (
    Monday = iota
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
    Sunday
)
```

## ساختارهای کنترلی

### دستور If

```go
if x > 0 {
    fmt.Println("x مثبت است")
} else if x < 0 {
    fmt.Println("x منفی است")
} else {
    fmt.Println("x صفر است")
}

// If با مقداردهی اولیه
if value := getSomeValue(); value < 10 {
    fmt.Println("مقدار کمتر از 10 است")
} else {
    fmt.Println("مقدار 10 یا بیشتر است")
}
```

### حلقه For

```go
// حلقه استاندارد
for i := 0; i < 5; i++ {
    fmt.Println(i)
}

// حلقه شبیه به while
i := 0
for i < 5 {
    fmt.Println(i)
    i++
}

// حلقه بی‌نهایت
for {
    // انجام کاری برای همیشه
    break // استفاده از break برای خروج
}

// حلقه مبتنی بر range (برای آرایه‌ها، برش‌ها، نقشه‌ها، رشته‌ها)
numbers := []int{1, 2, 3, 4, 5}
for index, value := range numbers {
    fmt.Printf("شاخص: %d، مقدار: %d\n", index, value)
}
```

### دستور Switch

```go
switch day {
case "Monday":
    fmt.Println("شروع هفته کاری")
case "Friday":
    fmt.Println("پایان هفته کاری")
case "Saturday", "Sunday":
    fmt.Println("آخر هفته")
default:
    fmt.Println("اواسط هفته")
}

// Switch بدون عبارت (مشابه زنجیره if-else)
switch {
case hour < 12:
    fmt.Println("صبح بخیر")
case hour < 17:
    fmt.Println("عصر بخیر")
default:
    fmt.Println("شب بخیر")
}
```

## توابع

### تابع پایه

```go
func add(a, b int) int {
    return a + b
}
```

### مقادیر بازگشتی چندگانه

```go
func divide(a, b float64) (float64, error) {
    if b == 0.0 {
        return 0.0, errors.New("نمی‌توان بر صفر تقسیم کرد")
    }
    return a / b, nil
}
```

### مقادیر بازگشتی نام‌گذاری شده

```go
func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return // بازگشت بدون نام - x و y را بازمی‌گرداند
}
```

### توابع متغیر

```go
func sum(nums ...int) int {
    total := 0
    for _, num := range nums {
        total += num
    }
    return total
}

// فراخوانی با: sum(1, 2, 3, 4)
```

### تابع به عنوان مقادیر و بسته‌ها

```go
// تابع به عنوان مقدار
add := func(a, b int) int {
    return a + b
}
result := add(3, 4)

// بسته
func adder() func(int) int {
    sum := 0
    return func(x int) int {
        sum += x
        return sum
    }
}

// استفاده
counter := adder()
fmt.Println(counter(1)) // 1
fmt.Println(counter(2)) // 3
fmt.Println(counter(3)) // 6
```

### Defer

اجرای یک تابع را تا زمانی که تابع احاطه‌کننده بازگردد به تأخیر می‌اندازد:

```go
func main() {
    defer fmt.Println("World")
    fmt.Println("Hello")
}
// خروجی: Hello\nWorld
```

## بسته‌ها

برنامه‌های Go به صورت بسته‌ها سازماندهی می‌شوند. یک بسته مجموعه‌ای از فایل‌های Go در یک دایرکتوری است.

### ایجاد یک بسته

```go
// در فایل math/math.go
package math

func Add(a, b int) int {
    return a + b
}

func Multiply(a, b int) int {
    return a * b
}
```

### استفاده از بسته‌ها

```go
package main

import (
    "fmt"
    "myproject/math"
)

func main() {
    result := math.Add(5, 3)
    fmt.Println("نتیجه:", result)
}
```

## آرایه‌ها و برش‌ها

### آرایه‌ها

```go
// اعلام
var arr [5]int // یک آرایه از 5 عدد صحیح، مقداردهی اولیه به مقادیر صفر

// اعلام با مقداردهی اولیه
arr := [5]int{1, 2, 3, 4, 5}

// شمارش خودکار عناصر
arr := [...]int{1, 2, 3, 4, 5} // کامپایلر عناصر را می‌شمارد
```

### برش‌ها

برش‌ها در Go انعطاف‌پذیرتر و معمولاً بیشتر از آرایه‌ها استفاده می‌شوند:

```go
// ایجاد یک برش
slice := []int{1, 2, 3, 4, 5}

// ایجاد یک برش از یک آرایه
arr := [5]int{1, 2, 3, 4, 5}
slice := arr[1:4] // عناصر 1، 2، 3 (شاخص‌های 1 تا 3)

// ایجاد یک برش با make
slice := make([]int, 5)    // len=5، cap=5
slice := make([]int, 3, 5) // len=3، cap=5

// افزودن به یک برش
slice = append(slice, 6, 7, 8)

// افزودن یک برش به دیگری
slice1 := []int{1, 2, 3}
slice2 := []int{4, 5, 6}
slice1 = append(slice1, slice2...)
```

## نقشه‌ها

نقشه‌ها نوع داده انجمنی داخلی Go هستند (گاهی اوقات در زبان‌های دیگر به عنوان دیکشنری یا جداول هش نامیده می‌شوند):

```go
// اعلام
var m map[string]int

// مقداردهی اولیه
m = make(map[string]int)

// اعلام و مقداردهی اولیه
m := map[string]int{
    "apple": 5,
    "banana": 10,
    "orange": 8,
}

// دسترسی
count := m["apple"]

// بررسی وجود کلید
count, exists := m["grape"]
if !exists {
    fmt.Println("Grape پیدا نشد")
}

// حذف
delete(m, "apple")

// تکرار
for key, value := range m {
    fmt.Printf("%s: %d\n", key, value)
}
```

## ساختارها

ساختارها مجموعه‌ای از فیلدها هستند:

```go
// تعریف یک ساختار
type Person struct {
    Name    string
    Age     int
    Address string
}

// ایجاد یک نمونه
var p Person
p.Name = "John"
p.Age = 30
p.Address = "123 Main St"

// ایجاد با مقداردهی اولیه
p := Person{
    Name:    "John",
    Age:     30,
    Address: "123 Main St",
}

// کوتاه‌نویسی (ترتیب مهم است)
p := Person{"John", 30, "123 Main St"}
```

### ساختارهای تو در تو

```go
type Address struct {
    Street  string
    City    string
    ZipCode string
}

type Person struct {
    Name    string
    Age     int
    Address Address
}

p := Person{
    Name: "John",
    Age:  30,
    Address: Address{
        Street:  "123 Main St",
        City:    "New York",
        ZipCode: "10001",
    },
}
```

## روش‌ها

روش‌ها توابعی با یک آرگومان گیرنده خاص هستند:

```go
type Rectangle struct {
    Width  float64
    Height float64
}

// روش با گیرنده مقدار
func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}

// روش با گیرنده اشاره‌گر (می‌تواند گیرنده را تغییر دهد)
func (r *Rectangle) Scale(factor float64) {
    r.Width *= factor
    r.Height *= factor
}

// استفاده
rect := Rectangle{Width: 10, Height: 5}
area := rect.Area()
rect.Scale(2)
```

## رابط‌ها

رابط‌ها مجموعه‌ای از امضاهای روش‌ها را تعریف می‌کنند:

```go
type Shape interface {
    Area() float64
    Perimeter() float64
}

type Rectangle struct {
    Width, Height float64
}

func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}

func (r Rectangle) Perimeter() float64 {
    return 2 * (r.Width + r.Height)
}

type Circle struct {
    Radius float64
}

func (c Circle) Area() float64 {
    return math.Pi * c.Radius * c.Radius
}

func (c Circle) Perimeter() float64 {
    return 2 * math.Pi * c.Radius
}

// تابع با استفاده از رابط
func PrintShapeInfo(s Shape) {
    fmt.Printf("مساحت: %f، محیط: %f\n", s.Area(), s.Perimeter())
}

// استفاده
r := Rectangle{Width: 10, Height: 5}
c := Circle{Radius: 7}
PrintShapeInfo(r)
PrintShapeInfo(c)
```

## مدیریت خطا

Go از نوع داخلی `error` برای مدیریت خطاها استفاده می‌کند:

```go
func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, errors.New("تقسیم بر صفر")
    }
    return a / b, nil
}

// استفاده
result, err := divide(10, 0)
if err != nil {
    fmt.Println("خطا:", err)
} else {
    fmt.Println("نتیجه:", result)
}
```

### خطاهای سفارشی

```go
type DivisionError struct {
    Dividend float64
    Divisor  float64
}

func (e *DivisionError) Error() string {
    return fmt.Sprintf("نمی‌توان %f را بر %f تقسیم کرد", e.Dividend, e.Divisor)
}

func divide(a, b float64) (float64, error) {
    if b == 0 {
        return 0, &DivisionError{a, b}
    }
    return a / b, nil
}
```

## همزمانی

### گوروتین‌ها

گوروتین‌ها نخ‌های سبک‌وزنی هستند که توسط زمان‌بند Go مدیریت می‌شوند:

```go
func say(s string) {
    for i := 0; i < 5; i++ {
        time.Sleep(100 * time.Millisecond)
        fmt.Println(s)
    }
}

func main() {
    go say("world") // گوروتین جدید
    say("hello")    // گوروتین فعلی
}
```

### کانال‌ها

کانال‌ها برای ارتباط بین گوروتین‌ها استفاده می‌شوند:

```go
// کانال بدون بافر
ch := make(chan int)

// ارسال در یک کانال
go func() {
    ch <- 42 // ارسال مقدار به کانال
}()

// دریافت از یک کانال
value := <-ch // دریافت مقدار از کانال

// کانال با بافر
ch := make(chan int, 2) // می‌تواند تا 2 مقدار را نگه دارد

// بستن یک کانال
close(ch)

// تکرار بر روی یک کانال
for value := range ch {
    fmt.Println(value)
}
```

### Select

دستور `select` به یک گوروتین اجازه می‌دهد تا بر روی چندین عملیات کانال منتظر بماند:

```go
select {
case msg1 := <-ch1:
    fmt.Println("دریافت از ch1:", msg1)
case msg2 := <-ch2:
    fmt.Println("دریافت از ch2:", msg2)
case ch3 <- msg3:
    fmt.Println("ارسال به ch3:", msg3)
case <-time.After(1 * time.Second):
    fmt.Println("زمان تمام شد")
default:
    fmt.Println("هیچ ارتباطی")
}
```

### WaitGroup

WaitGroup برای انتظار برای اتمام مجموعه‌ای از گوروتین‌ها استفاده می‌شود:

```go
func worker(id int, wg *sync.WaitGroup) {
    defer wg.Done() // کاهش شمارنده زمانی که گوروتین کامل می‌شود
    fmt.Printf("کارگر %d شروع شد\n", id)
    time.Sleep(time.Second)
    fmt.Printf("کارگر %d تمام شد\n", id)
}

func main() {
    var wg sync.WaitGroup
    
    for i := 1; i <= 5; i++ {
        wg.Add(1) // افزایش شمارنده WaitGroup
        go worker(i, &wg)
    }
    
    wg.Wait() // مسدود کردن تا زمانی که شمارنده WaitGroup صفر شود
    fmt.Println("همه کارگران تمام شدند")
}
```

## آزمون

Go دارای یک چارچوب آزمون داخلی است. فایل‌هایی که با `_test.go` پایان می‌یابند ایجاد کنید:

```go
// math.go
package math

func Add(a, b int) int {
    return a + b
}
```

```go
// math_test.go
package math

import "testing"

func TestAdd(t *testing.T) {
    result := Add(2, 3)
    if result != 5 {
        t.Errorf("Add(2, 3) = %d; می‌خواهیم 5", result)
    }
}
