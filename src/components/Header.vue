<template>
    <div class="header">
        <img src="https://static2.cnodejs.org/public/images/cnodejs_light.svg" alt="">
    <ul>
        <li><a href="">首页</a></li>
        <li><a href="">新手入门</a></li>
        <li><a href="">API</a></li>
        <li><a href="">关于</a></li>
        <li><a href="">注册</a></li>
        <li><a href="">登录</a></li>
    </ul>
    </div>
</template>
<style scoped>
.header{
    background-color: #444;
    height: 50px;
}
img{
margin-left: 50px;
margin-top: 10px;
    max-width: 120px;
}
ul{
    list-style: none;
    float: right;
    margin: 4px;
}
li{
    display: inline-block;/*行内块元素*/
    padding: 10px 15px;
}
a{
    text-decoration: none;/*a默认样式*/
    color: #ccc;
    font-size: 14px;
    text-shadow: none;/*加阴影？？*/
}
</style>