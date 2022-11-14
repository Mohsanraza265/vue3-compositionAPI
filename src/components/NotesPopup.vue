<script setup>
  
  import { ref } from 'vue'
  // for popup
  const showModal = ref(false);
  // for getting value of textarea
  const newNote = ref("Hello ");
  //for alert message
  const errorMessage = ref("");
  const notes = ref([])

  // go to google and search (javascript random light color generator) then pick that code & paste it But you set some changes delete 'color =' & replace return
  function getRandomColor() {
    return "hsl(" + Math.random() * 360 + ", 100%, 75%)";
  }

 
  const addNote = () => {
    if(newNote.value.length == 0){
      return errorMessage.value = "Jana message to likhooooo"
    }
    else{
      notes.value.push({
        id: Math.floor(Math.random() * 100000),
        text: newNote.value,
        date: new Date(),
        backgroundColor: getRandomColor()
      });
    }
    showModal.value = false;
    newNote.value = "" 
    errorMessage.value = ""

  }

</script>

<template>
  
 <main>
    
    <!-- for popup start -->
      
       <div v-if="showModal" class="overlay">
        <div class="modal">
           <!-- if we use trim key world after v-model then teaxtarea no accept space  -->
          <textarea v-model.trim="newNote" name="note" id="note" cols="30" rows="10"></textarea>
          <p style="color: red; font-weight: bold; font-size: 50px; " v-if="errorMessage">{{errorMessage}}</p>
          <button @click="addNote">Add Note</button>
          <button class="close"  @click="showModal = false">Close</button>
        </div>
      </div>

    <!-- for popup end -->


    <div class="container">
      <header>
        <h1>Notes</h1>
        <button @click="showModal = true">+</button>
      </header>
      <div class="cards-container">
        <div 
          v-for="note in notes" class="card" 
          :key="note.id"
          :style="{backgroundColor: note.backgroundColor}">
          <p class="main-text">{{note.text}}</p>
          <!-- if we want to use only date no day & other thing then after date key world we place (toLocalDateString("en-US")) -->
          <p class="date">{{note.date.toLocaleDateString("en-US")}}</p>
        </div>
        

      </div>

    </div>
    
 </main>
 
</template>

<style scoped>
  main{
    
    height: 100vh;
    width: 100vw;
    /* display: flex;
    align-items: center;
    justify-content: center; */
  }
  .container {
    max-width: 1000px;
    padding: 10px;
    margin: 0 auto;
  }
  header{
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  h1 {
    font-size: 75px;
    font-weight: bold;
    margin-bottom: 25px;
  }
  header button {
    width: 50px;
    height: 50px;
    padding: 10px;
    cursor: pointer;
    background-color: black;
    border: none;
    border-radius: 50%;
    color: white;
    font-size: 20px;
  }
  .card {
    width: 225px;
    height: 225px;
    padding: 10px;
    cursor: pointer;
    background-color: orange;
    border-radius: 15px;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    margin-right: 20px;
    margin-bottom: 20px;
  }
  .date {
    font-size: 12px;
    font-weight: bold;
  }
  .cards-container {
    display: flex;
    flex-wrap: wrap;
  }

  .overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.77);
    z-index: 10;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .modal {
    width: 750px;
    background-color: white;
    border-radius: 10px;
    padding: 30px;
    display: flex;
    position: relative;
    flex-direction: column;
  }
  .modal button {
    padding: 10px 20px;
    width: 100%;
    background-color: rgb(196, 63, 196);
    color: white;
    font-size: 20px;
    border-radius: 10px;
    cursor: pointer;
    border: none;
    margin: 10px 0px;
  }
  .modal textarea{
    border: 1px solid rgb(231, 62, 231);
    outline: none;
    border-radius: 10px;  
  }
  .close {
    background-color: rgb(221, 98, 98) !important;
  }
</style>