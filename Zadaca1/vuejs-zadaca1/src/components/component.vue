<template>
<div>
<header>
     <button v-on:click="changeAddItem" v-if="addItem"><h3>+LIST ITEM</h3></button>
    <h2 v-if="addItem">
        TO DO LIST
    </h2>
    <h2 v-if="!addItem">ADD NEW ITEM</h2>
</header>
<div v-if="addItem" >
<li  v-for="item in toDoList" :key="item.id">
    <div id="list" style="backround-color: item.color;"><div >{{item.name}}</div><button v-on:click="deleteItem(item.id)">Delete</button></div>
</li>
</div>

    
 <div class="form" v-if="!addItem">
    <h2>List Item</h2>
    <div>
        <input v-model="addName">
    </div>
    <h2>Choose a Color</h2>
    <div>
        <select v-model="pickColor" >
        <option>---- Select Color ----</option>
        <option value="red">RED</option>
        <option value="green">GREEN</option>
        <option value="blue">BLUE</option>
    </select><br>
        <button v-on:click="addNewItem">Add Item</button>
    </div>
 </div>

</div>

</template>

<script>
export default {
  
  data () {
    return {
     addItem:true,
     itemcolor:false,
     addName:"",
     pickColor:"",
     toDoList:[{id:1,name:"List1", color:"red"},
                {id:2,name:"List2",color:"green"} ,
                {id:3, name:"List3", color:"blue"}
     ]
    }
  },
  methods:{
      changeAddItem:function(){
          this.addItem=!this.addItem
      
      },
      deleteItem:function(id){
           this.toDoList = this.toDoList.filter((e)=>e.id !== id )
      },
      addNewItem:function(){
         this.toDoList.push({id:this.items.lenght+1,name:this.addName,color:this.pickColor});
    this.addName="";
    this.pickColor="";
    this.addItem=false;
      }
      
  }
}
</script>

<style>
.form{
    margin:0 auto;
    text-align: center;
    width: 40%;
}
.form button{
    float:right;
}

#list{
    width: 60%;
    margin: 30px auto;
    border-radius: 20px;
    text-align: center;
}
#list div{
    float:left;
}
#list button{
    float:right;

}

header{
   
    top:0;
    height: 70px;
   background-color:aquamarine
}
header h2{
    text-align: center;
    color: beige;
    
}
header button
{
    color: beige;
    float: right;
    background-color:cadetblue;
    border-radius: 20px;
    
}
</style>
