<template>
  <header>
      <div class="container">
    
        <div class="header-left">
            <img src="@/assets/logo.png" alt="">
        </div>
        <div class="header-right">
            <input type="text" v-model.trim="searchText" @keyup.enter="$emit('performSearch', searchText)">
            <button @click.prevent="$emit('performSearch', searchText)">Search</button>
        </div>
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            searchText: '',
        }
    }
}
</script>

<style scoped lang='scss'>
    header{
        padding: 1rem 0;
        background: #000;

        .container {            
            display: flex;
            justify-content: space-between;
            align-items: center;

            input {
                margin: 5px;
                background: rgb(248, 100, 100);
                border: 2px solid rgb(255, 145, 0);
            }

            button {
                background: white;
            }
        }
    }
</style>