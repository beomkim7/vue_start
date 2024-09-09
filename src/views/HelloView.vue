<template>
  <div>
    <p v-bind:title="msg">{{letgo}}</p>
    <p v-if="iftest=='1'">if</p>
    <p v-else-if="iftest=='2'">else if</p>
    <p v-else>else</p>
    <input type="text" v-model="iftest">
    <button @click="plus()">더하기</button>
   
    <beomkim v-bind:gridData="gridData"/>

    userId:<input type="text" v-model="userId">Id:<input type="text" v-model="Id"> Name:<input type="text" v-model="Name">
      <button v-on:click="add_data()">데이터추가</button>  
      <button v-on:click="get_data()">데이터 가져오기</button>
  </div>  
</template>

<script>
import BasicGrid from '@/components/BasicGrid.vue'
import axios from 'axios';

export default{
  name:'HelloView',
  data(){
    return{
    msg:'hello',
    letgo:'범서',
    iftest:'',
    userId:'',
    Id:'',
    Name:'',    
    gridData:{
        header:['userId','Id','Name'],
        body:[
          {'userId':'1','Id':'1','Name':'홍길동'},
          {'userId':'1','Id':'2','Name':'이몽룡'},
          {'userId':'1','Id':'3','Name':'성춘향'}
        ]
    }
    }
  },
  methods:{
    plus(){
      this.iftest++
    },
    add_data(){
      this.userId
      this.Id
      this.Name
      this.gridData.body.push({'userId':this.userId,'Id':this.Id,'Name':this.Name})
    },
    get_data(){
      axios.get('https://jsonplaceholder.typicode.com/posts')
      .then(r=>{        
        this.gridData.header = Object.keys(r.data[0])
        this.gridData.body = r.data
      })
    }
  },
  components: {
    beomkim : BasicGrid,
    //왼쪽에는 아무렇게나 이름을 지어도 된다. 이 화면에서 사용할 이름을 짓는 부분
  }
}


</script>

