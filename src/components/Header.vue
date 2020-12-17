<template>
    <!-- THIS IS MY HEADER FOR THE WEB PAGE -->
    <div class="header">
        <h1>{{title}}</h1><br>
    </div>
</template>

<script>
export default {
    name: "Header",
    props:['title'],
}
</script>

<style scoped>
    .header{
        background: rgb(41, 41, 41);
        color: rgb(233, 231, 230);
        text-align: center;
        padding: 10px;
        margin: 0px;
    }

</style>