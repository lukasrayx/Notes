上传图片：Command+Control + U

两张图片并排显示：

```html
<center class="half">
  <img src="img1.jpg" width="300"/>
  <img src="img2.jpg" width="300"/>
</center>
```

表格： Command+Option+T

插入一样代码 ` some code`



------

插入表格：command + T
插入代码：command + alt +c  或者'code'
代码块   '''
              我是代码
              '''
行间公式 command + Alt + b
段落：command + 0
竖线 ： command + Alt +q       
有序列表（1.  2.） ：输入数字+“.”之后输入空格 或者：command + Alt + o   
黑点标记：command + opt + u  
隔离线shift + command +  -
超链接：command + Alt + l
插入链接：command +k
下划线：command +u 
加粗：command +b
搜索：command +f

----------------------------------------

一级标题：⌘1 (command + 1)
二级标题：⌘2 (command + 2)
三级标题：⌘3 (command + 3)
四级标题：⌘4 (command + 4)
五级标题：⌘5 (command + 5)

段落：⌘o 不生效，快捷键冲突，使用⌃o (control + o)

提升标题级别：⌘= (command + =)
降低标题级别：⌘- (command + -)

表格：⌥⌘T (option + command + T)
代码块：⌥⌘C (option + command + C)
公式块：⌥⌘B (option + command + B)



引用：⌥⌘Q (option + command + Q)
有序列表：⌥⌘O (option + command + O)
无序列表：⌥⌘U (option + command + U)

任务列表：⌥⌘X (option + command + X)
列表缩进：
​ 增加缩进：⌘] ( command + ])
​ 减少缩进：⌘[ ( command + [)

链接引用：⌥⌘L (option + command + L)
脚注：⌥⌘R (option + command + R)

水平分割线：⇧⌘- (shift + command + -)

加粗：⌘B (command + B)
斜体：⌘I (command + I)
下划线：⌘U (command + U)

代码：⇧⌘(shift + command +K) 

内联公式：⌃M (control + M)
删除线：⌃~ (control + ~)      
注释：⌃- (control + -)

超链接:⌘K (command + K)
图像：⌃⌘I (control + command + U)
清除样式：⌘\ (command + )

显示/隐藏侧边栏：⇧⌘L (shift + command + L)
大纲视图：⌃⌘1 (control + command + 1)
文档列表视图：⌃⌘2 (control + command +2)
文件树视图：⌃⌘3 (control + command + 3)

```python
def deduplication(self, nums):
    for i in range(len(nums)):
        if nums[i]==self:
            return i
    i=0
    for x in nums:
        if self>x:
            i+=1
    return i
print(deduplication(5, [1,3,5,6]))
```

