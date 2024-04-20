<template>
  <div class="about">
    <dashboard/>
  <div class="card">
    <div style="margin-right:auto;margin-left:75px;width: 400px;">
      <h3 class="card-title">A propos</h3>
      <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Qui ducimus, dolores libero accusantium iure porro, sunt laudantium quod tenetur debitis ipsum nesciunt deserunt suscipit in rem a ad, nobis adipisci.</p>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Harum id possimus maiores natus cupiditate corporis? Nam quo rem molestiae id dolores deleniti magnam, quod doloremque adipisci asperiores quaerat animi autem?</p>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Harum id possimus maiores natus cupiditate corporis? Nam quo rem molestiae id dolores deleniti magnam, quod doloremque adipisci asperiores quaerat animi autem?</p>
    </div>
  </div>
  </div>
</template>
<style>
.card-title{
  /* margin-top: 15px; */
 /* margin-right:auto;
  margin-left:auto;
   padding: 15px; */
}
.card{
  margin:auto;
  padding: 15px;
  width:500px;
  margin-top: 15px;
}
</style>
<script>
  export default{
    components:{
      dashboard:()=>import('../components/HelloWorld.vue') 
    }
  }
</script>