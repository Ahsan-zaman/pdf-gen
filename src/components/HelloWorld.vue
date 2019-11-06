<template>
  
<div style="width:842px; height:595px; padding:20px; text-align:center; border: 10px solid #787878">
  <div style="width:792px; height:545px; padding:20px; text-align:center; border: 5px solid #787878">
        <br><br><br><br>
        <span style="font-size:50px; font-weight:bold">Certificate of Completion</span>
        <br><br>
        <span style="font-size:25px"><i>This is to certify that</i></span>
        <br><br>
        <span style="font-size:30px"><b>محمد احسان الزمان</b></span><br/><br/>
        <span style="font-size:25px"><i>has completed the course</i></span> <br/><br/>
        <span style="font-size:30px">CourseName</span> <br/><br/>
        <span style="font-size:20px">with score of <b>99%</b></span> <br/><br/><br/>
        <span style="font-size:25px"><i>dated</i></span><br>
        {{new Date().toISOString().substr(0,10)}}<br>
        <!-- <span style="font-size:30px">$dt</span> -->
  </div>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
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
</style>
