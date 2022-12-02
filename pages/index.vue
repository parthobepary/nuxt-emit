<template>
  <v-container>
    {{switchInfo}}
    <DialogToAddPerson @newPerson="newPerson($event)"></DialogToAddPerson>

    <div style="display: flex;  flex-direction: row; justify-content: center;">
      <div style="display: flex;  flex-direction: column; margin: 0 10px; width: 300px; height: 500px;">
        <div style="height:50px;" class="center">Stage 1</div>
        <div >

          <draggable style="height:450px;" :list="personlist1" group="tasks" @change="log($event, 1)">
            <SingleCard v-for="(person, index) in personlist1" :key="index" :person="person"></SingleCard>
          </draggable>
          

        </div>
      </div>
      <div style="display: flex;  flex-direction: column; margin: 0 10px; width: 300px; height: 500px;">
        <div style="height:50px;" class="center">Stage 2</div>
        <div>

          <draggable style="height:450px;" :list="personlist2" group="tasks" @change="log($event, 2)">
            <SingleCard v-for="(person, index) in personlist2" :key="index" :person="person"></SingleCard>
          </draggable>

        </div>
      </div>
    </div>

  </v-container>
</template>

<script>
import persons from '~/static/json/persons.json'
import draggable from "vuedraggable";
export default {
  name: 'IndexPage',
  components: { draggable },
  data(){
    return {
      personlist1: JSON.parse(JSON.stringify(persons)).slice(0, 5),
      personlist2: JSON.parse(JSON.stringify(persons)).slice(5, 10),
      removeAddedList: [],
      switchInfo: '',
    }
  },
  watch: {
    removeAddedList: function(){
      if(this.removeAddedList.length == 2){
        this.switchInfo = `Stage ${this.removeAddedList[1].stage} to Stage ${this.removeAddedList[0].stage}`
        this.removeAddedList = []
      }
    }
  },
  methods:{
    newPerson(newPerson){
      this.personlist1.push(newPerson)
    },
    log(event, id){
      if(event['added'] != undefined){
        this.removeAddedList.push({added: event.added.element, stage: id})
      }
      else{
        this.removeAddedList.push({removed: event.removed.element, stage: id})
      }
    }
  }
}
</script>

<style>
.center{
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
