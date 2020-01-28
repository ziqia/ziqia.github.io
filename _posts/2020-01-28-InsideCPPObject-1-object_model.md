---
title: 对象模型 关于对象(Object Lessons)
tags: c++ object
---

《深度探索C++对象模型》

对象成员布局

<!--more-->

## C++对象模型(The C++ object model)

### 简单对象模型

```cpp
class Point {
public:
    Point(float xval);
    virtual ~Point();

    float x() const;
    static int PointCount();

protected:
    virtual ostream& print(ostream &os) const;

    float _x;
    static int _point_count;
};
```
Point实例的内存布局如下:
<div class="mxgraph" style="max-width:100%;border:1px solid transparent;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;resize&quot;:true,&quot;toolbar&quot;:&quot;zoom layers lightbox&quot;,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;www.draw.io\&quot; modified=\&quot;2020-01-28T06:41:31.613Z\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.130 Safari/537.36 Edg/79.0.309.71\&quot; etag=\&quot;_3WmqlIctO2WnTXY69U3\&quot; version=\&quot;12.5.8\&quot; type=\&quot;device\&quot;&gt;&lt;diagram name=\&quot;Page-1\&quot; id=\&quot;9f46799a-70d6-7492-0946-bef42562c5a5\&quot;&gt;7Vrdb+I4EP9rkO4etkpiAuWx0NJ76EnVVbrbfUJuYoh3k5hzTIF9uL/9xl/5cmhZFmhXbYUqezx2xj//ZmxP0kOTbHPL8TL5k8Uk7QVevOmh614Q+F4Q9OTPi7da0u97WrDgNDZKleCBfie2p5GuaEyKhqJgLBV02RRGLM9JJBoyzDlbN9XmLG0+dYkXxBE8RDh1pf/QWCRG6nte1fAHoYvEPPoyNA2POPq24GyVm+f1AjRXf7o5w3Yso18kOGbrmgjd9NCEMyZ0KdtMSCqxtbDpftMdraXdnORinw63d1+2/uRfMt98Cgc35OvV9P72E0J6mCecroidh7JWbC1Cao5EjuL10HidUEEeljiSrWvgBMgSkaVQ86GIU7rIoZySOVg1NqMTLshmp91+iQawjLCMCL4FFdMhHBoADcEQMvV1tVwlyEltpSwRsWHIohy6QgkKBqgfAC0Y/HKgBWiwH2ij/olA8x3MLgoBLgSDXSQEEGkjWKxpluKcNKGas1w8GKU6dBEAQzgIJGwU3PvKNAgmwY4SmsZ3eMtWcp7qwbY2Thin32FYbJ8BzVyYSAVrXdd4UCbrReWkAJ17uyZ+KbrDhTA6EUtTvCzoY2lwhvmC5mMmBMuMkp3plKbphKWMKwBsNIFRG1wq44geP6ORKaf4kaTjMirZkXKmMCwEZ9/KEKegrD3OKEl0pzijqaTN34THOMcWdI2HHxyBnf6gxc7AdelSp87Oy5O5dIdHgx96M7D4Sm4rKcPCoSggIJr01Ci3UXWBbnl8N2kLCBg0X9wpnet+JfnLINLfEVoYjAcWS5IkNI5JrkgksMCah5ItS0ZzoWAMx/ADYCfeRdgLYV4TqPtVHX5SnYsJy2F+mKpFJkDyNSn2jle7g4JLE0sLN2Z1ssLqHT9mebto8bQUfDa7lxh+sOK8rAiD12ZFx1YWA4ofO9j72cHQ5VvbwdDQYeUT5WKFZU/t4vJ2xOH/vmHrJzz4OIEdnQosP3RdWM3/I5YfHstfuJG0Pcbf02NOFscDN46L7ZLMaD5np/GVH0So487md93ZTuYmgZsdsDFlEvSuvP8UOr/9Xs7/7BANOiDyzwpRf3fYHeBM+mr+WCiXBc8iOCvF+n9ba8klom1d09jqy4pXRH7UkVA4L/JuDHegIHl8JXOE8niV4qKQJ406MGRDxeda+YsMnRATde16YyKpqmxtJQfrP9crulcQ2nrVT9VsR20diZ18ZGsNYAZsxSPy3P5lQIVj3oIcshHXVi3sWDQr4yTFgj41De5aSfMEEy133fP7YYsMeqJVjJ3uGKhklh3Iaw2kgXAGgsXH25qa2RJ3GozCFssvw2ftcvT7jRwsFLQFFcvLNfgJ4rsnvTMT/8LzRk3y+8P+C+xXtXvCKUxfXnOO7hL25cFLLqHPE+/WJY7GwstTsXB4WPw9Z/j9NbgWtqPT8ECuhaP2satly6m5NjoN1/yDiDb8YNqLTBsdyjTnmInOyjR7Wq0xrYBbNZBJXXjkU1VBGTBhq/PeftpvQu0bzvrtp3/OMzgKHLhMKnR68VgUDiwfGdF3kxFF+yb5wlPld5Cb3+n05Zm6Fcwi6c1H9OVnHObtJkaRm85w8HhjnzagoRsFOz9tGJwMNDcToRNj+q2xItkGGl9xp+jA6Lx5MuR+M2PeqTdTXJtX3E/LK1QNpeFxQIJq9aWXPqxUn9Ohm/8B&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>

