<!-- JS 동적으로 제어하는 부분 -->
<script setup>
//뷰의 ref라는 것을 이용할 거다 ref는 상태값을 관리하는 아이
import { ref } from 'vue';
/*
// count라는 변수를 생성하고 ref에서 0으로 초기값으로 가짐 
const count = ref(0);
//계속 상태값이라했는데 상태값이 달라지면 vue는 뒷단에서 처리를하고 앞에서 그부분만 수정을혼다

// 함수는 동사로 많이하고 변수는 명사로많이함
const 증가 = ()=>{
  count.value += 1;
}
const 감소 = ()=>{
  count.value -= 1;
  if(count.value<0){
    count.value=0;
  }
}
*/

const inputValue = ref('');

const todoList = ref([
{ text:'vue',done:false},
{ text:'react',done:true},
{ text:'vercel',done:false}
]);

console.log(inputValue.value);

const handleClickButton =() =>{
  todoList.value.push(inputValue.value);
  console.log(todoList.value);
}

const handleChange = (event)=>{
  const nextValue = event.target.value;
  inputValue.value = nextValue;
}

const handleClickDeleteButton = (index) => {
  todoList.value.splice(index,1)
}
const handleClickUpdateButton = () =>{

}

</script>


<!-- Html -->
<template>
  <h1> TODO LIST</h1>
  <!--
  <div>
    변하는 상태값을 뷰가 탐색할 수 있도록 {{}}
    <div> count : {{ count }}</div>
    <button @click="증가" >+</button>
    <button @click="감소" >-</button>
  </div> -->
   <input v-model="inputValue" placeholder="Todo 입력하기" />
  <!-- <input :value = "inputValue" @change="handleChange" /> -->
  <button @click="handleClickButton"> 확인 </button>
  <div class="todo-item"  v-for="(item,index) in todoList">
    <input type="checkbox"  v-model="item.done" />
    <span :class="{'done-item':item.done}">
      {{ item.text }}
    </span>
    <div>
      <button  @click="handleClickDeleteButton(index)">수정</button>
      <button @click="handleClickDeleteButton(index)">삭제</button>
    </div>  
  </div>
</template>


<!-- Css -->
<style scoped>
  h1{ /*그냥내가넣음*/
    color : yellow;
  }
  .todo-item{
    display: flex;
    flex-direction : row;
    justify-content : space-between;
    align-items: center;
    border: 1px solid gray;
    padding : 2px; /*그냥내가넣음*/
  }
  .done-item{
    text-decoration:line-through;
  }
</style>