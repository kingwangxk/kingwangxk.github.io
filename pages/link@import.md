# css link和@import的区别
## 最近看到有些面试题中出现诸如“css引入方式link和@import的区别”之类的题目，测试后发现搜索结果中现有的文章不够全面。下面贴出测试结果，仅供参考。
##### 说明：本文只贴出代码片段，具体测试过程可分段复制到本地测试。link引入方式文件名：link.css，@import引入方式：import.css。文本显示红色（red），证明@import样式生效，否则link样式生效。
###### 1.HTML代码片段
``` html
<div>测试link和@import的区别</div>
<link rel="stylesheet" href="link_only.css">
<div class="test1">
  link引入方式
</div>
<style type="text/css">
  @import url(import_only.css);
</style>
<div class="test2">
  @import引入方式
</div>
<link rel="stylesheet" href="link_after_import.css">
<div class="test3">
  link引入方式，@import引入方式在头部
</div>
<link rel="stylesheet" href="link_before_import.css">
<div class="test4">
  link引入方式，@import引入方式在link样式之后，@import导入无效，原因：@import导入规则必须在样式表头部最先声明。并且其后的分号是必需的，如果省略了此分号，外部样式表将无法正确导入，并会生成错误信息。
</div>
```
###### 2. css样式相关文件
``` css
/* link_only.css */
.test1 {
    color: burlywood;
}

/* import_only.css */
.test2 {
    color: red;
}

/* link_after_import.css */
@import url(import_before.css);
.test3 {
    color: burlywood;
}

/* import_before.css */
.test3 {
    color: red;
}
/* link_before_import.css */
.test4 {
    color: burlywood;
}
@import url(import_after.css);

/* import_after.css */
.test4 {
    color: red;
}
```
