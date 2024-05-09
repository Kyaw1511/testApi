<template>
  <div>
    <h1>hello world</h1>
  </div>

  <!-- test -->
  <div class="row">
    <div class="col-md-3">
      
    </div>

    <!-- array of array -->
    <div
      class="col-md-9">
      <ul
        class="list-group">
        <li
          v-for="user in users.data" :key="user"
          class="list-group-item my-2 border border-dark">
          <div>
            <h4>
              No.{{ user.id }} 
            </h4>
            <h4>
              <pre>First Name : {{ user.first_name }}</pre>
            </h4>
            <h4>
              <pre>Last Name  : {{ user.last_name }}</pre>
            </h4>
            <h3>
              <pre>Email      : {{ user.email }}</pre>
            </h3>
            <img :src="user.avatar" :key="avatar" alt="">

          </div>
          
          <div>
            <h3
              v-for="person in people" :key="person.email">
              {{ user.email }}
            </h3>
            <button
              @click="showEmail"
              class="btn btn-sm btn-primary my-1">
              Detail
            </button>
          </div>

        </li>
      </ul>
    </div> 
  
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