《Python编程从入门到实践》

这本书挺有意思的，涉及的知识虽然不深入，但是实例，知识点安排都很合理。

# Cheat Sheet

## 1 起步
安装环境

## 2 变量和简单数据类型
- 变量

  **命名采用小写字母，用下划线分割**。如 `name_length`

- 字符串
  - title()函数，将字符串单词**首字母大写**
  - strip(), 去除首尾的空格
  
- 数字
  - 整数
  - 浮点数
  
- 注释

## 3 列表
- **列表是动态的，可修改**
- 访问列表：索引，从 0 开始 student[0]. 可以使用 -1 来访问倒数第一个元素
- 列表增删改
  - 修改 student[0] = 'new value'
  - 添加
    - 末尾增加 list.append('new value')
    - 任意位置插入 list.insert(索引0, 'new value')
  - 删除
    - 知道索引 del list(0), list.pop(索引 0)
    
    - 不知道索引 name = list.pop()  **弹出最后一个值，并返回弹出值给name**
      
      - list.remove('old value')  **根据值删除 如果列表内多个相同值，只会删除第一个**
      
      ```text
      pop()  和 append() 常常配合一起使用
      比如：
        已经有一个list   sizes = [10, 20, 30, 40]
        先用pop从末尾弹出元素，并用变量接收   size = sizes.pop()
        准备一个空list  numbers = []
        然后将弹出的值装进去  numbers.append(size)
      ```
  - 练习
  ```python
  # 练习 3-4
  friend = ['Alice', 'Bob', 'John']
  print(friend)

  # 练习 3-5
  print('Bob无法参加')
  friend[1] = 'Smith'
  print(friend)

  # 练习 3-6
  print('找到了一个更大的场地')
  friend.insert(0, '小米')
  friend.insert(2, '小花')
  friend.append('小红')
  print(friend)

  # 练习 3-7
  print('只能两位参加')
  friend.pop()
  friend.pop()
  friend.pop()
  friend.pop()

  print(friend[0], friend[-1])
  del friend[0]
  del friend[-1]
  print(friend)

  # 输出结果：
  """
  ['Alice', 'Bob', 'John']
  Bob无法参加
  ['Alice', 'Smith', 'John']
  找到了一个更大的场地
  ['小米', 'Alice', '小花', 'Smith', 'John', '小红']
  只能两位参加
  小米 Alice
  []
  """
  ```
- 列表排序
  - 永久性排序
    - list.sort()  # 按照字母排序 倒排：sort(reverse=True)
    - list.reverse()  # 反转元素
  - **临时排序**
    - sorted(list)   # 原 list 元素顺序不变
- 列表长度 使用 len(list)

## 4 操作列表
- for 循环遍历列表
  - for ele in list:   ele变量在 for 循环外依然存在？
  - 注意代码缩进
  
- 创建数字列表: 使用 range() 函数，可指定起始值(默认从 0 开始)，结束值(不包含在内)，步长(默认为 1)
  - 利用 list() 函数将结果变为列表  `number = list(range(2, 6, 2))  # 数字列表`
  - 统计计算：max(list), min(list), sum(list)
  
- **列表解析**：①for 循环提供值；②存储值

  ```python
  # 示例：nums = [value for value in range(10)]  前后value一致
  numbers = [value ** 3 for value in range(10)]
  # 输出：[0, 1, 8, 27, 64, 125, 216, 343, 512, 729]
  ```

- **切片**：获取列表的一部分内容

  - 利用负索引切片  `print(numbers[-3:])  # 输出: [343, 512, 729]`

  - **复制列表**

    ```python
    numbers = [value ** 3 for value in range(10)]
    nums = numbers  # 不是复制新的列表,只是将 numbers 的值赋给 nums,两个变量指向的内容是一致的
    print(id(nums))  # 返回变量的内存地址 唯一
    print(id(numbers))
    
    # 创建新 list 的两种方法：切片和 list()
    nums = numbers[:]
    print(id(nums))
    
    nums = list(numbers)
    print(id(nums))
    ```
