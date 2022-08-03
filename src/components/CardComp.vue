<template>
<div >
<b-container class="g-0"  fluid="sm">
  <b-row class="g-2">
    <b-col cols="6" md="3" v-for="user of usersList" :key="user.id">

      <b-card
      :img-src="'https://avatars.dicebear.com/v2/avataaars/'+ user.username +'.svg?options[mood][]=happy'"
      img-alt="Image"
      img-top
      tag="article"
      style="max-width: 20rem;"
      class="mb-3 g-20 userCard"
    >
      <b-card-text class="userName"> {{user.name}}</b-card-text>
      <b-card-text class="userInfo"><b-icon icon="envelope"></b-icon> &nbsp; {{user.email}}</b-card-text>
      <b-card-text class="userInfo"><b-icon icon="telephone"></b-icon> &nbsp; {{user.phone}}</b-card-text>
      <b-card-text class="userInfo"><b-icon icon="globe"></b-icon>  &nbsp; {{user.website}}</b-card-text>
      <b-card-footer class="footer">
        <b-container fluid>
          <b-row>
            <b-col class="actions"><b-button @click="reaction(user.name)" class="like" variant="none">
                <b-icon  icon="heart" style="color: deeppink;"></b-icon>
            </b-button></b-col>
            <b-col class="actions"><b-button variant="none"><b-icon icon="pen"></b-icon></b-button></b-col>
            <b-col class="actions"><b-button variant="none"><b-icon icon="trash"></b-icon></b-button></b-col>
          </b-row>
        </b-container>
      </b-card-footer>
    </b-card>
    </b-col>
  </b-row>
</b-container>
</div>
</template>

 
<script>



export default {


  props:['usersList'],
  data:()=>({
  liked:false
}),

methods:{
  reaction(name){
    console.log(name);
    this.liked=!this.liked
    alert("You liked " + name);
  }
}
 
}
</script>

<style scoped>
  .userCard{
    margin: 0px;
    text-align: left;
  }
  .userName{
    font-size: 20px;
  }
  .footer{
    background-color: transparent;
  }
  .actions{
    margin-left: auto;
    margin-right: auto;
    text-align: center;
  }

</style>