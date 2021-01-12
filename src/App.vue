<template>
<div>
 <h1>LOOP</h1>
  <table>
    <tr>
      <td>Name</td>
      <td>Calories</td>
      <td>Fat</td>
      <td>Carbs</td>
      <td>Protein</td>
      <td>Edit</td>
      <td>Delete</td>
    </tr>
    <tr v-for="(person,index) in persons" :key="index">
      <td v-if="person.edit===true">
          <input type="text" v-model="person.name" @blur="off(person)"
          @keypress.enter ="$event.target.blur()">
      </td> 
      <td v-else>
          {{person.name}}
      </td> 

      <td v-if="person.edit===true">
         <input type="text" v-model="person.calories" @blur="off(person)"
          @keypress.enter ="$event.target.blur()">
      </td>
      <td v-else>
         {{person.calories}}
      </td>

      <td v-if="person.edit===true">
          <input type="text" v-model="person.fat" @blur="off(person)"
          @keypress.enter ="$event.target.blur()">
      </td>
      <td v-else>        
        {{person.fat}}
      </td>

      <td v-if="person.edit===true">
          <input type="text" v-model="person.carbs" @blur="off(person)"
          @keypress.enter ="$event.target.blur()">
      </td>
      <td v-else>        
        {{person.carbs}}
      </td>

      <td v-if="person.edit===true">
        <input type="text" v-model="person.protein" @blur="off(person)"
        @keypress.enter ="$event.target.blur()">
      </td>
      <td v-else>        
       {{person.protein}}
      </td>

      <td>      
      <input type="button" value="Edit" @click ="editData(person)">     
      </td>
      <td><input type="button" value="Delete" @click ="delData(person)"></td>
      </tr>
      
      <tr>
        <td>Total</td>
        <td>{{totalCalories}}</td>
        <td>{{totalFat}}</td>
        <td>{{totalCarbs}}</td>
        <td>{{totalProtein}}</td>
      </tr>
  </table>

</div>
 
</template>

<script>
export default {
  data(){
    return{
      persons: [
          {
            name: 'Frozen Yogurt',
            calories: 159,
            fat: 6.0,
            carbs: 24,
            protein: 4.0,
            edit: false
          },
          {
            name: 'Ice cream sandwich',
            calories: 237,
            fat: 9.0,
            carbs: 37,
            protein: 4.3,
            edit: false
           
          },
          {
            name: 'Eclair',
            calories: 262,
            fat: 16.0,
            carbs: 23,
            protein: 6.0,
            edit: false
          
          },
          {
            name: 'Cupcake',
            calories: 305,
            fat: 3.7,
            carbs: 67,
            protein: 4.3,
            edit: false
            
          },
          {
            name: 'Gingerbread',
            calories: 356,
            fat: 16.0,
            carbs: 49,
            protein: 3.9,
            edit: false
         
          },
          {
            name: 'Jelly bean',
            calories: 375,
            fat: 0.0,
            carbs: 94,
            protein: 0.0,
            edit: false
          
          },
          {
            name: 'Lollipop',
            calories: 392,
            fat: 0.2,
            carbs: 98,
            protein: 0,
            edit: false
         
          },
          {
            name: 'Honeycomb',
            calories: 408,
            fat: 3.2,
            carbs: 87,
            protein: 6.5,
            edit: false
          
          },
          {
            name: 'Donut',
            calories: 452,
            fat: 25.0,
            carbs: 51,
            protein: 4.9,
            edit: false
           
          },
          {
            name: 'KitKat',
            calories: 518,
            fat: 26.0,
            carbs: 65,
            protein: 7,
            edit: false
          
          },          
      ],     
    }
  },
  computed: {
    totalCalories(){      
      return this.persons.reduce((sum,person) => sum + Number(person.calories),0)
    },
    totalFat(){
      return this.persons.reduce((sum,person) => sum + Number(person.fat),0)
    },totalCarbs(){
      return this.persons.reduce((sum,person) => sum + Number(person.carbs),0)
    },
    totalProtein(){
       return this.persons.reduce((sum,person) => sum + Number(person.protein),0)
    }
  },
  methods: {
    editData(person){   
      person.edit= true
    },
    off(person){
      person.edit= false
    },
     delData(person){
      let index = this.persons.indexOf(person)
      this.persons.splice(index,1)
    }
  }
}
</script>

<style>
tr{
  border: 1px solid gainsboro;
  width: 100%;
  padding: 0px;
  margin: 0px;
}
td{
  border: 1px solid gainsboro;
  width: auto;
  padding: 5px;
  margin: 0px;
}
input[type=button]{
  width: auto;
  color:black;
  border: 1px solid turquoise;
  background-color: darkturquoise;
  padding: 5px;
  margin: 2px;
  border-radius: 5px;
}
input[type=text]{
  width: 60%;
}

</style>

