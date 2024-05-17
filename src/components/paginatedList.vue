<template>
  <div>
    <ul>
      <li v-for="item in paginatedData" :key="item.id">{{ item.name }}</li>
    </ul>
    <div class="pagination-controls">
      <button @click="prevPage" :disabled="currentPage === 1">Previous</button>
      <span>Page {{ currentPage }} of {{ totalPages }}</span>
      <button @click="nextPage" :disabled="currentPage === totalPages">Next</button>
    </div>
  </div>
</template>
  
<script setup>
  import { ref, computed, onMounted } from 'vue';
  
  // Sample data - replace with your own data source
  // const data = ref([
  //   { id: 1, name: 'Item 1' },
  //   { id: 2, name: 'Item 2' },
  //   { id: 3, name: 'Item 3' },
  //   { id: 4, name: 'Item 4' },
  //   { id: 5, name: 'Item 5' },
  //   { id: 6, name: 'Item 6' },
  //   { id: 7, name: 'Item 7' },
  //   { id: 8, name: 'Item 8' },
  //   { id: 9, name: 'Item 9' },
  //   { id: 10, name: 'Item 10' },
  //   { id: 11, name: 'Item 11' },
  //   { id: 12, name: 'Item 12' },
  //   { id: 13, name: 'Item 13' },
  //   { id: 14, name: 'Item 14' },
  //   { id: 15, name: 'Item 15' },
  //   { id: 16, name: 'Item 16' },
  //   { id: 17, name: 'Item 17' },
  //   { id: 18, name: 'Item 18' },
  //   { id: 19, name: 'Item 19' },
  //   { id: 20, name: 'Item 20' },
  //   { id: 21, name: 'Item 21' },

  // ]);

  // const users = ref([])
  // const loadUsers = () => {
  //   axios.get('https://reqres.in/api/users')
  //   .then((res) => {
  //     users.value = res.data
      
  //   })
  //   .catch((err) => console.log(err))

  // }
  // onMounted(() => {
  //   loadUsers()

  // })
  
  // const itemsPerPage = 3;
  // const currentPage = ref(1);
  
  // const totalPages = computed(() => Math.ceil(data.value.length / itemsPerPage));
  // const paginatedData = computed(() => {
  //   const start = (currentPage.value - 1) * itemsPerPage;
  //   const end = start + itemsPerPage;
  //   return data.value.slice(start, end);
  // });
  
  // const nextPage = () => {
  //   if (currentPage.value < totalPages.value) {
  //     currentPage.value++;
  //   }
  // };
  
  // const prevPage = () => {
  //   if (currentPage.value > 1) {
  //     currentPage.value--;
  //   }
  // };

  // Reactive state
  const data = ref([]);
  const itemsPerPage = (6);
  const currentPage = ref(1);

const loadUsers = () => {
  // `https://reqres.in/api/users?page=${currentPage.value}`
    axios.get('https://reqres.in/api/users')
    .then((res) => {
      data.value = res.data
      
    })
    .catch((err) => console.log(err))

  }
  onMounted(() => {
    loadUsers()

  })

  //Fetch data from API
//   const fetchData = async () => {
//   try {
//     // const response = await fetch('https://api.example.com/items');
//     const response = await fetch('https://reqres.in/api/users');
//     data.value = response.data;
//   } catch (error) {
//     console.error('Error fetching data:', error);
//   }
// }
  // Fetch data when the component is mounted
  // onMounted(fetchData);

  // Computed properties
  const totalPages = computed(() => Math.ceil(data.value.length / itemsPerPage));
  const paginatedData = computed(() => {
    const start = (currentPage.value - 1) * itemsPerPage;
    const end = start + itemsPerPage;
    return data.value.slice(start, end);
  });

  // Methods to change pages
  const nextPage = () => {
    if (currentPage.value < totalPages.value) {
      currentPage.value++;
    }
  };

  const prevPage = () => {
    if (currentPage.value > 1) {
      currentPage.value--;
    }
  };

</script>
  

<style>
  .pagination-controls {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 1rem;
  }
  button {
    padding: 0.5rem 1rem;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 0.25rem;
    cursor: pointer;
  }
  button:disabled {
    background-color: #d6d6d6;
    cursor: not-allowed;
  }
</style>

