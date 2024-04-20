<template>
    <div>
  <div>
    <b-form-group
      id="fieldset-horizontal"
      label-cols-sm="4"
      label-cols-lg="3"
      content-cols-sm
      content-cols-lg="7"
      label="Enter your firstname"
      label-for="input-horizontal"
    >
      <b-form-input id="input-horizontal" style="width: 200px;border-color: red;margin-top:15px;margin-bottom:15px" v-model="firstname"></b-form-input>
    </b-form-group>
    <b-form-group
      id="fieldset-horizontal"
      label-cols-sm="4"
      label-cols-lg="3"
      content-cols-sm
      content-cols-lg="7"
      label="Enter your lastname"
      label-for="input-horizontal"
    >
      <b-form-input id="input-horizontal" style="width: 200px;border-color: red;margin-top:15px;margin-bottom:15px" v-model="lastname"></b-form-input>
    </b-form-group>
    <b-form-group
      id="fieldset-horizontal"
      label-cols-sm="4"
      label-cols-lg="3"
      content-cols-sm
      content-cols-lg="7"
      label="Enter your email"
      label-for="input-horizontal"
    >
      <b-form-input id="input-horizontal" style="width: 200px;margin-top:15px;margin-bottom:15px" v-model="email" type="email" placeholder="exemple@gmail.com"></b-form-input>
    </b-form-group>
    <b-form-group
      id="fieldset-horizontal"
      label-cols-sm="4"
      label-cols-lg="8"
      content-cols-sm
      content-cols-lg="7"
      label="Enter your password"
      label-for="input-horizontal"
    >
      <b-form-input id="input-horizontal" style="width: 200px;border-color: red;margin-top:15px;margin-bottom:15px" v-model="password" type="password"></b-form-input>
    </b-form-group>
    <div>
  <div>
    <b-button-group>
      <b-button type="submit" style="margin-right:10px;height:35px;width:80px;background-color:green" @click="onSubmit()">Submit</b-button>
      <b-button type="reset" style="margin-left:10px;height:35px;width:80px;background-color:red" @click="onReset()">Reset</b-button>
    </b-button-group>
  </div>
</div>
  </div>
</div>
</template>
<script>
    import{BFormInput,BFormGroup,BButton,BButtonGroup}from"bootstrap-vue";
    export default {
        components:{BFormInput,BFormGroup,BButton,BButtonGroup},
        data(){
            return{
                firstname:"",
                lastname:"",
                email:"",
                password:"",
            }
        },
        methods:{
            onSubmit(){
                console.log('firstname :',this.firstname);
                console.log('lastname :',this.lastname);
                console.log('email :',this.email);
                console.log('password :',this.password);
            },
            onReset(){
                this.firstname="";
                this.lastname="";
                this.email="";
                this.password="";
            }

        }


}
    
</script>