- 元组

  - 元组同样使用索引访问

  - **注意：即使元组内只有一个元素，后面也要跟上 `,`. 如： sizes = (10,)**

  - **元组内元素是不可修改，元组本身是可以重新赋值的**

    ```python
    size = (10, 20)
    size[0] = 30   # 运行时报错
    
    size = (20, 10)  # 这是可以的，新建了一个元组
    ```

  - 定义元组

    ```python
    size = (20, 10)  # 使用圆括号
    
    # 和list相似，同样可以使用索引来访问元素
    print(size[0])
    print(size[1])
    
    # 使用for循环遍历元组
    for value in size:
        print(value)
    ```

- 设置代码格式

  遵循 PEP 8 规范

## 5 if语句

- 变量比较

  `==` 判断， 区分字母大小写

- **检查特定值是否包含在列表中**

  - 使用关键词 `in`

    ```python
    sizes = [10, 20, 30, 40]
    is_true = 10 in sizes
    print(is_true)  # True
    
    # 检查特定值是否包含在列表内
    sizes = [10, 20, 30, 40]
    is_true = 10 not in sizes
    print(is_true)  # False
    ```

- **将list用作条件表达式时，list不为空时返回True，否则返回False**

  ```python
  sizes = []
  
  if sizes:
      print('列表不为空')
  else:
      print('列表为空')
  ```

## 6 字典

- 字典是一种动态结构

- 删除键值对

  - del list['key name']

- **遍历字典**

  - **遍历所有的键值对**

    ```python
    info = {
        'name': '张三',
        'age': 20,
        'Class': '201'
    }
    
    for key, value in info.items():
        print(key + ":", value)
        
    """输出
    name: 张三
    age: 20
    Class: 201
    """
    ```

  - **遍历字典中的所有键**

    **keys() 返回键列表**

    遍历字典时，默认遍历所有的键
    
    ```python
    info = {
        'name': '张三',
        'age': 20,
        'Class': '201'
    }
    
    for key in info.keys():   # keys() 返回的是列表
        print('基本信息：' + key)
    
    """输出
    基本信息：name
    基本信息：age
  基本信息：Class
    """
    
    # 判断键值对是否存在
    info = {
        'name': '张三',
        'age': 20,
        'Class': '201'
    }
    
    if 'address' not in info.keys():
        print('没有地址信息')
    ```
    
  - 按顺序遍历字典中的所有键
  
  使用sorted()进行排序
  
  ```python
    info = {
        'name': '张三',
        'age': 20,
        'Class': '201'
    }
    
    for key in sorted(info.keys()):
        print(key)
    ```
  
- **遍历字典中的所有值**
  
  values() 返回值列表
  
  ```python
    info = {
        'name': '张三',
        'age': 20,
        'Class': '201'
    }
    
    for value in info.values():   # 没有考虑值重复
        print(value)
    ```
  
  使用 `set()` 去除重复值 
  
  ```python
    info = {
        'name': '张三',
        'age': 20,
        'Class': '201',
        'NO.': '201'
    }
    
    for value in set(info.values()):   # 使用set提取不同的值
        print(value)
    ```

## 7 用户输入和while循环

- input()

- 设置标志符

  ```python
  active = True
  while active:
      ...
  ```

  ```python
  sizes = [10, 20, 30]
  while sizes: # list不为空时返回True
  ```

## 8 函数

- 每个函数都只应负责一项具体的工作

