<template>
  
  <div class="black-bg" v-if="모달창열렸니== true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  
  
  <div class="menu">
      <!-- html 메뉴들 개수만큼 메뉴들을 작명에 담아 for문-->
      <!-- key는 반복문돌린 요소를 구분-->
      <!--<a v-for="(a,i) in 메뉴들" :key="i">{{a}}{{i}}</a>-->
      <a v-for="a in 메뉴들" :key="a">{{a}}</a>
  </div>

  






  <div v-for="(a,i) in 원룸들" :key="i">
    <img :src="원룸들[i].image" class="room-img">
    <!-- html 속성은 :를 붙인다-->
    <h4 @click="모달창열렸니= true">{{원룸들[i].title}}</h4>
    <!--아래 데이터보관함 값{{}} 가져온다-->
    <p>{{원룸들[i].price}}원</p>
    <!--뷰 문법@mouseover-->
    <button @click="신고수[i]++">허위매물신고</button>
    <span>신고수 : {{신고수[i]}}</span>
  </div>
  
</template>



<script>
import data from './assets/oneroom.js';

export default {
  name: 'App',
  //vue의 실시간 자동 렌더링 -아래data를 변경하면 실시간으로 자동으로 반영됨
    //데이터보관함
  data(){
    return{
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0,0,0,0],
      메뉴들 : ['Home','Shop','About'],
      products : ['역삼동원룸', '청담동원룸', '마포구원룸'],
    }
  },
  //함수
  methods : {
    increase(){
      this.신고수[this] +=1;
    }
  },

  components: {
    
  }
}
</script>

<style>

body{
  margin : 0;
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
  
.room-img{
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color: white;
  padding: 10px;
}

</style>