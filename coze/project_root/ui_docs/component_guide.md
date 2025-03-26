# UI组件指南

## 1. 基础组件
### 按钮组件
- **类型**：
  - 主按钮
  - 次按钮
  - 文本按钮
  - 图标按钮
- **状态**：
  - 默认
  - 悬停
  - 点击
  - 禁用
- **示例代码**：
```html
<button class="primary-btn">
  <icon name="submit" />
  提交
</button>
```

### 输入框组件
- **类型**：
  - 单行文本
  - 多行文本
  - 密码输入
  - 数字输入
- **功能**：
  - 自动完成
  - 字数限制
  - 实时验证
- **示例代码**：
```html
<input 
  type="text"
  placeholder="请输入..."
  maxlength="100"
  @input="handleInput"
/>
```

### 选择器组件
- **类型**：
  - 下拉选择
  - 多选框
  - 单选框
  - 开关
- **功能**：
  - 搜索过滤
  - 分组选项
  - 自定义选项
- **示例代码**：
```html
<select v-model="selected">
  <option v-for="item in options">
    {{ item.label }}
  </option>
</select>
```

## 2. 复合组件
### 表单组件
- **布局**：
  - 垂直布局
  - 水平布局
  - 网格布局
- **验证**：
  - 必填验证
  - 格式验证
  - 自定义验证
- **示例代码**：
```html
<form @submit="handleSubmit">
  <form-item label="用户名">
    <input v-model="username" />
  </form-item>
</form>
```

### 表格组件
- **功能**：
  - 排序
  - 筛选
  - 分页
  - 选择
- **定制**：
  - 自定义列
  - 固定列
  - 合并单元格
- **示例代码**：
```html
<table>
  <thead>
    <tr>
      <th v-for="col in columns">
        {{ col.title }}
      </th>
    </tr>
  </thead>
</table>
```

### 对话框组件
- **类型**：
  - 信息提示
  - 确认框
  - 表单对话框
- **功能**：
  - 自定义标题
  - 自定义按钮
  - 拖拽支持
- **示例代码**：
```html
<dialog v-model="visible">
  <dialog-header>标题</dialog-header>
  <dialog-content>内容</dialog-content>
  <dialog-footer>
    <button @click="close">关闭</button>
  </dialog-footer>
</dialog>
```

## 3. 业务组件
### 搜索组件
- **功能**：
  - 关键词搜索
  - 高级搜索
  - 搜索历史
- **交互**：
  - 自动补全
  - 实时搜索
  - 结果高亮
- **示例代码**：
```html
<search-box
  v-model="keyword"
  :history="searchHistory"
  @search="handleSearch"
/>
```

### 上传组件
- **功能**：
  - 文件上传
  - 图片上传
  - 拖拽上传
- **特性**：
  - 进度显示
  - 预览功能
  - 批量上传
- **示例代码**：
```html
<upload
  :action="uploadUrl"
  :accept="fileTypes"
  @success="handleSuccess"
>
  <button>点击上传</button>
</upload>
```

### 编辑器组件
- **功能**：
  - 富文本编辑
  - Markdown编辑
  - 代码编辑
- **特性**：
  - 工具栏配置
  - 快捷键支持
  - 主题切换
- **示例代码**：
```html
<editor
  v-model="content"
  :toolbar="toolbarConfig"
  :theme="editorTheme"
/>
``` 