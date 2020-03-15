# Technique Throttle
<p dir="rtl">این تیکنیک موقعی استفاده می شود که می خواهید از کاری که پشت سر هم تکرار می شود جلوگیری کنید برای performance بالا تر که دو حالت دارد . حالت اول به این صورت که اول درخواست یک کار انجام می شود و اگه پشت هم بزنید تا مدتی که تعیین می کنید نمی توانید در خواست کنی . اگر هم مثلا بعد 5 ثانیه در خواست کردید با انجام شدن دوباره ، باز باید 5 ثانیه منتظر بمانید . حالت دوم مث حالت اول است اگر شما آخرین در خواستتون در بازه زمانی منع شده باشد بعد از گذشت زمان اخرین درخواست را انجام می دهد.</p>

<h2 dir="rtl">حالت اول</h2>
```javascript
const throttle = (func, limit) => {
    let inThrottle
    return function () {
        const args = arguments
        const context = this
        if (!inThrottle) {
            func.apply(context, args)
            inThrottle = true
            setTimeout(() => inThrottle = false, limit)
        }
    }
}
```
<h2 dir="rtl">حالت دوم</h2>
```javascript
const throttle = (func, limit) => {
    let lastFunc
    let lastRan
    return function () {
        const context = this
        const args = arguments
        if (!lastRan) {
            func.apply(context, args)
            lastRan = Date.now()
        } else {
            clearTimeout(lastFunc)
            lastFunc = setTimeout(function () {
                if ((Date.now() - lastRan) >= limit) {
                    func.apply(context, args)
                    lastRan = Date.now()
                }
            }, limit - (Date.now() - lastRan))
        }
    }
}
```