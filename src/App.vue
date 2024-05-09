<template>

  <!-- test -->
  <div class="row">
    <div class="container">
      <nav class="navbar navbar-expand-lg bg-info mx-2">
        <div class="container-fluid">
          <a class="navbar-brand" href="#">API</a>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
              <li class="nav-item">
                <a class="nav-link active" aria-current="page" href="#">Home</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Features</a>
              </li>
            </ul>
          </div>
        </div>
    </nav>

    </div>
    <div class="col-md-3"></div>

    <!-- array of array -->
    <div
      class="col-md-6">
      <ul
        class="list-group">
        <li
          v-for="user in users.data" :key="user"
          class="list-group-item my-2 border border-dark flex">
          <div class="float-start">
            <h4>
              No.{{ user.id }} 
            </h4>
            <h4>
              <pre>First Name : {{ user.first_name }}</pre>
            </h4>
            <h4>
              <pre>Last Name  : {{ user.last_name }}</pre>
            </h4>
            <h4>
              <pre>Email      : {{ user.email }}</pre>
            </h4>
          </div>
          
          <div class="float-end">
            <img 
              :src="user.avatar" :key="avatar" alt=""
              class="float-end"
            >
          </div>
          <!-- <div class="">
            <h3
              v-for="person in people" :key="person.email">
              {{ user.email }}
            </h3>
            <button
              @click="showEmail"
              class="btn btn-sm btn-primary my-1">
              Detail
            </button>
          </div> -->

        </li>
      </ul>
    </div> 
  
    <div class="col-md-3"></div>
  </div>
  
</template>

<script setup>
  import {onMounted, reactive, ref} from 'vue';
  
  const users = ref([])
  const loadUsers = () => {
    axios.get('https://reqres.in/api/users')
    .then((res) => {
      users.value = res.data
      
    })
    .catch((err) => console.log(err))

  }
  onMounted(() => {
    loadUsers()

  })
  
  const person31 = reactive({
    email: ''
  })
  const people = ref([])
  const showEmail = () => {
    people.value.push({...person31})
    person31.email = ''
    
  }
  
  // const storeUser = () => {
  //   axios.post('https://reqres.in/api/users')
  //   .then((res) => {
  //     users.value.push(res.data)
    
  //     console.log(res)
  //   })
  // }
  
  

</script>

<style scoped>

</style>