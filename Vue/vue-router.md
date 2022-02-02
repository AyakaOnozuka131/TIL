# Vue routerについて

## 役割
vue-routerというVue.jsを利用したSPA構築で、ルーティング制御をするための公式プラグイン。
従来はマルチタイプアプリケーションだったが、ブラウザ側でできる処理はJavaScriptで終わらせるSPAができるようになる。
index.htmlを生成を行い、URL（GET）を使用して動的コンポーネントを書き換える。

[【Vue.js】Vue Routerとは？使い方と実例](https://prograshi.com/framework/vue-js/bsics-of-vue-router-and-spa/)

## URL
ルーティングを自動的に行ってくれるが、公開時にはサーバー側にhtmlを返す設定が必要となる。  
```
export default new Router({
  mode: 'history', // デフォルトがhashのため、urlに#がついてしまうのを防ぐためhistoryを設定する。
  routes: [{path: '/', component: Home}, {path: '/users', component: Users}]
});
```
[HTML5 History モード](https://router.vuejs.org/ja/guide/essentials/history-mode.html#html5-history-%E3%83%A2%E3%83%BC%E3%83%88%E3%82%99)

### リンク設定
リンクを設定するときは、  
```
<router-link to="/users">Users</router-link>
```  
を使う

パラメーターが変わった時にライフサイクルフックが変わらないことに注意する  
対処法：wathのオブジェクトに$routeを使用する
```
  wath: {
    $route(to, from) {
      console.log(to);
      console.log(from);
    }
  }
```  
