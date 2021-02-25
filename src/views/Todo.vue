<template>
 <v-container>
    <v-row>
     <v-col cols="12" md="6" xm="12">
      <div class="home">

    <list-tasks
      v-if="$store.state.tasks.length"
    />

    <no-tasks
      v-else
    />

    <button-done-sorting 
      v-if="$store.state.sorting"
    />

  </div>
  </v-col>
  
  <v-col cols="150" md="6" xm="15">
    <v-img
    lazy-src="https://picsum.photos/id/11/10/6"
    src="familia.jpeg"
    ></v-img>
  </v-col>


  </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Home',
  components: {
    'list-tasks': require('@/components/Todo/ListTasks.vue').default,
    'no-tasks': require('@/components/Todo/NoTasks.vue').default,
    'button-done-sorting': require('@/components/Todo/ButtonDoneSorting.vue').default
  }
}
</script>