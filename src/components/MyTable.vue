<template>
  <div class="hello">
    <!-- {{ tableDatas[0] }} -->
    <div style="display: inline-block;margin-left:auto;margin-right:auto;">
      <!--eslint-disable-next-line-->
      <table v-for="(tableData, tableIndex) in tableDatas" style="float:left;display: inline-block;">
        <tr>
          <th>规定尺寸</th>
          <th>实际尺寸</th>
        </tr>
        <!--eslint-disable-next-line-->
        <tr v-for="(rowData,rowIndex) in tableData">
          <td><p>{{rowData.ruleSize}}</p></td>
          <td><p v-bind:class="{ 'highlight': tableIndex+1==x&&rowIndex+1==y }">{{rowData.realSize}}</p></td>
        </tr>
      </table>
      <div style="clear: both;"></div>
    </div>
    
  </div>
</template>

<script lang="ts">
import { ref, reactive,onMounted } from "vue";
const size = require("../data/size.json")
console.log(size);
function Datas(data:any, num:number) {
  let index = 0
  let array = []
  while(index < data.length) {
          array.push(data.slice(index, index += num));
      }
    return array ;
}

export default {
  setup() {
    const x = ref(1);
    const y = ref(1);
    const allSize = reactive({size}).size
    const tableDatas = Datas(allSize,10)



    onMounted(() => {
      document.onkeydown = (e) => {
        switch (e.code) {
          case 'Enter':
            if(y.value>=1&&y.value<tableDatas[x.value-1].length){
              y.value=y.value+1;
            }
            console.log("Enter",y);
            break
          case 'Tab':
            if(x.value>=1&&x.value<tableDatas.length){
              x.value=x.value+1;
            }
            e.preventDefault()
            console.log("Tab",x);
            break
          default:
            break
        }
      }
    })


    return {
      x,
      y,
      tableDatas
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
table{
  border-collapse: collapse;
  margin: 9px;
}
td, th{
border:1px solid rgb(240, 240, 240);
font-weight: normal;
width: 100px;
height: 28px;
text-align: left;
text-indent: 10px;
}
th{
  background: rgb(250, 250, 250);
}
.highlight{
  background: yellow;
}
p{
  margin: 0;
}
</style>
