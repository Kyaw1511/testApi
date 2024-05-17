<template>

  <!-- test -->
  <div class="container-fluid">

    <!-- navigation bar -->
    <nav class="navbar navbar-expand-lg bg-info">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">
          <img src="https://reqres.in/img/logo.png" alt="Logo" width="50" height="30" class="d-inline-block align-text-top">
          Bootstrap
        </a>
      </div>
    </nav>

    <!-- Home page -->
    <div class="row">
      <!-- Empty space -->
      <div class="col-md-3"></div>

      <!-- List of Contents -->
      <!-- array of array -->
      <div
        class="col-md-6" id="app">
        <PaginatedList />
        <ul
          class="list-group">
          <li
            v-for="user in users.data" :key="user"
            class="list-group-item my-2 border border-dark flex" 
            id="app">
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
                :src="user.avatar" alt=""
                class=""
              >
            </div>
          </li>
        </ul>
      
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
      
      <!-- Empty Space -->
      <div class="col-md-3"></div>
    </div>

    <!-- <div class="overflow-auto">
      <b-pagination
        v-model="currentPage"
        :total-rows="totalRows"
        :per-page="perPage"
        :limit="limit"
        align="center"
        class="pagination"
        aria-controls="mytable"
      ></b-pagination>

      <p class="mt-3">Current Page: {{ currentPage }}</p>

      <b-table
        id="mytable"
        :items="itmes"
        :per-page="perPage"
        :current-page="currentPage"
        small
      >
      </b-table>
    </div> -->

    

  </div>
  
</template>

<script setup>
  import {onMounted, ref} from 'vue';
  import PaginatedList from './components/paginatedList.vue';

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
  
  // const person31 = reactive({
  //   email: ''
  // })
  // const people = ref([])
  // const showEmail = () => {
  //   people.value.push({...person31})
  //   person31.email = ''
    
  // }

  // const perPage = ref(3)
  // const currentPage = ref(1)
  // const items = ref([
  //   { id: 1, first_name: 'Fred', last_name: 'Flintstone' },
  //   { id: 2, first_name: 'Wilma', last_name: 'Flintstone' },
  //   { id: 3, first_name: 'Barney', last_name: 'Rubble' },
  //   { id: 4, first_name: 'Betty', last_name: 'Rubble' },
  //   { id: 5, first_name: 'Pebbles', last_name: 'Flintstone' },
  //   { id: 6, first_name: 'Bamm Bamm', last_name: 'Rubble' },
  //   { id: 7, first_name: 'The Great', last_name: 'Gazzoo' },
  //   { id: 8, first_name: 'Rockhead', last_name: 'Slate' },
  //   { id: 9, first_name: 'Pearl', last_name: 'Slaghoople' }
  // ])
  // const rows = computed(() => {
    
  //   console.log(rows) 
  //   return rows.items.length
    
  // })

  


  // const perPage = ref(3)
  // const currentPage = ref([
  //   items = (rows) => ([
  //   { id: 1, first_name: 'Fred', last_name: 'Flintstone' },
  //   { id: 2, first_name: 'Wilma', last_name: 'Flintstone' },
  //   { id: 3, first_name: 'Barney', last_name: 'Rubble' },
  //   { id: 4, first_name: 'Betty', last_name: 'Rubble' },
  //   { id: 5, first_name: 'Pebbles', last_name: 'Flintstone' },
  //   { id: 6, first_name: 'Bamm Bamm', last_name: 'Rubble' },
  //   { id: 7, first_name: 'The Great', last_name: 'Gazzoo' },
  //   { id: 8, first_name: 'Rockhead', last_name: 'Slate' },
  //   { id: 9, first_name: 'Pearl', last_name: 'Slaghoople' }
  // ]),
  // rows = computed(() => {
  //   return items.value.length
  // })
  // ])

// const perPage = ref(3);
// const currentPage = ref(1);
// const items = [
//   { id: 1, first_name: 'Fred', last_name: 'Flintstone' },
//   { id: 2, first_name: 'Wilma', last_name: 'Flintstone' },
//   { id: 3, first_name: 'Barney', last_name: 'Rubble' },
//   { id: 4, first_name: 'Betty', last_name: 'Rubble' },
//   { id: 5, first_name: 'Pebbles', last_name: 'Flintstone' },
//   { id: 6, first_name: 'Bamm Bamm', last_name: 'Rubble' },
//   { id: 7, first_name: 'The Great', last_name: 'Gazzoo' },
//   { id: 8, first_name: 'Rockhead', last_name: 'Slate' },
//   { id: 9, first_name: 'Pearl', last_name: 'Slaghoople' }
// ];

// const rows = computed(() => {
//   rows.value.length
// });

  
  const storeUser = () => {
    axios.post('https://reqres.in/api/users')
    .then((res) => {
      users.value.push(res.data)
    
      console.log(res)
    })
  }
  
  

</script>

<style scoped>

</style>