### 继承

  单一继承: `class Book : public Library_entry { ... };`

  多重继承: `class iostream : public istream, public ostream { ... };`

  虚拟继承, 虚继承的类不管被派生多少次, 永远只会有一个实体subobject 
`class istream : virtual public ios { ... };`
`class ostream : virtual public ios { ... };`

### 编译器展开(一种可能)

new = malloc + ctor

ctor = 构造函数 + vptr

虚成员函数: 跳转到 p->vptr[n] 执行

非虚成员函数: 直接跳转到对应 func 执行

## 关键词差异(A keyword distinction)

组合composition的struct(继承时编译器可能添加额外的data member到base struct subobject中),
拥有与C兼容的空间布局.

## 对象差异(An object distinction)

C++程序设计支持3中设计典范(programming paradigms):
 1. 过程式procedureal model: C
 2. 抽象数据类型abstract data type, ADT: 由“抽象”和一组表达式(public接口)一起提供
 3. 面向对象object-orientated: 通过一个抽象的base class封装起来

### 内存布局

```cpp
class ZooAnimal {
public:
  ZooAnimal();
  virtual ~ZooAnimal();

  // ...
  virtual void rotate();

protected:
  int loc;
  string name;
};

ZooAnimal za("Zoey");
ZooAnimal *pza = &za;
```

<div class="mxgraph" style="max-width:100%;border:1px solid transparent;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;resize&quot;:true,&quot;toolbar&quot;:&quot;zoom layers lightbox&quot;,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;www.draw.io\&quot; modified=\&quot;2020-01-28T13:35:25.659Z\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.130 Safari/537.36 Edg/79.0.309.71\&quot; etag=\&quot;yy-MWpOSV6TiP2TufL-9\&quot; version=\&quot;12.6.1\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;MLUQBpD2WiBy1TRwVkGI\&quot; name=\&quot;Page-1\&quot;&gt;3ZfbjtMwEIafJjdISDk0TbnsaUFIIFBXC8tN5bVnE0tOHDnuaZ+eSe00TZ3Cguiuyk3l+W2PPd+MHdeLpvn2vSJl9kkyEF7os60XzbwwTEYh/tbCzgiDZGCEVHFmpKAVFvwJrOhbdcUZVJ2BWkqhedkVqSwKoLqjEaXkpjvsUYruqiVJwREWlAhX/caZzow6CpNW/wA8zZqVg+E705OTZrCNpMoIk5sjKZp70VRJqU0r305B1OwaLmbezZnew8YUFPo5E27n63H59eMN5dXt4POdSu7K6q31siZiZQPm6C30haR213rXoFByVTCovfleNNlkXMOiJLTu3WDuUct0LtAKsEkETwtsC3jE3U3WoDRHqmMrP0itZY4ddn3shu3ZwIIDLiwzkDlotcMhdkIYWcK2xIbW3LT5CpokZEe5ajRiSyQ9eG4pYsOC/AOooQO10ooXKWoFyeGiYLUsL0N19EyqyaWoRudKFYrrKdW4CzUIeqj6L1mrA4cqzYhC5Q3W7PVyjV6ba+xwXa5LrZbLH1KOC54TcT1wT26CIH7tC3bowHVgQsHG9ecfLSpIVXHa5Yexq913y3pv3B8bs23H2lnLLAPMeTOcsMRHClEp6N99eV3mR0zjHqSNpkAQzdfdbfRxtit8keaybGpg1P/JbDxUcqUo2EnHb4oTP6H/az+GguNnn/RD0H9fB4lTB+UTcUoBK1/3Hx6KWQPVc3xyzlg9faKg4k/kYe+qLoCyDmUfXDzx4lnta6VlZZ6twb85b6fJGbjHLXrJ0zZyKP8HkE8vtctBRrN95JvKb/8pRfOf&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>

 - 多态

