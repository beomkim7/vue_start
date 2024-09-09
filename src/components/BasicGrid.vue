<template>
  <div>
    <table border="1" align="center">
      <tr>
        <td v-for="(head,index) in gridData.header" v-bind:key="index">{{head}}</td>        
      </tr>
      <tr v-for="(bodys,rows) in gridData.body" v-bind:key="rows">
        <td v-for="(body,row) in Object.values(bodys)" v-bind:key="row">{{body}}</td>
      </tr>      
    </table>
    
  </div>
</template>

<script>
export default {
  name: 'BasicGrid',
  props:['gridData']
  
  
}
</script>

