# 将微信读书划线和笔记同步到Notion
<p align="center"> 
  <kbd>
    <a href="https://annahuangna.github.io/" target="_blank"><img src="asset/cover.png">
  </a>
  </kbd>
</p>




预览效果：https://www.notion.so/2af7c981ef1281a692f6c9d103b16604?v=2af7c981ef1281e083e1000c7296b91c

## 关于 weread2notion 的几个问题处理：
### Error: Process completed with exit code 1.
- File "/home/runner/work/weread2notion/weread2notion/scripts/weread.py", line 399, in <module>
    latest_sort = get_sort()
- File "/home/runner/work/weread2notion/weread2notion/scripts/weread.py", line 225, in get_sort
    response = client.databases.query(
- AttributeError: 'DatabasesEndpoint' object has no attribute 'query'
- 我理解的意思：无法及时查询和更新数据库，所以：
#### 1.先使数据库不更新。
##### 1）删除get_sort函数
##### 2）删掉主循环中get_sort相关内容（如图所示）
<p align="center"> 
  <kbd>
    <a href="https://annahuangna.github.io/" target="_blank"><img src="asset/cancel_dissort.png">
  </a>
  </kbd>
</p>

###### 删除后的影响：
- 每次运行都会同步所有书籍，而不是只同步新添加的。

- 可能会重复处理已存在的书籍，但由于有 check(bookId) 函数会先删除已存在的记录，所以不会产生重复数据。

- 运行时间可能会更长，因为需要处理所有书籍而不是只处理新的。

#### 2. 在weread.yml中添加 pip install --upgrade notion-client（如图所示），同时在requirements.txt中添加“notion-client==1.0.0”

<p align="center"> 
  <kbd>
    <a href="https://annahuangna.github.io/" target="_blank"><img src="asset/pipstall.png">
  </a>
  </kbd>
</p>


## 使用
> [!WARNING]  
> 请不要在Page里面添加自己的笔记，有新的笔记的时候会删除原笔记重新添加。











