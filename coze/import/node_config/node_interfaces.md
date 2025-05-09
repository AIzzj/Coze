# Coze平台节点界面详细说明

本文档详细记录了Coze平台各类节点的界面组成、参数配置和使用方法，基于实际界面截图整理。

## 1. 代码节点界面

代码节点用于编写代码，处理输入变量并生成返回值。

### 界面组成

- **顶部标题栏**：显示"代码"标题，右侧有播放、更多选项和关闭按钮
- **功能描述**：编写代码，处理输入变量并生成返回值

### 输入部分

- **标题**：输入 (带信息图标)
- **参数表格**：
  - 参数名列：显示"input"
  - 参数值列：显示"str."下拉选择框，右侧有"输入或引用参数值"输入框
  - 操作按钮：引用按钮和删除按钮
- **添加按钮**：右上角"+"按钮，用于添加新参数

### 代码部分

- **标题**：代码 (带信息图标)
- **IDE按钮**：右上角"在IDE中编辑"按钮
- **代码编辑区**：
  - 行号显示
  - 语法高亮
  - 注释说明：
    ```javascript
    // 在这里，您可以通过 'params' 获取输入参数
    // 'params' 和 'ret' 已经被正确地注入
    // 下面是一个示例，获取名为input的参数
    // const input = params.input;
    // 下面是一个示例，输出一个包含多种数据类型的对象
    // const ret = { "name": "小明", "hobby": "读书" };
    
    async function main({ params }: Args) {
      // 构建输出对象
      
    }
    ```

### 输出部分

- **标题**：输出 (带信息图标)
- **变量表格**：
  - 变量名列：显示"key0"、"key1"、"key2"等
  - 变量长度：显示"4/20"等字符限制
  - 变量类型：下拉选择框，显示"str.String"、"[].Array"、"{}.Object"等
  - 操作按钮：问号图标和删除按钮
- **嵌套结构**：Object类型可展开，显示子属性如"key21"
- **添加按钮**：右上角"+"按钮，用于添加新输出变量

### 异常忽略

- **标题**：异常忽略 (带信息图标)
- **开关**：右侧滑动开关
- **说明**：忽略异常并在异常发生时使用默认输出替代

## 2. 选择器节点界面

选择器节点用于连接多个下游分支，根据设定条件选择执行路径。

### 界面组成

- **顶部标题栏**：显示"IF 选择器"标题，右侧有更多选项和关闭按钮
- **功能描述**：连接多个下游分支，若设定的条件成立则仅运行对应的分支，若均不成立则只运行"否则"分支

### 条件分支部分

- **标题**：条件分支 (带添加按钮)
- **条件卡片**：
  - 标题：显示"如果"
  - 删除按钮：右上角删除图标
  - 条件设置：
    - 条件参数：下拉选择框"请选择"
    - 条件操作符：下拉选择框
    - 条件值：输入框"str. 输入或引用参数值"
    - 添加按钮：底部"+ 新增"按钮，用于添加多个条件

### 否则分支部分

- **标题**：否则
- **说明**：当所有条件不满足时执行的默认分支

## 3. 意图识别节点界面

意图识别节点用于用户输入的意图识别，将用户输入与预设意图进行匹配。

### 界面组成

- **顶部标题栏**：显示"意图识别"标题，右侧有播放、更多选项和关闭按钮
- **功能描述**：用于用户输入的意图识别，并将其与预设意图选项进行匹配

### 模式选择

- **模式选项**：
  - 极速模式：左侧按钮
  - 完整模式：右侧按钮

### 输入部分

- **标题**：输入 (带信息图标)
- **参数表格**：
  - 参数名列：显示"query"
  - 参数值列：显示"str."下拉选择框，右侧有"输入或引用参数值"输入框
  - 操作按钮：引用按钮

### 意图匹配部分

- **标题**：意图匹配 (带信息图标和添加按钮)
- **意图输入框**：
  - 文本框：显示"请输入用户意图的描述，如星座问题等"
  - 删除按钮：右侧删除图标
- **其他意图**：未匹配到预设意图时的默认分类

### 输出部分

- **标题**：输出 (带信息图标)
- **输出变量**：
  - 变量名：显示"classificationId"
  - 变量类型：显示"Integer"

## 4. 循环节点界面

循环节点用于通过设定循环次数和逻辑，重复执行一系列任务。

### 界面组成

- **顶部标题栏**：显示"循环"标题，右侧有播放、更多选项和关闭按钮
- **功能描述**：用于通过设定循环次数和逻辑，重复执行一系列任务

### 循环设置

- **标题**：循环设置
- **循环类型**：
  - 标题：循环类型 (带信息图标)
  - 下拉选择框：显示"使用数组循环"

### 循环数据

- **标题**：循环数据 (带信息图标和添加按钮)
- **参数表格**：
  - 参数名列：显示"input"
  - 参数值列：显示"[str]"下拉选择框，右侧有"输入或引用参数值"输入框
  - 操作按钮：引用按钮和删除按钮

### 中间变量

- **标题**：中间变量 (带信息图标和添加按钮)
- **参数表格**：
  - 参数名列：用于定义循环过程中的临时变量
  - 参数值列：用于设置变量值

### 输出部分

- **标题**：输出 (带信息图标和添加按钮)
- **参数表格**：
  - 参数名列：显示"output"
  - 参数值列：显示"str."下拉选择框，右侧有"引用参数值"输入框
  - 变量类型：显示"新数据"
  - 操作按钮：删除按钮

## 5. 批处理节点界面

批处理节点用于通过设定批量运行次数和逻辑，运行批处理体内的任务。

### 界面组成

