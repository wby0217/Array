### 冒泡排序
    ```
    function beble(arr) {
        var flag = false;
        for (var i=0; i<arr.length-1; i++) {
            for (var j=0; j<arr.length-1-i; j++) {
                if(arr[j] > arr[j+1]) {
                    arr[j] = arr[j] + arr[j+1]
                    arr[j+1] = arr[j] - arr[j+1]
                    arr[j] = arr[j] - arr[j+1]
                    flag = true
                }
            }
            if(flag) {
                flag = false
            } else {
                break
            }
        }
        return arr;
    }
    var arr = [1,4,3,2,5]
    var abc = beble(arr);   //输出 1, 2, 3, 4, 5
    ```

### 数组快速排序
```
    function quk(ary) {
         if(ary.length <= 1) {
             return ary;
         }
        var index = Math.floor(ary.length/2);
        var val = ary.splice(index,1)[0];
        var left =[];
        var right = [];
        for (var i=0; i<ary.length; i++) {
            var sur = ary[i];
            sur < val? left.push(sur): right.push(sur);
        }
        return quk(left).concat([val],quk(right));
    }
    var ary = [1, 3, 4, 2, 3, 1, 4, 2]
    console.log(quk(ary)) //输出 1,, 1, 2, 2, 3, 3, 4, 4
    ```

### 插入排序
```
    function pushs(ary) {
        var newArr = [];
        newArr.push(ary[0]);
        for(var i=1; i<ary.length; i++) {
            var cur = ary[i];
            for(var j = newArr.length-1; j >=0; ) {
                if(cur<newArr[j]){
                    j--;
                    if(j === -1) {
                        newArr.unshift(cur);
                    }
                } else {
                    newArr.splice(j + 1, 0 , cur);
                    j = -1;
                }
            }
        }
        return newArr;
    }

    var ary = [2, 5, 6, 7, 4, 3]；
    var arr = pushs(ary)
    console.log(arr) //2, 3, 4, 5, 6, 7
    ```

### 数组去重
```
    function fn(ary) {
        var obj = {}
        for(var i=0; i < ary.length; i++) {
            var cur = ary[i];
            if(obj[cur] == cur) {
                ary[i] = ary[ary.length-1];
                ary.length--
                i--
                continue;
            }
            obj[cur] = cur;
        }
        return ary
    }

    var ary = [1, 3, 4, 2, 3, 1, 4, 2, 1, 2, 3, 4]
    var arr = fn(ary)
    console.log(arr) // 1, 3, 4, 2
```

### 函数递归方法实现10以内被3整除的数相加
```
    function sum(n) {
        if(n == 0) {
            return 0;
        }
        if(n%3 !=0 ) {
            return sum(n-1);
        }
        return n + sum(n-1);
    }
    var add = sum(10)
    console.log(add) // 输出18
    ```

### 递归方法用 setTimeout 实现 setInterval
```
    var sum = 0;
    var timer = null;
    function move() {
        window.clearTimeout(timer)
        sum++
        console.log(sum); //输出 1 2 3 4 5 6 7 8 9 10 每秒输出一个数字
        if(sum == 10) {
            return;
        }
        timer = window.setTimeout(move,1000);
    }
    move()
    ```