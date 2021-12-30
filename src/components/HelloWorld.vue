<template>
  <div class="hello">
      <div v-for="(item,key) in list" :key="key" id="list">
        <span style="width: 100px">{{item.name}}：</span>
        <input style="width: 300px" :v-model="item.value" :placeholder="item.placeholder"/>
        <span class="yc">{{item.errorName}}</span>
      </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      list: [{
        name: '用户名',
        value: '',
        placeholder: '请输入用户名',
        errorName: '用户名不能为空'
      },
      {
        name: '邮箱',
        value: '',
        placeholder: '请输入邮箱',
        errorName: '邮箱不能为空'
      }
      ,
      {
        name: '密码',
        value: '',
        placeholder: '请输入密码',
        errorName: '密码不能为空'
      },{
        name: '重复密码',
        value: '',
        placeholder: '请输入重复密码',
        errorName: '重复密码不能为空'
      }]
    }
  },
  mounted() {
    this.getFormatData()
  },
  methods: {
    getFormatData() {
      
      let input = document.getElementsByTagName('input');
      let span = document.getElementsByTagName('span');
      for(let i=0;i<input.length;i++) {
        input[i].addEventListener('blur',function() {
          if(this.value == '') {
            this.style.borderColor = 'red'
            span[(2*i)+1].style.color = 'red'
            span[(2*i)+1].className = ''
          }else {
               this.style.borderColor = 'black'
            span[(2*i)+1].style.color = 'black'
            span[(2*i)+1].className = 'yc'
          }
          
        })
      }
      //var t = 'fsdfsdfs1235435jo-i-4o8p23i90';
		//var reg =/8/ // /8/ 等价于new RegExp("8")
		//alert(reg.test(t))
		// 正则中最常用的修饰符
		// g(global) :全局匹配
		// i(ignore) : 忽略大小写
		//  ----- 二 ------- 全局和忽略大小写
		//reg = new RegExp("fs","g") // new RegExp("FS","ig") 等价于/FS/i
		//alert(reg.test(t))
		// ------ 三 ------- 返回的是找到的内容
		// alert(reg.exec(t))
		// ------ 四 ---------
		// search  返回指定模式的子字符串首次出现的位置
		// match  以数组的形式返回指定模式的字符串，可以返回所有匹配结果
		// replace //替换查找到的字符串
		// 以指定结果分割字符串，返回结果是数组
		
		// 子表达式
		//reg = /\d(\d)\1\1/;
		//t.match(reg)
		// 捕获
		//()
		//例题1：查找连续的四个数字，如：3567
		// /\d\d\d\d/
		// 查找数字 1221，3443
		// /(\d)\1(\d)\2
		/**
		查找字符如：AABB,TTMM
		/([A-Z])\1([A-Z])\2/

    字符簇
    [a-z]
    [A-Z]
    [0-9]

    ^脱字符  （方括号时候代表取反的意思）
    \d 匹配纯数字
    \D 配置非数字字符
    \w  匹配包括下划线的任何字母数字下划线字符还可以使用[a-zA-Z0-9_]
    \w 配置任何非字符数字下划线字符，还可以使用[^\w]
    \s 匹配任何空白字符
    \S 匹配非空空白字符
    .匹配除了\n之外的任务单个字符
    [\u4e00-\u9fa5] 匹配中文字符中的任一字符 
    * 匹配前面的子表达式零次或者多次，0-多
    + 匹配前面的子表达式一次或多次 ，1-多
    ？ 匹配前面的子表达式零次或者1次 ，0或1
    {n} 匹配确定的n次
    {n,}至少匹配n 次
    {n,m} 至少匹配n次最多匹配m次
    匹配手机号  /1[3,4,5,7,8]\d{9}/
		^匹配字符串开始的位置
    $匹配字符簇结束的位置
    \b 定位符用于单词定位
    \B 用于非定位符 非单独定位
    /\w+@\w+\.\w{2,6}/
    (?=) 预查
    (?!)\w{3} 不等于
    **/
		
    }
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.yc{
  display: none;
}
</style>
