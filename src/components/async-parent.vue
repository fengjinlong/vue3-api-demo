<template>
  <div :class="$style.d">
    <h1>下面异步组件</h1>
    <async-child />
    <async-child2 />
  </div>
</template>
<script setup>
import { ref, defineAsyncComponent } from "vue";
import Loading from "./async-loading.vue";

//  同步引用
// import asyncChild from "./async-child.vue";

/**
 * defineAsyncComponent(fn or obj)
 * 参数
 * 1 函数 必须返回一个Promise，Promise的resolve应该返回一个组件
 * 2 对象
 */
// 传递参数是 函数
const asyncChild = defineAsyncComponent(() => {
  return new Promise((resolve, reject) => {
    let a = import("./async-child.vue");
    setTimeout(() => {
      resolve(a);
    }, 2000);
  });
});

// 参数是对象
/**
 * loader：同工厂函数；
 * loadingComponent：加载异步组件时展示的组件；
 * errorComponent：加载组件失败时展示的组件；
 * delay：显示loadingComponent之前的延迟时间，单位毫秒，默认200毫秒；
 * timeout：如果提供了timeout，并且加载组件的时间超过了设定值，将显示错误组件，默认值为Infinity（单位毫秒）；
 * suspensible：异步组件可以退出<Suspense>控制，并始终控制自己的加载状态。具体可以参考文档；
 * onError：一个函数，该函数包含4个参数，分别是 error、retry、fail和attempts
 * 这4个参数分别是 错误对象、重新加载的函数、加载程序结束的函数、已经重试的次数。
 *
 */
let n = 0;
const asyncChild2 = defineAsyncComponent({
  loader: () => {
    return new Promise((resolve, reject) => {
      let a = import("./async-child.vue");
      setTimeout(() => {
        if (n < 3) {
          n++;
          console.log("加载失败", n, " 次");

          reject(a);
        } else {
          console.log("加载成功");

          resolve(a);
        }
      }, 1000);
    });
  },
  loadingComponent: Loading,
  onError(error, retry, fail, attempts) {
    if (n < 4) {
      retry();
    }
  },
});
</script>

<style scoped module>
.d {
  border: 1px solid red;
}
</style>
