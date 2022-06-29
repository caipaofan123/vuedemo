<template>
  <div class="hello">
    <div class="container">
      <div class="imglist">
        <h3>图片列表区</h3>
        <img src="../assets/01.jpg" alt="" @mouseover="mouseoverFn(1)" @click="clickFn(1, $event)"/>
        <img src="../assets/02.jpg" alt="" @mouseover="mouseoverFn(2)" @click="clickFn(2, $event)"/>
        <img src="../assets/03.jpg" alt="" @mouseover="mouseoverFn(3)" @click="clickFn(3, $event)"/>
      </div>
      <div class="show">
        <h3>图片预览区</h3>
        <img
          v-bind:src="currentImg"
          alt=""
          style="width: 600px; height: auto"
        />
      </div>
      <div></div>
    </div>

    <div>
      <div>
        <span>选择所在地区：</span>
        <input type="radio" value="0" name="area" v-model="area" />中国大陆
        <input type="radio" value="1" name="area" v-model="area" />中国香港
      </div>
      <div>
        <span>手机号码：</span>
        <input type="text" v-model.number="phone" />
      </div>

      <div>
        <span>年龄</span>：
        <input type="text" v-model="agee" />
      </div>
      <div>
        <span>密码</span>：
        <input type="password" v-model.number="pwd" />
      </div>

      <div>
        <span>爱好：</span>
        <input type="checkbox" v-model="hobbyy" value="看书" />看书
        <input type="checkbox" v-model="hobbyy" value="学习" />学习
        <input type="checkbox" v-model="hobbyy" value="写代码" />写代码
        <input type="checkbox" v-model="hobbyy" value="游戏" />游戏
      </div>
      <div><input type="checkbox" v-model="ifre" /> 记住密码</div>
      <div>===============================================</div>
      <div>
        我来自：{{ areas[area] }}
        <br />
        手机号码是：{{ phone }}
        <br />
        年龄是：{{ agee }}
        <br />
        密码是：{{ pwd }}
        <br />
        爱好是：{{ hobbyy.join('*') }}
        <br />
        是否记住密码：{{ ifre ? '是' : '否' }}
      </div>
    </div>

    <select v-model="from">
      <option value="北京市">北京</option>
      <option value="南京市">南京</option>
      <option value="天津市">天津</option>
    </select>

    <span>爱好: </span>
    <input type="checkbox" v-model="hobby" value="抽烟" />抽烟
    <input type="checkbox" v-model="hobby" value="喝酒" />喝酒
    <input type="checkbox" v-model="hobby" value="写代码" />写代码

    <span>性别: </span>
    <input type="radio" value="男" name="sex" v-model="gender" />男
    <input type="radio" value="女" name="sex" v-model="gender" />女

    <span>自我介绍</span>
    <textarea v-model="intro"></textarea>

    <input type="text" name="" id="" :value="bdval" @input="bdFn" />
    <h3>{{ bdval }}</h3>

    <h2>{{ text }}</h2>
    <input type="text" name="" id="" v-model.number.trim.lazy="text" />
    <h1>{{ msg }}</h1>
    <button @click="fz">翻转</button>
    <input type="text" @keydown.enter="qwe" />
    <input type="text" @keydown.esc="rty" />

    <div @click="ev">
      <div @click.once.stop="evt(88, $event)">rsserfesr</div>
    </div>

    <p>商品总数 {{ count }}</p>
    <button v-on:click="count++">+1</button>
    <button v-on:click="addFn">+1</button>
    <button v-on:click="addFn1(5)">+5</button>
    <button @click="subFn">-1</button>
    <a :href="href">baidu</a>
    <img :src="image" alt="" />
    <img :src="img" alt="" />
    <img src="../assets/logo.png" alt="" />
    <h1>{{ msg }}</h1>
    <p>{{ obj.name }}</p>
    <p>{{ obj.age }}</p>
    <p>{{ obj.home }}</p>
  </div>
</template>

<script>
import img from '../assets/logo.png';

import img01 from '../assets/01.jpg';
import img02 from '../assets/02.jpg';
import img03 from '../assets/03.jpg';

export default {
  data() {
    return {
      currentImg: img01,
      pwd: 6869979879,
      phone: 146547658690,
      hobbyy: ['学习'],
      agee: '88',
      ifre: true,
      // area:'中国香港',
      area: 0,
      areas: {
        0: '中国大陆',
        1: '中国香港',
        2: '中国台湾',
      },
      gender: '',
      from: '',
      hobby: [],
      sex: '',
      intro: '',
      bdval: '',
      text: '',
      count: 0,
      msg: '你一定要这么做吗老六？',
      obj: {
        name: '快来看',
        age: 99999999,
        home: '香港',
      },
      href: 'http://www.baidu.com/',
      image:
        'http://yun.itheima.com/Upload/./Images/20210412/60741c11ab77b.jpg',
      img,
    };
  },
  methods: {
    bdFn(e) {
      this.bdval = e.target.value;
    },
    fz() {
      this.msg = this.msg.split('').reverse().join('');
    },
    rty() {
      console.log('你强');
    },
    qwe() {
      console.log('你屌');
    },
    ev(e) {
      e.preventDefault();
      // console.log(e);
      console.log('dad');
    },
    evt(val, e) {
      // console.log(e);
      // console.log(val);
      console.log('son');
    },
    addFn() {
      this.count++;
    },
    addFn1(val) {
      this.count += val;
    },
    subFn() {
      this.count--;
    },
    mouseoverFn(val) {
      // 拿到对应地址
      this.currentImg = { 1: img01, 2: img02, 3: img03 }[val];
    },
    clickFn(val,e){
      console.log(`第${val}张图${e.target.src}`);
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  color: blueviolet;
  font-style: italic;
  font-size: 70px;
}
p {
  color: violet;
  font-size: 100px;
}
.container {
  display: flex;
}
.imglist {
  border: 2px solid red;
}
.imglist img {
  width: 200px;
  height: auto;
}
.show {
  border: 2px solid red;
  margin-right: 20px;
}
</style>
