# techniques Debounce
<p dir="rtl">زمانی از این تیکنیک استفاده می شود که شما میخواهید جلوگیری کنید از انجام شدن  کاری که پشت هم تکرار می شود . بصورتی که کار شروع به درخواست می شود و تا موقعی که در خواست ها تمام نشود از انجام آن خودداری میکند . بعد از آخرین درخواست به مدت زمانی که مشخص شده مکث کرده و آخرین کار را انجام میدهد .</p>

```javascript
const debounce = (func, delay) => {
  let inDebounce
  return function() {
    const context = this
    const args = arguments
    clearTimeout(inDebounce)
    inDebounce = setTimeout(() => func.apply(context, args), delay)
  }
}
```
