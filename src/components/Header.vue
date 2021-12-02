<template>
  <header>
      <div class="container">
    
        <div class="header-left">
            <img src="@/assets/logo.png" alt="">
            <button @click.prevent="change('all')">Home</button>
            <button @click.prevent="change('movies')">Movies</button>
            <button @click.prevent="change('Tvs')">Tvs</button>
        </div>
        <div class="header-right">
            <input type="text" v-model.trim="searchText" @keyup.enter="$emit('performSearch', searchText, datas)">
            <button @click.prevent="$emit('performSearch', searchText, datas)">Search</button>
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
            datas: 'all',
        }
    },
    methods: {
        change(info) {
            this.datas = info;
            this.$emit('performSearch', this.searchText, this.datas);
        }
    }
}
</script>

<style scoped lang='scss'>
    header{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 120px;
        padding: 1rem 0;
        background: rgba(0, 0, 0, .9);
        z-index: 2;

        .container {            
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 100%;

            img {
                margin-right: 20px;
            }

            input {
                background: rgb(248, 100, 100);
                border: 2px solid rgb(255, 145, 0);
            }

            button {
                background: rgba($color: #fff, $alpha: .5);
                border: 1px solid black;
                border-radius: 5px;
                box-shadow: 5px 5px 5px rgba($color: #fff, $alpha: .2);
                margin: 5px;
                padding: 5px 10px;
                transition: background .15s ease-out;

                &:active {
                    background: rgba($color: #fff, $alpha: .8);
                }
            }
        }
    }
</style>