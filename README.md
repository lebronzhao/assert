# assert

Assert模块主要用于断言。如果表达式不符合预期，就抛出一个错误

```
/**
 * Created by dllo on 17/4/20.
 */
const assert = require('assert');

assert(true);  // OK
assert(1);     // OK
assert(false);
// throws "AssertionError: false == true"
assert(0);
// throws "AssertionError: 0 == true"
assert(false, 'it\'s false');
// throws "AssertionError: it's false"

//上面代码中如果是true就会正常通过，如果为false就会抛出异常。

const obj1 = {
    a : {
        b : 1
    }
};
const obj2 = {
    a : {
        b : 2
    }
};
const obj3 = {
    a : {
        b : 1
    }
}
const obj4 = Object.create(obj1);

assert.deepEqual(obj1, obj1);
// OK, object is equal to itself

assert.deepEqual(obj1, obj2);
// AssertionError: { a: { b: 1 } } deepEqual { a: { b: 2 } }
// values of b are different

assert.deepEqual(obj1, obj3);
// OK, objects are equal

assert.deepEqual(obj1, obj4);
// AssertionError: { a: { b: 1 } } deepEqual {}
// Prototypes are ignored

//deepEqual的语法，实际上是对实际值和期待值得比较操作，类似于JavaScript中的 ==


assert.notStrictEqual(1, 2);
// 通过

assert.notStrictEqual(1, 1);
// 抛出 AssertionError: 1 !== 1

assert.notStrictEqual(1, '1');
// 通过

//使用不全等运算符（!==）测试是否不全等。
```

