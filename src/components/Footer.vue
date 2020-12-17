<template>
    <div class="Footer">
        <!-- THIS IS MY FOOTER THAT HAS IMPORTANT INFROMATION -->
        <h6>Hannah Givens &copy; Dec 2020</h6>
        <p>Weather provided by: openweathermap.org</p>
    </div>
</template>

<script>
export default {
    name: "Footer",
}
</script>

<style scoped>
    .Footer{
        position: fixed;
        left: 0;
        bottom: 0;
        width: 100%;
        background-color: black;
        color: white;
        text-align: center;
    }
    p{
        font-size: 10px;
    }
    h6{
        font-size: 12px;
    }

</style>