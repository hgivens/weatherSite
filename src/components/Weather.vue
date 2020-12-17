<template>
    <div class="Weather">
        <!-- SWITCHING TYPES OF UNTIS AS A NAV -->
        <!-- <select class="form-select" aria-label="Default select example">
            <option selected>Perferd Tempeture Units</option>
            <option value="1" v-on:click="metric()">C</option>
            <option value="2" v-on:click="imperial()">F</option>
        </select> -->


        <!--ERROR MESSAGE IF ZIP WRONG -->
        <div class="error" style="styleOfError">{{zipError}}</div>

        <!-- ZIP CODE INPUT -->
        <div class="input-group mb-3">
            <input id="input" type="text" class="form-control" placeholder="Zip Code" aria-label="Zip Code" aria-describedby="button-addon2" v-model="zip">
            <!-- onclick check for verification  -->
            <button  v-on:click="checkForm()" class="btn btn-outline-secondary" type="button" id="button-addon2">Check Your Weather</button>
        </div>

        <!--WEATHER UPDATE CARD  -->
        <div class="card" style="width: 18rem;">
            <p>{{weatherdata.name}}</p>
            <img v-bind:src="weatherimg" class="card-img-top" alt="Unavaiable">
            <div class="card-body">
                <ul class="list-group list-group-flush">
                    <li class="list-group-item">Weather Conditions: {{weatherdata.weather[0].main}}</li>
                    <li class="list-group-item">Current Temperature is: {{weatherdata.main.temp}}</li>
                    <li class="list-group-item">The high for the day is: {{weatherdata.main.temp_max}}</li>
                    <li class="list-group-item">The low for the day is: {{weatherdata.main.temp_min}}</li>
                    <li class="list-group-item">Feels Like: {{weatherdata.main.feels_like}}</li>
                  
                </ul>
            
                
        </div>
        </div>

       

              
    </div>
</template>

<script>
export default {
    name: "Weather",
    props:['weatherdata','weatherimg'],
    data(){
        return{
            zipError:'Invalaid Zip Code, Must real and contain 5 Charaters',
            styleOfError: '',
            // units:'',
            zip:''
        }
    },
    methods:
    {
        // //NAV BAR UNIT SWITCHING METHODES 
        // imperial(){
        //     this.units = 'imperial'
        //     this.$emit('unit','imperial')
        // },
        // metric(){
        //     this.units = 'metric'
        //     this.$emit('unit','metric')
        // },


        //THIS WILL CHECK THE ZIP TO SEE IF IT MATCHES THE FORMAT OF ZIPFORMAT
        checkForm(){
            if(this.zipFormat(this.zip) == true ){
                this.$emit('zip', this.zip);
               this.styleOfError = 'display: none';
          
            }else{
                this.styleOfError = 'display: inline-flex;  color: red';
            }
            
        },
        //THIS IS REGEX TO VALIDATE THE ZIP CODE 
        zipFormat(theValue){
            var validNum = /^\d{5}/;
            return validNum.test(theValue);
        }
    }
}
</script>

<style scoped>
    .Weather{
        background: rgb(181, 199, 223);
        color: rgb(22, 21, 41);
        text-align: center;
        padding: 10px;
        margin: 0px;
    }
    .error{
        color: red;
    }
    .card{
        margin-left: 40%;
    }

</style>