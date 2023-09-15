# ACM

## 模式各种输入总结C++版



[ACM模式各种输入总结C++版 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/494535515)

#### getchar()

- `getchar()` 是一个C标准库函数，通常用于从标准输入流（通常是键盘）读取一个字符。

- 它返回一个整数，表示读取的字符的ASCII码值（或EOF，表示文件结束或读取错误）。

- 示例：

	```
	
	int ch = getchar();
	```

#### cin.get()

- `cin.get()` 是C++中的输入方法，用于从标准输入流（通常是键盘）读取一个字符。

- 它返回一个 `istream` 对象，允许你进一步处理读取的字符。

- 示例：

	```
	char ch;
	ch = cin.get();
	```





#### getline(ss, str,',')

- `getline` 是C++标准库函数，通常用于从输入流中读取一行文本并将其存储在字符串变量中。

- ==`ss` 是输入流（例如 `cin`、文件流等）。==

	- 文件流

		```cpp
		#include <fstream>
		// 打开一个文件流来读取文件
		std::ifstream fileStream("example.txt");
		std::istream& ss = fileStream; // 将ss设置为文件流fileStream
		
		```

	- cin流

		```cpp
		std::istream& ss = std::cin; // 将ss设置为标准输入流cin
		
		```

		

- `str` 是用于存储读取的文本行的字符串对象。

- `','` 是可选的分隔符，如果提供了分隔符，`getline` 会在遇到分隔符时停止读取，否则会读取整行文本。

- 如果读取成功，返回的是输入流 `ss` 的引用，这意味着你可以将 `getline` 作为条件表达式使用，例如 `while (getline(ss, str, ','))`。

	如果读取失败，例如在输入流结束时（EOF）或发生错误时，返回的是输入流 `ss` 的引用，但条件表达式会被视为假，从而退出循环。

#### cin.getline()

`cin.getline()` 是C++中用于从标准输入流 `cin` 中读取一行文本的函数。它的语法如下：

```cpp
cin.getline(char_array, size, delimiter);
```

其中：

- `char_array` 是一个字符数组，用于存储读取的文本行。
- `size` 是字符数组的大小，用于指定最多可以读取多少个字符。
- `delimiter` 是一个可选的参数，用于指定行的结束标志。当遇到指定的结束标志或者达到字符数组大小的限制时，`cin.getline()` 将停止读取。

`cin.getline()` 会读取一行文本，包括行尾的换行符（`\n`），并将其存储在字符数组 `char_array` 中。如果指定了 `delimiter`，则在遇到该字符之前停止读取，不包括该字符。

以下是一个示例：

```cpp
#include <iostream>

int main() {
    char buffer[100];
    
    std::cout << "Enter a line of text: ";
    std::cin.getline(buffer, 100); // 从标准输入读取一行文本并存储在buffer中
    
    std::cout << "You entered: " << buffer << std::endl;
    
    return 0;
}
```

在这个示例中，用户被要求输入一行文本，然后 `cin.getline()` 从标准输入中读取这行文本并存储在 `buffer` 中，最后将其打印出来。





#### stringstream input(s)

istringstream input(s);

ostringstream input(s);

在C++中，`istringstream`、`ostringstream` 和 `stringstream` 都是与字符串相关的流类，它们用于在内存中对字符串进行输入和输出操作。它们的主要区别在于它们的用途和功能：

1. `istringstream`（输入字符串流）：
   
   - ==`istringstream` 用于从字符串中读取数据，将字符串解析为不同的数据类型（例如整数、浮点数、字符等）。==
   - 主要用于从字符串中提取数据，类似于从标准输入流 `cin` 中读取数据。
   - 示例：
     ```cpp
     #include <iostream>
     #include <sstream>
     
     int main() {
         std::string s = "42 3.14 hello";
         std::istringstream input(s);
         int i;
         double d;
         std::string str;
         input >> i >> d >> str;
         std::cout << "Parsed values: " << i << ", " << d << ", " << str << std::endl;
         return 0;
     }
     ```
   
2. `ostringstream`（输出字符串流）：
   - ==`ostringstream` 用于将数据输出到字符串中，将各种数据类型的值转换为字符串。==
   - 主要用于构建字符串，类似于将数据写入标准输出流 `cout`。
   - 示例：
     ```cpp
     #include <iostream>
     #include <sstream>
     
     int main() {
         std::ostringstream output;
         int i = 42;
         double d = 3.14;
         std::string str = "hello";
         output << i << ' ' << d << ' ' << str;
         std::string result = output.str();
         std::cout << "Resulting string: " << result << std::endl;
         return 0;
     }
     ```

3. `stringstream`（字符串流）：
   
   - `stringstream` 具有同时输入和输出的功能，可以用于读取和写入字符串。
   - 可以将数据从字符串中读取到变量中，也可以将数据从变量写入到字符串中。
   - 示例：
     ```cpp
     #include <iostream>
     #include <sstream>
     
     int main() {
         std::string s = "42 3.14 hello";
         std::stringstream input(s);
         int i;
         double d;
         std::string str;
         input >> i >> d >> str;
         std::cout << "Parsed values: " << i << ", " << d << ", " << str << std::endl;
     
         std::stringstream output;
         int x = 10;
         double y = 2.5;
         std::string z = "world";
         output << x << ' ' << y << ' ' << z;
         std::string result = output.str();
         std::cout << "Resulting string: " << result << std::endl;
         return 0;
     }
     ```

