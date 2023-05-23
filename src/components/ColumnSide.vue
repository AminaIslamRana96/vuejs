import axios from 'axios';

<template>
  
  <div class="section">
    <div class="column">
      <h2>Instructions</h2>
      <p>This is some placeholder text for column 1.</p>
    </div>
    <div class="column">
      <h2>Task</h2>
      <p>This is some placeholder text for column 2.</p>
    </div>
    <div class="column ">
      <h2>Answer</h2>
      <div class="input-section">
        <textarea
          v-model="name"
          placeholder="Enter JavaScript code..."
        ></textarea>
        <button v-on:click="submitCode">Submit</button>
      </div>
    </div>
  </div>
  
</template>

<script>
import axios from "axios"
export default {
  name: "submitCode",
  data() {
    return {
      name: " "  
    };
  },
  methods: {
    async submitCode() {
      
    let result = await axios.post("http://localhost:3000/user",
    {
      name :this.name
    });
    console.warn(result);
    if(result.status==201){
      alert("submit succesfully")
    }
    }
  }

};

</script>

<style scoped>
.section {
  display: flex;
  flex-wrap: wrap;
  margin-top: 60px;
}

.column {
  background-color: #eba750;
  padding: 20px;
  margin: 10px;
  box-sizing: border-box;
  text-align: center;
  height: 400px;
  width: 300px;
  border-radius: 12px;
  width: cal(33.3% - 20px);
  
}
.column p {
  margin-top: 20px;
}
.column h2 {
  color: rgb(22, 20, 19);
}
/* for mediam */
@media screen and (max-width:768px) {
  .column{
    width: 250px;
    height: 260px;
    
  }

.input-section textarea {
  padding: 8px;
  height: 140px;
  resize: none;
  border-radius: 4px;
  border-color: rgb(238, 190, 100);
}
}

.input-section {
  margin-top: 20px;
}

textarea {
  width: 100%;
  padding: 8px 0 0 8px;
  height: 150px;
  resize: none;
  border-radius: 4px;
  border-color: rgba(53, 39, 8, 0.87);
}

button {
  display: block;
  margin-top: 10px;
  padding: 8px 16px;
  background-color: rgb(114, 59, 13);
  color: white;
  border: none;
  cursor: pointer;
  border-radius: 4px;
}
</style>
