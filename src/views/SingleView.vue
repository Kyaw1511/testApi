<template>

    <div class="container-fluid">
        <div
            class="list-group-item my-2 border border-dark flex" 
            v-if="user"
            >
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
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted} from 'vue';
import { useRoute } from 'vue-router'

const route = useRoute()

  const user = ref()


  const loadUser = () => {
    axios.get('https://reqres.in/api/users/' + route.params.id)
    .then((res) => {
      user.value = res.data.data
    })
    .catch((err) => console.log(err))

  }
  onMounted(() => {

    loadUser()
  })
</script>