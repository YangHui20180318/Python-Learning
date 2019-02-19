# Python-Learning（What the f*ck Python! 学习过程）

-----------------------------------------------------------------
***目录***
-----------------------------------------------------------------
- [ection 1: Strain your brain!](#s1)
  + [>Strings can be tricky sometimes!](#s1_1)
  + [>Time for some hash brownies!](#s1_2)



-------------------------------------------------------------------
 # <s1 id ='s1'>Section 1：Strain your brain!</s1>

## <s11 id='s1_1'> >Strings can be tricky sometimes!</s11>
>  示例1 与文章一致，2,3,稍有不同

字符串的驻留与常量折叠
- 字符串驻留
&emsp;某些情况下，Cpython在编译优化时，会尝试使用***已经存在的不可变对象***，而不是每次都创建一个新对象。这样许多变量可以指向内存中的相同字符串，从而***节省内存***。
- 发生隐式驻留的情况
   - 所有长度为 0 和长度为 1 的字符串都被驻留.
   - 字符串在编译时被实现 ('wtf' 将被驻留, 但是 ''.join(['w', 't', 'f'] 将不会被驻留)
   - 字符串中只包含字母，数字或下划线时将会驻留. 所以 'wtf!' 由于包含 ! 而未被驻留. 可以在这里<https://github.com/python/cpython/blob/3.6/Objects/codeobject.c#L19>找到 CPython 对此规则的实现
- 常量折叠:常量折叠(constant folding) 是 Python 中的一种 窥孔优化(peephole optimization) 技术. 这意味着在编译时表达式 'a'*20 会被替换为 'aaaaaaaaaaaaaaaaaaaa' 以减少运行时的时钟周期. 只有长度小于 20 的字符串才会发生常量折叠. 
>

## <s12 id ='s1_2'> >Time for some hash browines! </s12>
+ Python 字典通过检查键值是否相等和哈希值来确定两个键是否相同。
+ **具有相同值的不可变对象**在python中始终具有相同的hash值
>hash(1)=hash(1.0)
