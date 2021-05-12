## vector容器
```cpp
//vector的初始化
vector<int> a(10); //定义了10个整型元素的向量（尖括号中为元素类型名，它可以是任何合法的数据类型），但没有给出初值，其值是不确定的。
vector<int> a(10,1); //定义了10个整型元素的向量,且给出每个元素的初值为1
vector<int> a(b); //用b向量来创建a向量，整体复制性赋值
vector<int> a(b.begin(),b.begin+3); //定义了a值为b中第0个到第2个（共3个）元素
int b[7]={1,2,3,4,5,9,8};
vector<int> a(b,b+7); //从数组中获得初值

//赋值
a.assign(b.begin(), b.begin()+3); //b为向量，将b的0~2个元素构成的向量赋给a
a.assign(4,2); //是a只含4个元素，且每个元素为2

//插入操作
a.insert(a.begin()+1,5); //在a的第1个元素（从第0个算起）的位置插入数值5，如a为1,2,3,4，插入元素后为1,5,2,3,4
a.insert(a.begin()+1,3,5); //在a的第1个元素（从第0个算起）的位置插入3个数，其值都为5
a.insert(a.begin()+1,b+3,b+6); //b为数组，在a的第1个元素（从第0个算起）的位置插入b的第3个元素到第5个元素（不包括b+6），如b为1,2,3,4,5,9,8，插入元素后为1,4,5,9,2,3,4,5,9,8

//删除操作
 a.erase(pos);//   删除pos位置的数据
 a.erase(a.begin(),a.end());// 删除[beg,end)区间的数据

//resize()函数
a.resize(15); //大小改为15，用0填充新的位置，若比原来短，删除超出的部分
a.resize(20, 13); //用13填充新的位置

a.push_back(3); // 在数组的最后添加一个数据
a.pop_back();//    去掉数组的最后一个数据
a.at(5);     //     得到编号位置的数据
a.begin();     //    得到数组头的指针
a.end();     //   得到数组的最后一个单元+1的指针
a.front();   //  得到数组头的引用
a.back();   //   得到数组的最后一个单元的引用
a.max_size();   //  得到vector最大可以是多大
a.capacity();   //   当前vector分配的大小
a.size();       //    当前使用数据的大小
a.reserve(1000);    //  预留空间为1000，改变当前vecotr所分配空间的大小
a.clear();      //    清空当前的vector
a.rbegin();     //  将vector反转后的开始指针返回(其实就是原来的end-1)
a.rend();     //  将vector反转构的结束指针返回(其实就是原来的begin-1)
a.empty();     //   判断vector是否为空
a.swap(b);      //  与另一个vector交换数据

//算法
sort(a.begin(),a.end(),greater<int>());//使用内建函数降序排列
```

## deque 容器
```cpp
//初始化
deque<int> d1; //默认构造
deque<int>d2(d1.begin(), d1.end());
deque<int>d3(10, 12); //10个12
deque<int>d4(d3); //拷贝构造

//赋值操作
d2 = d1;
d3.assign(d1.begin(), d1.end());
d4.assign(12, 13);
d1.resize(12); //用0填充,超出部分删除
d1.resize(12, 1); //用1填充

//插入操作
	d1.push_back(1); //尾插
	d1.push_front(2); //头插
	d1.pop_back(); //尾删
	d1.pop_front(); //头删
	d1.insert(d1.begin(), 3); //在起始位置插入3
	d1.insert(d1.begin(), 2, 4); //在起始位置插入2个4
	d1.insert(d1.begin(), d2.begin(), d2.end()); //将d2插入d1的起始位置

//删除操作
	deque<int>::iterator it = d1.begin();
	it++;
	d1.erase(it); //删除it位置的数据
	d1.erase(it, d1.end()); //删除区间it到尾部的数据

```

## stack 容器
先进后出，不允许遍历
```c++
stack<int>s1;  //构造
s1.push(11); //入栈
s1.push(12);
s1.pop();//出栈
```

## queue 容器
队列容器，先进先出，队尾只进，队头只出
```c++
queue<int>s1;  //构造
s1.push(11); //入栈
s1.push(12);
s1.pop();//出栈
```