总之，这些字符串流类允许你在内存中轻松处理字符串数据，无论是将数据从字符串中提取还是将数据构建成字符串。你可以根据需要选择适合你任务的字符串流类型。



#### istringstream 和istream的关系

1. `istream`（输入流）：
	- `istream` 是C++标准库中的一个基类，代表通用输入流。
	- ==`istream` 用于从各种输入源（例如键盘、文件、字符串等）读取数据。==
	- `istream` 类的直接实例化不常见，通常使用其派生类，如 `cin`（标准输入流）。
2. `istringstream`（输入字符串流）：
	- `istringstream` 是 `istringstream` 类的一个派生类，专门用于从字符串中读取数据。
	- ==`istringstream` 可以将一个字符串解析为不同的数据类型，例如整数、浮点数、字符等。==
	- `istringstream` 的主要用途是在内存中从字符串提取数据，类似于从标准输入流 `cin` 中读取数据。

#### C++的输入、输出流类

C++标准库提供了丰富的输入和输出流类，用于处理输入和输出操作。这些流类是用于与不同类型的数据源（例如键盘、文件、字符串等）进行通信的工具。以下是一些常见的C++输入和输出流类：

**输入流类（用于读取数据）：**

1. `cin`（标准输入流）：
   - `cin` 是用于从标准输入设备（通常是键盘）读取数据的输入流。
   - 通常与 `>>` 运算符一起使用来从控制台接收用户输入。

2. `ifstream`（文件输入流）：
   - `ifstream` 类用于从文件中读取数据。
   - 通过打开文件并将文件流与文件关联，可以使用 `>>` 运算符从文件中读取数据。

3. `istringstream`（字符串输入流）：
   - `istringstream` 类用于从字符串中读取数据。
   - 可以将一个字符串解析为不同的数据类型，类似于 `cin`。

**输出流类（用于写入数据）：**

1. `cout`（标准输出流）：
   - `cout` 用于将数据输出到标准输出设备（通常是屏幕）。
   - 通常与 `<<` 运算符一起使用来向控制台输出信息。

2. `ofstream`（文件输出流）：
   - `ofstream` 类用于将数据写入文件。
   - 通过打开文件并将文件流与文件关联，可以使用 `<<` 运算符将数据写入文件。

3. `ostringstream`（字符串输出流）：
   - `ostringstream` 类用于将数据写入字符串。
   - 可以将各种数据类型的值转换为字符串，并将其存储在一个字符串中。

**其他流类：**

1. `stringstream`（字符串流）：
   - `stringstream` 具有输入和输出的功能，可以用于从字符串读取数据以及将数据写入字符串。
   - 通常用于在内存中对字符串进行输入和输出操作。

#### 举例

以下是一些使用C++输入和输出流类的常见案例：

**1. 从标准输入读取用户输入：**

```cpp
#include <iostream>
#include <string>

int main() {
    std::cout << "Enter your name: ";
    std::string name;
    std::cin >> name;
    std::cout << "Hello, " << name << "!" << std::endl;
    return 0;
}
```

这个程序使用 `cin` 从标准输入中读取用户输入的名称，然后使用 `cout` 将问候消息输出到屏幕上。

**2. 读取和写入文件：**

```cpp
#include <iostream>
#include <fstream>
#include <string>

int main() {
    // 写入数据到文件
    std::ofstream outFile("data.txt");
    if (outFile.is_open()) {
        outFile << "Hello, World!" << std::endl;
        outFile.close();
    }

    // 从文件读取数据
    std::ifstream inFile("data.txt");
    if (inFile.is_open()) {
        std::string line;
        while (getline(inFile, line)) {
            std::cout << "Read from file: " << line << std::endl;
        }
        inFile.close();
    }

    return 0;
}
```

这个程序演示了如何使用 `ofstream` 将数据写入文件，然后使用 `ifstream` 从文件中读取数据。

**3. 字符串流的使用：**

```cpp
#include <iostream>
#include <sstream>
#include <string>

int main() {
    std::ostringstream oss; // 创建字符串输出流
    int num = 42;
    double pi = 3.14159;
    std::string message = "Hello, World!";
    
    oss << "Number: " << num << ", Pi: " << pi << ", Message: " << message;
    
    std::string result = oss.str(); // 从字符串输出流中获取字符串
    std::cout << result << std::endl;

    std::istringstream iss(result); // 创建字符串输入流
    std::string token;
    
    while (iss >> token) {
        std::cout << "Token: " << token << std::endl;
    }

    return 0;
}
```

这个程序演示了如何使用 `ostringstream` 将数据写入字符串，然后使用 `istringstream` 从字符串中读取数据。

这些案例展示了C++中输入和输出流类的基本用法，可以根据需要进行扩展和修改，以满足不同的输入和输出需求。

