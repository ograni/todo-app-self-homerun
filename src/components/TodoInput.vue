<template>
    <div class="inputBox shadow">
        <input type="text" 
            v-model="inputText" 
            placeholder="Type what you have to do"
            v-on:keypress.enter="addItem">
            <!-- v-model : 인풋에 입력된 값을 동적으로 뷰 안의 인스턴스와 매핑한다. -->
        <!-- <button v-on:click="addItem">add</button> -->
        <!-- v-on:click="클릭했을때 동작할 메서드 명" -->
        <span class="addContainer" v-on:click="addItem">
            <i class="addBtn fas fa-plus"></i>
        </span>
    </div>
</template>

<script>
export default {
    // input이 바라볼 data 속성을 만든다.
    data() {
        return {
            inputText: '',
        }
    },
    methods: {
        addItem() {
            var value = this.inputText;
            localStorage.setItem(value, value);
            this.$emit('add', value);
            this.clearInput();
        },
        clearInput(){
            this.inputText = '';
        }
    }
}
</script>

<style scoped>
    input:focus {
        outline: none;
    }
    .inputBox {
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input {
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: inline-block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
        }
    .addBtn {
        color: white;
        vertical-align: middle;
    }
</style>
