<template>
    <header class="header">
        <h1>Todo Lists</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>|
            <router-link to="/todopage">TODO</router-link>
        </div>
    </header>    
</template>
<script>
export default {
    name:"Header"
}
</script>

<style>
    .header{
        background: #333;
        color: #ffffff;
        text-align: center;
        padding: 10px;
    }

    .header a{
        color: #ffffff;
        padding-right:5px;
        text-decoration: none;
    }
    .header a:active{
        color: red;
    }
    .header a:hover{
        color: burlywood;
    }
    .router-link-active {
        text-decoration: none;
        color: red;
    }
</style>