- **顶部标题栏**：显示"批处理"标题，右侧有播放、更多选项和关闭按钮
- **功能描述**：通过设定批量运行次数和逻辑，运行批处理体内的任务

### 批处理设置

- **标题**：批处理设置 (带信息图标)
- **并行运行数量**：
  - 标题：并行运行数量 (带信息图标)
  - 输入框：显示"int. 10"，右侧有引用按钮
- **批处理次数上限**：
  - 标题：批处理次数上限 (带信息图标)
  - 输入框：显示"int. 100"，右侧有引用按钮

### 输入部分

- **标题**：输入 (带信息图标和添加按钮)
- **参数表格**：
  - 参数名列：显示"input"
  - 参数值列：显示"[str]"下拉选择框，右侧有"输入或引用参数值"输入框
  - 操作按钮：引用按钮和删除按钮

### 输出部分

- **标题**：输出 (带信息图标和添加按钮)
- **参数表格**：
  - 参数名列：显示"output"
  - 参数值列：显示"str."下拉选择框，右侧有"引用参数值"输入框
  - 变量类型：显示"新数据"
  - 操作按钮：删除按钮

## 节点界面通用元素

### 顶部标题栏

- **节点图标**：左侧显示节点类型图标
- **节点名称**：显示节点类型名称
- **操作按钮**：
  - 播放按钮：用于测试节点功能
  - 更多选项按钮：显示更多操作选项
  - 关闭按钮：关闭节点编辑界面

### 参数配置

- **参数名**：定义输入或输出参数的名称
- **参数类型**：下拉选择框，选择参数数据类型
- **参数值**：输入框，可直接输入或引用其他参数
- **引用按钮**：用于引用其他节点的输出参数
- **删除按钮**：用于删除当前参数

### 添加按钮

- **位置**：通常位于各部分的右上角
- **图标**："+"符号
- **功能**：添加新的参数、条件或配置项

## 节点界面使用技巧

1. **参数命名规范**：
   - 使用有意义的参数名，反映参数用途
   - 避免使用特殊字符和空格
   - 保持命名风格一致

2. **类型选择建议**：
   - 为参数选择最合适的数据类型
   - 使用复合类型（如对象、数组）组织相关数据
   - 注意类型匹配，避免类型转换错误

3. **界面操作技巧**：
   - 使用引用按钮快速引用其他节点输出
   - 利用添加按钮扩展配置
   - 合理组织复杂条件和嵌套结构

4. **调试方法**：
   - 使用播放按钮测试单个节点功能
   - 检查参数值和类型是否正确
   - 利用异常忽略功能处理可能的错误

## 6. 变量聚合节点界面

变量聚合节点用于对多个分支的输出进行聚合处理。

### 界面组成
- **顶部标题栏**：显示"变量聚合"标题，右侧有更多选项和关闭按钮
- **功能描述**：对多个分支的输出进行聚合处理

### 聚合策略部分
- **标题**：聚合策略 (带信息图标)
- **策略选择**：下拉框显示"返回每个分组中第一个非空的值"

### 分组配置部分
- **分组名称**：显示"Group1"
- **类型选择**：显示"str."下拉选择框
- **参数值**：显示"输入或引用参数值"输入框
- **操作按钮**：
  - 引用按钮：用于引用其他节点输出
  - 删除按钮：用于删除当前分组
- **新增按钮**：底部"+ 新增分组"按钮

## 7. SQL自定义节点界面

SQL自定义节点用于执行用户自定义的SQL操作。

### 界面组成
- **顶部标题栏**：显示"SQL自定义"标题，右侧有播放、更多选项和关闭按钮
- **功能描述**：基于用户自定义的SQL完成对数据库的增删改查操作

### 输入部分
- **标题**：输入 (带信息图标)
- **参数配置**：
  - 参数名：显示"input"
  - 参数类型：显示"str."下拉选择框
  - 参数值：显示"输入或引用参数值"输入框
  - 操作按钮：引用和删除按钮
- **添加按钮**：右上角"+"按钮

### 数据表部分
- **标题**：数据表 (带信息图标)
- **添加按钮**：右上角"+"按钮
- **提示信息**：显示"请添加数据表到此节点，仅支持添加一个数据表"

### SQL部分
- **标题**：SQL (带信息图标)
- **编辑按钮**：右上角编辑按钮
- **提示信息**：显示变量引用格式说明

### 输出部分
- **标题**：输出 (带信息图标)
- **输出配置**：
  - outputList：[{}] Array类型
  - rowNum：int. Integer类型

## 8. 新增数据节点界面

新增数据节点用于向表添加新数据记录。

### 界面组成
- **顶部标题栏**：显示"新增数据"标题，右侧有播放、更多选项和关闭按钮
- **功能描述**：向表添加新数据记录，用户输入数据内容后插入数据库

### 数据表部分
- **标题**：数据表 (带信息图标)
- **添加按钮**：右上角"+"按钮
- **提示信息**：显示"请添加数据表到此节点，仅支持添加一个数据表"

### 输出部分
- **标题**：输出 (带信息图标)
- **输出配置**：
  - outputList：[{}] Array类型
  - rowNum：int. Integer类型

## 9. 输入节点界面

输入节点用于支持中间过程的信息输入。

### 界面组成
- **顶部标题栏**：显示"输入"标题，右侧有播放、更多选项和关闭按钮
- **功能描述**：支持中间过程的信息输入

### 输入部分
- **标题**：输入 (带信息图标)
- **输入配置**：
  - 变量名列：显示"input"
  - 长度显示：显示"5/20"
  - 变量类型：显示"str. String"下拉选择框
  - 必填标记：显示必填勾选框
  - 操作按钮：
    - 引用按钮
    - 删除按钮
- **添加按钮**：右上角"+"按钮和导入按钮 