
#  页面显示隐藏监听

```js
const hidden = 'hidden' in document ? 'hidden' :
  'webkitHidden' in document ? 'webkitHidden' :
    'mozHidden' in document ? 'mozHidden' :
      'msHidden' in document ? 'msHidden' : '';

if (hidden) {
  const visibilityChange = hidden.replace(/hidden/i, 'visibilitychange')
  document.addEventListener(visibilityChange, () => {
    console.log('banke page ' + (document[hidden] ? 'onHide' : 'onShow'));
    if (!document[hidden]) {
      // 页面显示
      document.dispatchEvent(new Event('onShow'))
    } else {
      // 页面不可见
      document.dispatchEvent(new Event('onHide'))
    }
  }, false)
}
```


## 监听处理

vue组件监听处理

```js
export default {
    mounted() {
    document.addEventListener("onHide", this.hanlder, false);
    document.addEventListener("onShow", this.hanlder, false);
  },
  beforeDestroy() {
    document.removeEventListener('onHide', this.hanlder)
    document.removeEventListener('onShow', this.hanlder)
  },
  methods:{
      hanlder(e){
          console.log(e.type)
      }
  }
}
```