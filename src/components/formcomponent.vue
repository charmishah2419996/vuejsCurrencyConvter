<template>
<div id="app-form">
    <h1>form component</h1>
    <form  id="form" @submit="convertMoney">
        <p>
            <label for="money">money</label>
            <input id="money" v-model="money" type="text" name="money"/>
        </p>
        <p>
            <label for="conversion">cONVERSION</label>
            <select v-model="selected">
                <option value = "UTI">USD to INR</option>
                <option value = "ITU">INR TO USD</option>
                <option  value = "GTI">GBP to INR</option>
            </select>
        </p>
        <div>{{selectedvalue}}</div>
        <div>{{result}}</div>
          <p><input type="submit" value="Submit"></p>
          

    </form>

    <input type="submit" v-on:click="showmore" value="Show more">
</div>


</template>
<script>
 import axios from 'axios';
 const api = 'https://b2cdn.automatad.com/json/2019-11-13.json';

export default{
   /* eslint-disable */
   name: 'FormComponent',
        data(){
          return {
            money :"",
             isshow:false,   
             result:"result",
             selected:"",
             selectedvalue:"",
           };
        },
        methods:{

                showmore(){
                       this.isshow=true; 
                      
                        this.$emit('isshow',this.isshow);
                },

                convertMoney(e){
                    var converter =1 ;
                    this.selectedvalue=this.selected;
                        console.log(this.selected);
                        console.log(converter);
                    axios.get(api).then((response) => {
                    switch (this.selected) {
                        
                    case "UTI" : 
                    
                    converter= response.data.conversions.USD.INR;
                 

                    break;
                    case "ITU" : 
                    converter= 1/response.data.conversions.USD.INR;
                  
                    break;
                    case "GTI" : 
                    converter= response.data.conversions.GBP.INR;
                    
                    break;
                    default:
                    converter= 1;
                    }
                        console.log(converter);


                    this.result=this.money * converter;        
                        }, (error) => {
                        console.log(error);
                        });
                    e.preventDefault();
                     },
        },
             
    }
</script>