<template>
    <div class="Unit">
         <!-- SWITCHING TYPES OF UNTIS AS A NAV -->
        <select class="form-select" aria-label="Default select example">
            <option selected>Perferd Tempeture Units</option>
            <option value="1" v-on:click="metric()">C</option>
            <option value="2" v-on:click="imperial()">F</option>
        </select>
    </div>
</template>

<script>
export default {
    name: "Unit",
    data(){
        return{
            units:''
        }
    },
    methods:{
        // UNIT SWITCHING METHODES 
        imperial(){
            this.units = 'imperial'
            this.$emit('unit','imperial');
        },
        metric(){
            this.units = 'metric'
            this.$emit('unit','metric');
        },
    }
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