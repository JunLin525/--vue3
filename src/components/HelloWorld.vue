<template>
  <div class="hello">
    <div v-for="item in itemList" :key="item.id">
      <div class="item_header item_body">
              <div class="item_detail">
                  <img v-bind:src="item.imgUrl" alt="">
                  <div class="name">{{item.itemName}}</div>
              </div>
              
              <div class="price"><span>$</span>{{item.price}}</div>
              <div class="count">
                  <button @click="handleSub(item)">-</button>
                  <button @click="$event => handleSetTen(item)">10</button>
                  {{item.count}}
                  <button @click="handlePlus(item)">+</button>
              </div> 
              <div class="amount">{{item.price * item.count}}</div>
              <div class="operate">
                  <button @click="handledelete(index)">刪除</button>
              </div>
      </div>
      <!-- 您可以在這裡添加更多的項目資訊 -->
    </div>
  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  methods:{
    handleSetTen:function(item){
      console.log(item);
      if(item.count<10)
        item.count=10;
      else
        item.count+=10;
    },
    handlePlus: function(item){
    console.log(item);
    item.count++;
    },
    handleSub: function(item){
    console.log(item);
    if(item.count>1){
      item.count--;
    }
    },
    handledelete: function(index){
    this.itemList.splice(index,1);
    }, 
  },
  props: {
    items: Array
  },
 data(){
    return{
    itemList:[
      {
        id:'1',
        itemName:'優質短袖白T',
        imgUrl:'https://images.unsplash.com/photo-1534961880437-ce5ae203:3053?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=668&q=80',
        price:'500',
        count:'1'
      },
      {
        id:'2',
        itemName:'骷髏手短黑T',
        imgUrl:'https://images.unsplash.com/photo-1503342217505-b0a15ec3261c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80',
        price:'790',
        count:'1'
      },
      {
        id:'3',
        itemName:'超時尚牛仔庫',
        imgUrl:'https://images.unsplash.com/photo-1529391409740-59f2cea08bc6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1124&q=80',
        price:'1200',
        count:'1'
      },
      {
        id:'4',
        itemName:'質感褐色系大衣服',
        imgUrl:'https://images.unsplash.com/photo-1491998664548-0063bef7856c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1500&q=80',
        price:'2300',
        count:'1'
      },
    ]
    }

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
