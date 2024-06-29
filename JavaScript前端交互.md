## 模态窗口

`prompt`，`alert`，`confirm`，用于定义模态窗口

#### alert（警告）

一个带有提示信息，一个确认按钮的模态窗口创建函数

- 参数：`message: string`
  - `message`：提示信息

#### prompt（提示）

一个带有提示信息，输入框，一个确认按钮和一个取消按钮的模态窗口创建函数

- 参数：`message :string, [default] :string`
  - `message`：提示信息
  - `default`：可选参数，输入框默认内容
- 返回值：`null | string`
  - `null`: 点击取消按钮
  - `string`: 输入框输入的内容，输入框为空则返回空字符串""

#### confirm（确认）

一个带有提示信息，一个确认按钮和一个取消按钮的模态窗口创建函数

- 参数：`message: string``
  - `message`：提示信息
- 返回值：`boolean`
  - `true`：点击确认
  - `false`：点击取消