## list 容器
list容器,链表，任意位置插入，删除，但是遍历速度比数组慢并且占据空间大，迭代器只支持前移或者后移不支持随机访问，是双向迭代器，不会造成内存的浪费或溢出，插入和删除不会影响原有迭代器的失效，这在vector中是不成立的。
```c++
list<int>l1; //默认构造
list<int>l2(l1.begin(), l1.end()); //按照区间构造
list<int>l3(l2); //拷贝构造
list<int>l4(10, 100); //10个100

//赋值
l2 = l1;
l3.assign(l1.begin(), l1.end());
l4.assign(10, 11);

//交换
l1.swap(l4); //l1和l4互换

l1.resize(10); //指定比原来长，用0补齐
l1.resize(10, 1); //用1补齐
l1.resize(3);//多出部分删除

//插入操作
l1.push_back(11); //尾插
l1.push_front(12); //头插
l1.pop_back(); //尾删
l1.pop_front(); //头删
l1.insert(l1.begin(), 13); 

//删除操作
l1.erase(l1.begin());

//移除
l1.remove(10000); //删除所有与输入值匹配的元素
l1.clear(); //清空

//数据存取，不可以用[]和at来访问数据
cout << "第一个元素" << l2.front() << endl;
cout << "最后一个元素" << l2.back() << endl;

//反转操作
l2.reverse();
```

## set 容器
set和multiset容器,插入时自动排序，set不允许有重复的元素，但是multiset允许
```c++
//构造与赋值
set<int>s1;
s1.insert(10); //插入数据只有insert
s1.insert(20);
s1.insert(30);
s1.insert(40);
printset(s1);
set<int>s2(s1);
set<int>s3;
s3 = s1;  //赋值
s3.insert(1);

//set 的遍历
void printset(set<int>& s)
{
	for (set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

//交换
s1.swap(s3);

//删除
s1.erase(s1.begin()); //删除第一个
s1.erase(20); //删除20
s1.clear(); //清空

//查找
set<int>::iterator pos = s1.find(10);  //返回10的迭代器
if (pos != s1.end())
{
	cout << "找到元素:" << *pos;
}
else
{
	cout << "未找到" << endl;
}

//统计
int num = s1.count(10); //查找10的个数

//默认排序为升序，指定排序规则要写仿函数来指定排序类型
set<int, Mycompare>s4;
s4.insert(45);
s4.insert(12);
s4.insert(56);
```

## map 容器
map容器和multimap容器,map不允许有重复的key值，但是multimap允许有重复的key值
```c++
//构造和赋值
map<int,int>m1;
m1.insert(pair<int, int>(1, 10)); //1为key,10为val
m1.insert(pair<int, int>(2, 20));
m1.insert(pair<int, int>(3, 30));
m1.insert(pair<int, int>(4, 40));
map<int, int>m2(m1); //拷贝构造
map<int, int>m3;
m3 = m1; //赋值

//插入
m1.insert(make_pair(5, 50));
m1.insert(pair<int, int>(6, 60));
m1.insert(map<int, int>::value_type(7, 70));
//m1[8] = 80; //不建议插数，但是可以利用[]来访问数据

//删除
m1.erase(m1.begin()); //删除第一对数
m1.erase(3); //通过key值来删整对
m1.clear(); //清空

//查找
map<int, int>::iterator pos = m1.find(3); //3为key
if (pos != m1.end())
{
	cout << "找到元素:" << (*pos).first << pos->second << endl;
}
else
{
	cout << "未找到" << endl;
}

//统计,map结果不是0就是1
int num1 = m1.count(3);

//map的遍历
void printmap(map<int,int>&m)
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << (*it).first << it->second << endl;
	}
	cout << endl;
}

//排序，默认按照kry值从小到大排
map<int, int, Mycomparemap>m4;
m4.insert(make_pair(5, 50));
m4.insert(pair<int, int>(6, 60));
m4.insert(map<int, int>::value_type(7, 70));
for (map<int, int, Mycomparemap>::iterator it = m4.begin(); it != m4.end(); it++)
{
	cout << (*it).first << it->second << endl;
}

//仿函数
//仿函数可以调用，可以有参数，可以有返回值，可以有自己的状态，可以作为参数传递
//返回值为bool的叫做谓词，operator()接受一个参数叫做一元谓词，接受两个参数叫做二元谓词
class Mycomparemap
{
public:
	bool operator()(int v1, int v2) const  //const必须加，要不然会报错
	{
		return v1 > v2;
	}
};
```

