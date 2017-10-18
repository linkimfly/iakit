# iakit

无依赖 mini 组件库，只封装了 alert, toast, loading, actionSheet 等使用频率较高的组件。适用于类似 H5 活动页的简单移动端项目，不必为了使用这些组件而引入一个大而全的 UI 库和框架。

```
$ yarn add iakit
```

<table>
  <tbody>
    <tr>
      <td align="center" valign="top">
        <p>iakit.alert</p>
        <img width="210" src="./docs/alert.jpg">
      </td>
      <td align="center" valign="top">
        <p>iakit.loading</p>
        <img width="210" src="./docs/loading.jpg">
      </td>
      <td align="center" valign="top">
        <p>iakit.actionSheet</p>
        <img width="210" src="./docs/actionsheet.jpg">
      </td>
      <td align="center" valign="top">
        <p>iakit.toast</p>
        <img width="210" src="./docs/toast.jpg">
      </td>
    </tr>
  </tbody>
</table>

### `iakit.alert(title, content, buttons)`

* title: `string`，可选
* content: `string`，必选
* buttons: `array` | `function`，可选（button 结构：{ text: <String>, onClick: <Function> }）

```js
import * as iakit from 'iakit'

// demo 1.
iakit.alert('注册失败', '该邮箱已经被注册，如果有您有任何疑问请咨询客服。')

// demo 2.
iakit.alert(
  '注册失败',
  '该邮箱已经被注册，如果有您有任何疑问请咨询客服。',
  [
    { text: '取消', onClick: () => {} },
    { text: '确定', onClick: () => {} }
  ]
)
```

### `iakit.toast.showTop(content, time, callback)`

* content: `string` 必选
* time: `number` 显示多少毫秒，可选，默认 1500
* callback: `function` toast 消失后的回调，可选

```js
import * as iakit from 'iakit'

// demo 1.
iakit.toast.showTop('注册成功')

// demo 2.
iakit.toast.showCenter('注册成功', 5000)

// demo 3.
iakit.toast.showBottom('注册成功', () => {
  // do something you want
})
```


### `iakit.loading.show()`

```js
import * as iakit from 'iakit'

iakit.loading.show()

setTimeout(() => {
  iakit.oading.hide()
}, 3000)
```

## `iakit.actionSheet(options)`

#### options:
* title: `string`，可选
* options: `array` 可以操作的选项，必选（option 结构：{ text: <String>, disable: <Boolean>, onClick: <Function> }）
* destructiveIndex：`number` 危险选项的 index， 可选

```js
import * as iakit from 'iakit'

iakit.actionSheet({
  options: [
    {
      text: '我再想想',
      disable: false,
      onClick: (i, text) => {}
    },
    {
      text: '去它的(disabled)',
      disable: true
    },
    {
      text: '就这样吧',
      onClick: (i, text) => {
      }
    }
  ],
  destructiveIndex: 2,
  title: '确认要分手吗？',
  onClick(i, text) {
    // 点击了没有指定 onClick 函数的选项时，执行这个函数
  },
  onCancel() {
    // 取消了
  }
})
```
