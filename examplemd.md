# 就在这里测试 {#就在这里测试}

This file file serves as your book's preface, a great place to describe your book's content and ideas.

测试1：【github/gitbook\[可视化编辑、web、pdf、epub\] 】通过“\#锚点”方式跳转，例如

1. 跳转到本文的某标题

   * 

     [标题3](https://hltj.gitbooks.io/sandbox/content/#标题3)

     ```
     [标题3](#标题3)

     ```


2. 包含字母的一律用小写字母，包含空格的一律用“-”号

   * 

     [外部调用约定（Foreign calling conventions）](https://hltj.gitbooks.io/sandbox/content/#外部调用约定（foreign-calling-conventions）)

     ```
     [外部调用约定（Foreign calling conventions）](#外部调用约定（foreign-calling-conventions）)

     ```


3. 跳转到另外一个文件锚点，直接文件名后跟“\#锚点”

   * 

     [chapter1.md\#标记](https://hltj.gitbooks.io/sandbox/content/chapter1.html#标记)

     ```
     [chapter1.md#标记](chapter1.md#标记)

     ```


4. 特殊符号会被过滤

   * 

     [`RefCell<T>`](https://hltj.gitbooks.io/sandbox/content/#refcellt)

         [`RefCell<T>`](#refcellt)



5. 手写HTML标签`<a name=""></a>`定义的锚点可使用

   * 

     [chapter1.md\#测试手写a标签定位到代码块](https://hltj.gitbooks.io/sandbox/content/chapter1.html#测试手写a标签定位到代码块)

     ```
     [chapter1.md#测试手写a标签定位到代码块](chapter1.md#测试手写a标签定位到代码块)

     ```



# 标题1 {#标题1}

测试2：【github/gitbook\[可视化编辑、web、pdf、epub\] 】嵌套的三个反引号不能支持，外层可以用`~~~`代替。

    /// ```rust/// fn main {}/// ```fnmain {}


测试3：【github/gitbook\[可视化编辑~~、web、pdf、epub~~\] 】语法名后加“,”及参数

```
fn main {}

```

上面代码为

    ```rust,ignore
    fn main {}
    ```

测试4：【~~github~~/gitbook\[可视化编辑、web、pdf、epub\] 】脚注或尾注。

这是一句话[脚注](https://hltj.gitbooks.io/sandbox/content/#fn_脚注)。

```
这是一句话[^脚注]。

… 中间省略 …

---
[^脚注]: 脚注在这里。
```

测试5：【github/gitbook\[可视化编辑、web、pdf、epub\] 】类似引用的链接。

[Rust website](http://www.rust-lang.org/)

```
[Rust website][1]

[1]: http://www.rust-lang.org

```

## 标题2 {#标题2}

1. a

2. b

3. c

4. d

5. e

6. f

7. g

8. h

9. i


### 标题3 {#标题3}

1. a

2. b

3. c

4. d

5. e

6. f

7. g

8. h

9. i


### 外部调用约定（Foreign calling conventions） {#外部调用约定（foreign-calling-conventions）}

1. a

2. b

3. c

4. d

5. e

6. f

7. g

8. h

9. i


## `RefCell<T>` {#refcellt}

1. a

2. b

3. c

4. d

5. e

6. f

7. g

8. h

9. i


## Hello, Cargo! {#hello-cargo}

1. a

2. b

3. c

4. d

5. e

6. f

7. g

8. h

9. i