### 一、**整型数组输入：**







1.在终端的一行中输入**固定数目**的整型数字，并存到数组中，中间以**空格**分隔。

示例：

- 3
- 1 2 3

```cpp
    //方法1：固定大小n   优先用方法1
    int n;
    cin >> n;
    vector<int> nums(n);
    for (int i = 0; i < n; ++i){
        cin >> nums[i];
    }
    //方法2：resize大小为n
    int n;
    cin >> n;
    vector<int> nums;
    nums.resize(n);
    for (int i = 0; i < n; ++i){
        cin >> nums[i];
    }
    //方法3：vector数组未初始化大小时，只能用push_back方式插入数据  注意  不能vector<int> nums(n)这样默认前n个数为0
    int n;
    cin >> n;
    vector<int> nums;
    for (int i = 0; i < n; ++i){
        int val;
        cin >> val;
        nums.push_back(val);
    }
```



2.在终端的一行中输入**非固定数目**的整型数字，并存到数组中，中间以**空格（或者其他单字符,./）**分隔。

示例：

- 1 2 3

```cpp

//方法1：getchar 
//代码通过cin.get()从缓存中读取一个字节，这样就扩充了cin只能用空格和TAB两个作为分隔符。
//这很精巧。发现是’\n’就知道一行结束了 
    vector<int> nums;
    int num;
    while(cin>>num){
        nums.push_back(num);
        if(getchar() == '\n')
            break;
    }
   //方法2：cin.get
    vector<int> nums;
    int num;
    while(cin>>num){
        nums.push_back(num);
        if(cin.get() == '\n')
            break;
    }
```



3.在终端的一行中输入**固定数目**的整型数字，并存到数组中，中间以**（其他单字符,./）**分隔。

示例：

- 3
- 1,2 ,3

```cpp
    int m;
    cin >>  m;
    char sep;
    vector<int> nums(m);
    
    for (int i = 0; i < m - 1; ++i){
        cin >> nums[i] >> sep;
    }
    cin >> nums[m - 1];
```



### 二、字符串输入：

1、给定**一行字符串**，每个字符串用**空格**间隔，**一个样例为一行**

示例： daa ma yello

```cpp
int main() {
	string str;
	vector<string> strs;
	while (cin >> str) {
		strs.push_back(str);
		if (getchar() == '\n') {  //控制测试样例           
			for (auto& str : strs) {
				cout << "当前单词："<< str << " ";
			}
			cout << endl;
			strs.clear();
		}
	}
	return 0;
}
```

![img](https://zhaozhao626.oss-cn-shenzhen.aliyuncs.com/zhaozhao/202309132313273.png)

2、给定**一行字符串**，每个字符串用**逗号**间隔，**一个样例为一行**

方法：使用getline 读取一整行字符串到字符串input中，然后使用字符串流stringstream，读取单个数字或者字符。每个字符中间用','间隔

```cpp
int main() {
	string input;
	while (getline(cin, input)) {  //读取一行
        vector<string> strs;
        string str;
        stringstream ss(input);
        while(getline(ss, str,',')){
            strs.push_back(str);
        }
        sort(strs.begin(), strs.end());
		for (auto& str : strs) {
			cout << str << " ";
		}
		cout << endl;
    }
	return 0;
}
```

![img](https://zhaozhao626.oss-cn-shenzhen.aliyuncs.com/zhaozhao/202309132314666.png)

3、给定**一行字符串**，每个字符串用**空格**间隔，**一个样例为一行**

```cpp
int main() {
	string input;
	while (getline(cin, input)) {  //读取一行
		stringstream data(input);  //使用字符串流
		int num = 0, sum = 0;
		while (data >> num) {
			sum += num;
		}
		cout << sum << endl;
	}
	return 0;
}
```

输入 1 2 3

输出6



[getline()与cin.getline()函数用法详解_AC-fun的博客-CSDN博客_getline(cin,s)函数用法](https://link.zhihu.com/?target=https%3A//blog.csdn.net/qq_41575507/article/details/90936476)



### 三、字符串输入到数组：

输入n行字符串，逗号分开，存到数组里

示例

3

1,2,3,3,2

4,5,6,1,3

7,8,9,3,4

```cpp
#include<bits/stdc++.h>

#define MAXN 10000005
using namespace std;


int main()
{
    int n;
    cin >> n;
    vector<vector<int>> vec(n,vector<int>(5));
    for (int i = 0; i < n;++i){//注意这里一定要有i控制，用while容易一直输入导致错误
        string s;
        cin >> s;
        replace(s.begin(), s.end(), ',', ' ');
        istringstream input(s);
        string tmp;
        for (int j = 0; j < 5;++j){//内层循环也很重要
            input >> tmp;
            vec[i][j] = stoi(tmp);
        }
    }

        for (int i = 0; i < vec.size(); i++)
        {
            for (int j = 0; j < vec[0].size(); j++)
            {
                cout << "输出是" << vec[i][j] << endl;
            }
        }
    return 0;
}
```





## ACM/OI中C++常用优化(实用/调试/技巧)代码(语法) 