- 传递实参

  - 位置实参

    依次按顺序传入参数

    ```python
    def dowork(name, age):
        ...
    
    dowork('张三', 20) 
    ```

  - 关键字实参

    ```python
    def dowork(name, age):
        ...
    
    dowork(name='张三', age=20)    
    
    # 通过指定形参名，可以无视参数顺序
    ```

  - 默认值

    **当形参设定默认值时，如果有实参传入，则用实参值代替，否则函数体内为默认值**

    ```python
    def f(b, a=1):   # 指定默认值的形参必须位于普通形参后面
        print(a + b)
    
    f(2)  # 按顺序给形参赋值
    ```

    注意：函数设置默认值通常是有用的。在调用的时候，如果没有此参数，无需传入。如：

    ```python
    def get_full_name(first_name, last_name, middle_name=''):
        if middle_name:   #  非空时为True
            full_name = first_name + middle_name + last_name
        else:
            full_name = first_name + last_name
        print(full_name)
    
    get_full_name('jimi', 'hendrix')
    ```

    > 一个技巧：如果参数传入list时，又不希望list被更改，可以传入list的副本。即：`list_name[:]` 作为参数传入。

- **传递任意数量的实参**

  - **在形参变量名前添加 `*` . python 会创建一个元组来接收任意个数参数(传入0个实参也是可以的)**

    ```python
    def get_num(*num):
        print(num)
    
    get_num(101)
    get_num(10, 20, 30)
    
    """输出：
    (101,)
    (10, 20, 30)
    """
    ```

  - 位置实参+任意数量实参

    ```python
    def get_num(size, *num):
        print(size, end='')
        print(num)
    
    
    get_num(101)
    get_num(10, 20, 30)
    
    """输出：
    101()
    10(20, 30)
    """
    ```

  - **使用任意数量的关键字实参**

    注：变量名前添加2个 * ，python会创建字典来接收参数。

    ```python
    def build_profile(first_name, last_name, **user_info):
        profile = {'first_name': first_name, 'last_name': last_name}
        for key, value in user_info.items():
            profile[key] = value
        return profile
    
    
    # user_profile = build_profile('albert', 'einstein')  # 不传入也是可以的
    user_profile = build_profile('albert', 'einstein', location='princeton', field='physics')
    print(user_profile)
    
    """输出：
    {'first_name': 'albert', 'last_name': 'einstein'}
    {'first_name': 'albert', 'last_name': 'einstein', 'location': 'princeton', 'field': 'physics'}
    """
    ```

- **导入模块**

  - import module_name
    - 使用模块内的函数  module_name.func_name([optional])
    - python隐式地复制模块中的所有函数
    - 使用 `as` 给模块指定别名
      - import module_name as mn
  - from module_name import func_name1, func_name2,...
    - 使用函数  func_name1([optional])
    - 显示的指定部分函数
    - 可使用 `as` 指定函数别名
      - from module_name import func_name as fn
    - from module_name import *  [不建议使用，可能会覆盖函数]

## 9 类

- **类的解释**

  ```python
  class Dog():
      """
       理解：
       1. 首字母大写的变量是类，类中的函数叫方法
       __init(self)__ 是一个特殊的方法，创建实例时，都会自动运行
       形参 self 必不可少，创建实例时，将自动传入实参self， 所以形参必不可少。每个与类相关联的方法，调用的时候都会自动传入
       实参 self ，这是一个指向实例本身的引用，让实例能访问类的属性和方法。
  
       以 self 为前缀的变量都可以供类中的所有方法使用，并且可以通过实例来访问这些变量
  
       self.name = name 将形参的值存储在变量name中，然后该变量被关联到当前创建的实例。 这个变量称为属性
      """
  
      def __init__(self, name, age):
          self.name = name   # 实例属性
          self.age = age
          self.height = 10   # 给属性指定默认值
  
      def sit(self):
          print(self.name + '在坐着')
  
      def roll_over(self):
          print(str(self.age) + '岁的' + self.name + '在打滚')
  
  
  """
  创建实例
  调用 Dog 类的 __init()__ 方法，将小黑，2岁分别赋值给变量 name, age.
  隐式的返回实例，并存储在变量 my_dog 中
  """
  my_dog = Dog('小黑', 2)
  print(my_dog.name, my_dog.age)
  my_dog.sit()
  my_dog.roll_over()
  ```

