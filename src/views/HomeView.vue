<template>
  <div>
  <dashboard/>
  <div class="row" style="margin-top: 100px;">         
    <div class="cols-12 col-lg-5">
      <div class="card">
        <div>
          <h3>Ajout user</h3>
        </div>
        <!--<b-form name="myForm">-->
        <div class="row" style="margin-bottom: 50px;">
      <div class="col">
        <label for="">Nom : </label>
        <b-form-input type="text" v-model="nom"> </b-form-input>
      </div>
      <div class="col">
        <label for="">Prénom : </label>
        <b-form-input type="text" v-model="prenom"> </b-form-input>
      </div>
    </div>
    <div class="row" style="margin-bottom: 50px;">
      <div class="col">
        <label for="">Email : </label>
        <b-form-input type="email" style="width:230px" v-model="email" name="email"></b-form-input>
        <small class="text-danger" id="email-validation"></small>
      </div>
      <div class="col">
        <label for="">Mot de passe : </label>
        <b-form-input type="password" v-model="password"> </b-form-input>
      </div>
    </div>
    <div style="margin-bottom: 20px;">
    <b-button-group>
      <b-button type="submit" @click="addElement()" style="margin-right:10px;height:35px;width:80px;background-color:green" @>Submit</b-button>
      <b-button type="reset" style="margin-left:10px;height:35px;width:80px;background-color:red" @click="onReset()">Reset</b-button>
      </b-button-group>
        </div>
     <!--   </b-form>-->
      </div>
    </div>
    <div class="col-12 col-lg-7">
      <div class="card">
        <div class="card-header">
          <h3>Liste</h3>
        </div>
        <div>
          <b-table :items="items" :fields="colonne">
            <template #cell(action)="{item}"> 
              <b-icon @click="deleteItem(item)" icon="trash" title="supprimer" style="margin-right: 15px;background-color: red; height: 20px; width: 20px">
              </b-icon>
              <b-icon @click="showDetail(item)" icon="pen-fill" title="modifier" style="background-color:green;height :20px; width: 20px" >
              </b-icon>
            </template>
          </b-table>
        </div>
      </div>
      <b-modal hide-header-close no-close-on-backdrop title="BootstrapVue" v-model="show" ok-title=" Confirmer" cancel-title="Quitter" @ok="confirmDelete()">
        <p class="my-4">Voulez vous vraiment supprimer l'élément sélectionné ?</p>
      </b-modal> 
      <b-modal v-model="modalShow">
        <form action="">
        <div class="row">
          <div class="col">
          <label for="">Nom :</label>
          <input type="text" v-model="nomDetail" readonly>
          </div>
          <div class="col">
          <label for="">Prénom :</label>
          <input type="text" v-model="prenomDetail" disabled>
        </div>
        </div>
        <div class="row">
          <div class="col">
          <label for="">Email :</label>
          <input type="text" v-model="emailDetail" disabled>
          </div>
        <div class="col">
          <label for="">Mot de passe :</label>
          <input type="text" v-model="passwordDetail" disabled>
        </div>
        </div>
        </form>
      </b-modal>
    </div>
  </div>
</div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
import {BFormInput,BButton,BButtonGroup,BIcon,BModal} from 'bootstrap-vue'
import {db} from "../firebase/config.js"
// import {collection} from "firebase/firestore"
export default {
  data(){
    return{
      nom:"",
      prenom:"",
      email:"",
      password:"" ,
      items: [],
      colonne:[{label:"Nom",key:"nom",thClass:"text-center",tdClass:"text-center"},{label:"Prénom",key:"prenom",thClass:"text-center",tdClass:"text-center"},{label:"Email",key:"email",thClass:"text-center",tdClass:"text-center"},{label:"mot de passe",key:"password",thClass:"text-center",tdClass:"text-center"},{label:"Actions",key:'action',thClass:"text-center",tdClass:"text-center"}],
      show:false,
      indexItem:-1,
      modalShow:false,
      nomDetail:"",
      prenomDetail:"",
      emailDetail:"",
      passwordDetail:"",
      regex:/^\w+@[a-zA-Z_]+?\.[a-zA-Z]{2,3}$/,
      varBool:false,
    }},
  
  name: 'HomeView',
  components: {
    // HelloWorld
    dashboard:()=>import('../components/HelloWorld.vue'),
    BFormInput,BButton,BButtonGroup,BIcon,BModal 
  },
  methods:{
    confirmButton(){
      event.preventDefault()
      // this.items.push({
        
      //     nom:this.nom,
      //     prenom:this.prenom,
      //     email:this.email,
      //     password:this.password,
        
      // })
      if(document.myForm.email.value.match(this.regex)){
        document.myForm.email.classList.remove("is-invalid");
        document.myForm.email.classList.add("is-valid");
        document.getElementById("email-validation").innerText ="email valide";
        this.varBool=true;  
      }else{
        document.myForm.email.classList.remove("is-valid");
        document.myForm.email.classList.add("is-invalid");
        document.getElementById("email-validation").innerText ="email invalide";
        this.varBool=false;
      }
    },
    addElement(){
    //   this.confirmButton();
    //   if(this.varBool){
    //     this.items.push({
    //       nom:this.nom,
    //       prenom:this.prenom,
    //       email:this.email,
    //       password:this.password,
    //     })
    //   }else{
    //     alert("Ajout impossible car email invalide");
    // }
    const champ={name:this.nom,prenom:this.prenom,email:this.email,password:this.password}
    console.log(db,"db")
    //db.collection("user").add(champ);
  },
    confirmDelete(){
      this.items.splice(this.indexItem,1)
    },
    deleteItem(item){
      this.indexItem=this.items.indexOf(item);
      this.show=true;
    },
    showDetail(item){
      this.modalShow=true;
      this.nomDetail=item.nom;
      this.prenomDetail=item.prenom;
      this.emailDetail=item.email;
      this.passwordDetail=item.password;
    } 
  }
}

</script>

<style>
  .test{
    margin-top: 120px;
  }
</style>