<template>
  <div class="hello">
  <div class="container">
     <div class="row">
            <!-- 左侧 -->
        <div class="col-xs-6 col-sm-6">
                <div class="panel panel-success">
                      <!-- 标题 -->
                      <div class="panel-hading">
                            <h3 class="panel-title">省份{{leftData.length}}/当前选中({{rightData.length}})</h3>
                      </div>
                      <!-- 内容 -->
                      <div class="panel-body panel-height">
                          <ul>
                            <li :class="item.flag? 'selected':''" v-for="(item,index) in leftData" :key= "index.id" @click="add(item)">{{item.name}}</li>
                            <!-- <li>上海市</li>
                            <li>天津市</li>
                            <li class="selected">辽宁省</li> -->
                          </ul>
                      </div>
                </div>
        </div>
          <!-- 右侧 -->
        <div class="col-xs-6 col-sm-6">
                <div class="panel panel-success">
                      <!-- 标题 -->
                      <div class="panel-hading">
                            <h3 class="panel-title">已选省份{{rightData.length}}</h3>
                      </div>
                      <!-- 内容 -->
                      <div class="panel-body panel-height">
                          <ul>
                            <!-- 移入移出 -->
                            <!-- //<li v-for="(item,index) in leftData" :key= "index.id" @mousemove="s='show'" @mouseout="s='hide'">{{item.name}} -->
                           <li v-for="(item,index) in leftData" :key= "index.id" v-on:mousemove="s='s=index'" @mouseout="s='hide'">{{item.name}}
                                <span class="del" v-show="s==show" @click="del(v,i)">x</span>

                            </li>
                         
                            <!-- <li>天津市
                               <span class="del">x</span>
                            </li>
                          
                            <li>辽宁省
                               <span class="del">x</span>
                            </li> -->
                            
                          </ul>
                      </div>
                </div>
        </div> 
     </div>
  
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
     return{
    leftData:[
      {id:1,name:"北京1市",flag:false},
       {id:2,name:"北京2市",flag:false},
        {id:3,name:"北京3市",flag:false},
         {id:4,name:"北京4市",flag:false},
          {id:5,name:"北京5市",flag:false},
          {id:6,name:"北京5市",flag:false},
            {id:7,name:"北京1市",flag:false},
       {id:8,name:"北京2市",flag:false},
        {id:9,name:"北京3市",flag:false},
         {id:10,name:"北京4市",flag:false},
          {id:11,name:"北京5市",flag:false},
          {id:12,name:"北京5市",flag:false},
    ],
    rightData:[],
    s:'hide'
  }
  },
  methods:{
    //点击追加到右边
    add:function(item){
      item.flag=true
       //去重
  //     for(var i=0;i<this.rightData.length;i++){
  //         if(item.id==this.rightData[i].id) return
  // }
  // //filter
  // var a=this.rightData.filter(function(v){
  //   return v.id=item.id
  // })
      this.rightData.push(item)
      this.rightData=[...new Set(this.rightData)]
    },
    //删除
    del:function(v,i){
      this.rightData.splce(i,1)
      this.leftData.forEach(function(item){
        if(item.id==v.id){
           item.flag=false
        }
       
      })
    }
  },
 
  
 
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped >
.hello,html,body{
  width:100%;
  height:100%;
  display: flex;
  flex-direction: column;
 
}
*{
  margin: 0;
  padding: 0;
}
ul li{
  list-style: none;
}
.panel-height,
.panel-hading{
  width:100%;
  line-height: 30px;;
  background: silver;
  border:1px solid red;
}
.panel-hading{
  font-weight: normal;
  font-size: 14px
}
.panel-title{
  margin-left: 5px;
}
ul{
  width: 100%;
  height: 100%;;
  display: flex;
  flex-wrap: wrap;
    display: -webkit-flex;   -webkit-flex-wrap:wrap;

        justify-content: center;
  /* justify-content: space-around; */
}
li{
  width:25%;
  height: 50px;
  line-height: 50px;
  color:sandybrown;
  text-align: center;
  position: relative;
  font-size: 14px;
  display: flex;
  justify-content: center;
  /* border:1px solid #ccc; */
}
ul li :hover{
color:red;
background: #ccc;
/* border:1px solid burlywood */
}
ul li span:hover{
  color:red;
background: #ccc;
}
 .panel-height>li{
    width:25%;
  height: 50px;
  line-height: 50px;;
  color:sandybrown;
  text-align: center;
  border:1px solid #ccc;
  display: flex;
  justify-content: space-around
}
span{
  width:20px;
  height: 20px;
  text-align: center;
  display: flex;
  line-height: 20px;
  position: absolute;
  top:0;
  right: 25px;
  color:red;

}
.col-xs-6{
  width:100%;
  height: 800px;
}
.row{
  width:100%;
  height: 800px;
  display: flex;
  justify-content: space-between;
  border:1px solid red
}
</style>