- 修改属性的值

  - 直接修改—在实例中

    ```python
    # 句点表示法
    
    my_dog.height = 15   # 先获取属性值，再重新赋值
    ```

  - 通过方法修改—在类中

    ```python
    def update_height(self, new_height):
        self.height = new_height
    
    my_dog.update_height(15)
    ```

  - 通过方法对属性值进行递增

    增量改变

    ```python
    # 每个月长高1cm
    def incr_height(self, incr):
        self.height += incr
    
    my_dog.update_height(15)  # 先设置起始值为 15
    my_dog.incr_height(1)  # 这个月长高了1cm
    ```

- **继承**

  ```python
  """
  1.创建子类
  创建子类时，父类必须包含在当前文件中，且位于子类前面
  """
  class superclass():
      def __init__(self, name, age):
          self.name = name
          self.age = age
  
      def desc_name(self):
          print(self.name)
  
  class subclass(superclass):   # 必须在括号中注明父类
      def __init__(self, name, age):
          # 给父类的所有属性赋值
          # super()用来调用父类的__init()__  让子类拥有父类的所有属性
          super().__init__(name, age)
  
  # 创建子类实例
  my_subclass = subclass('小明', 10)
  my_subclass.desc_name()   # 子类拥有父类所有的属性和方法
  ```

  ```python
  """
  2.给子类定义属性和方法
  """
  
  class subclass(superclass):   # 必须在括号中注明父类
      def __init__(self, name, age): # 需要包含父类所有的属性
          # super()用来调用父类的__init()__  让子类拥有父类的所有属性
          super().__init__(name, age)
          
          # 定义子类自己的属性
          self.teacher = '李明'
          
      # 定义子类自己的方法
      def describe_teacher(self):
          print(self.teacher + '是一个语文老师')
  
  # 创建子类实例
  my_subclass = subclass('小明', 10)
  my_subclass.desc_name()   # 子类拥有父类所有的属性和方法
  
  # 调用子类自己的方法
  my_subclass.describe_teacher()
  
  # 注： 如果一个属性或方法是任何汽车都有的，而不是子类特有的，应该将其放到父类中。只在子类中处理特有的方法和属性
  ```

  ```python
  """
  3. 重写父类的方法
  如果父类含有的方法和子类不符合，可以对其重写
  方法名一样。
  """
  class subclass(superclass):
      def desc_name(self):   # 方法名一致
          print('重写父类方法')
  
  # 让子类保留从父类那里继承而来的精华，并剔除不需要的糟粕        
  ```

  ```python
  """
  4. 将实例用作属性
  将子类冗长的属性和方法抽取为一个单独的类, 不继承于任何一个类
  """
  # 抽取类
  class detailclass():
      def __init__(self, size=70):
          self.size = size   # 初始化属性，当没有参数传入时，size默认为70，有参数传入时，赋值为实参值
      def desc_size(self):
          print(self.size)
  
  # 子类
  class subclass(superclass):   # 必须在括号中注明父类
      def __init__(self, name, age):  # 需要包含父类所有的属性
          # super()用来调用父类的__init()__  让子类拥有父类的所有属性
          super().__init__(name, age)
          
          # 定义子类自己的属性
          self.teacher = '李明'
          # 将实例用作子类的属性
          self.detail = detailclass()
          
      # 定义子类自己的方法
      def describe_teacher(self):
          print(self.teacher + '是一个语文老师')
  
  # 创建子类实例
  my_subclass = subclass('小明', 10)
  my_subclass.desc_name()   # 子类拥有父类所有的属性和方法
  
  # 调用子类自己的方法
  my_subclass.detail.desc_size(50)  # 子类实例调用抽取类方法
  ```