```cpp
class Bear : public ZooAnimal {
public:
  Bear();
  virtual ~Bear();

  // ...
  virtual void rotate();

protected:
  enum Dances { ... };

  Dances dance;
  int block;
};

Bear b("Yogi");
Bear *pb = &b;
Bear &rb = *pb;
```

<div class="mxgraph" style="max-width:100%;border:1px solid transparent;" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;nav&quot;:true,&quot;resize&quot;:true,&quot;toolbar&quot;:&quot;zoom layers lightbox&quot;,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;www.draw.io\&quot; modified=\&quot;2020-01-28T13:43:56.941Z\&quot; agent=\&quot;Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.130 Safari/537.36 Edg/79.0.309.71\&quot; etag=\&quot;4gCYgfDvLOejeu-UTHEN\&quot; version=\&quot;12.6.1\&quot; type=\&quot;device\&quot;&gt;&lt;diagram id=\&quot;MLUQBpD2WiBy1TRwVkGI\&quot; name=\&quot;Page-1\&quot;&gt;1ZjLjpswFIafhk2lShjCkC5zm1aVWrXKaCp1ExlzBtwCRsbkMk9fe2xIwERN1WRGbCLz2z74fP7xJY6/yPcfOS7TLyyGzPHceO/4S8fzwqknf5Vw0MIknGgh4TTWEjoKa/oMRnSNWtMYqk5DwVgmaNkVCSsKIKKjYc7ZrtvsiWXdt5Y4AUtYE5zZ6g8ai1SrUy886p+AJmnzZnT3QdfkuGlsMqlSHLPdieSvHH/BGRO6lO8XkCl2DRfd7/5MbTswDoW4pMPDajsrv3++J7R6mHx95OFjWb03g93irDYJ/2RsVtAcq65VHbHol8KqMxCHBgtndRGDiuw6/nyXUgHrEhNVu5M+kFoq8kw+IVnEGU0KWc7gSY50vgUuqCQ8M7Jgqr0ZiKyD/dkMUctN+g1YDoIfZBPToTWN8ZpvHnfHiUMTo6Wnk9aI2JglaUMfecqCQfoPeJGFl8pUPDdj5KZIIyYEy69E1e9SvRug6g1Q9W4F1bOgVoLTIpFagXMYiVd7VKcXUg1vRdU/Z1UoxmPVoAsVoQGq7mt6dWJRJSnmUnknPTterkMr66tyDSyum20p+GZzsn2NBW5vJUDBWy+wyN62lrgg8hgmz3GqMJIltnccQOGF5wH/ZmDtrUsvspE8EPweJ1XPfXOq9tZloYQinqnbgHwiGa4qSrr0dAeIrcvAX7GcpB0MZN1oHDIs6LYbfgiFecM3pp2x7xE9DMOsWM0JmE6nl4BenHNH5CaOwDwBYcV5mZc26f+YKns/LCMZiUfWjEmHimGHEzklwAc8ntM4Vt3nHCr6jKOXUOrTKVU+LxkGcydYqli1YJW+bKLrfBf9GRo4egx9FbdbxO0tcvyQrSXdhnylnVKZsr2aa/sf/9/wV38A&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://www.draw.io/js/viewer.min.js"></script>
