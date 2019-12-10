## 分析
- 好处：稳定减少3%键盘磨损
- 坏处：偶而引起bug

## DEMO
```js
const makeTrouble = () => {
	console.log('我没有被调用')
	return [1, 2, 3, 4]
}
let func = undefined || makeTrouble
(undefined || []).forEach(item => {
	console.log(item)
})
```
### 参考资料
https://github.com/Fundebug/fundebug-blog/issues/7
