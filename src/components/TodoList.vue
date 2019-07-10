<template>
    <div>
        <ul>
            <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem" class="shadow">
                {{ todoItem }}
                <!-- <button v-on:click="removeItem(todoItem, index)">
                    remove
                </button> -->
                <span class="removeBtn" type="button" @click="removeItem(todoItem, index)">
                    <i class="far fa-trash-alt"></i>
                </span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props:['propsdata'],
    // data() {
    //     return {
    //         todoitems:[]
    //     }
    // },
    methods: {
        removeItem(todoItem, index) {
            this.$emit('remove', todoItem, index)
            // console.log(todoItem, index);
            // localStorage.removeItem(todoItem);
            // this.todoitems.splice(index, 1)
        }
    },
    // created () {
    //     if(localStorage.length > 0){
    //         for (var i = 0; i < localStorage.length; i++){
    //             // console.log(localStorage.key(i));  
    //             this.todoitems.push(localStorage.key(i))
    //         }
    //     };
    // },
}
</script>

<style scoped>
  ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }
  li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }
  .checkBtn {
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
  }
  .removeBtn {
    margin-left: auto;
    color: #de4343;
  }
  .list-enter-active, .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }
</style>