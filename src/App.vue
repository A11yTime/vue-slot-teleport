<template>
  <div>
    <the-header></the-header>
    <!-- <badge-list></badge-list>
    <user-info
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    ></user-info> -->
    <button role="tab" :aria-selected="selectedComponent === 'active-goals' ? 'true' : 'false'" @click="setSelectedComponent('active-goals')">Active Goals</button>
    <button role="tab" :aria-selected="selectedComponent === 'manage-goals' ? 'true' : 'false'" @click="setSelectedComponent('manage-goals')">Manage Goals</button>
    <!-- <active-goals  v-if="selectedComponent === 'active-goals'"></active-goals>
    <manage-goals v-if="selectedComponent === 'manage-goals'"></manage-goals> -->
    <keep-alive>
      <component :is="selectedComponent"></component>
    </keep-alive>
   
  </div>
</template>

<script>
import ActiveGoals from './components/ActiveGoals.vue';
import ManageGoals from './components/ManageGoals.vue';
export default {
  components: {
    ActiveGoals,
    ManageGoals
  },
  data() {
    return {
      selectedComponent: 'active-goals',
      activeUser: {
        name: 'Maximilian Schwarzmüller',
        description: 'Site owner and admin',
        role: 'admin',
      },
    };
  },
  methods: {
    setSelectedComponent(cmp){
      this.selectedComponent = cmp;
    }
  }
};
</script>

<style>
html {
  font-family: sans-serif; 
}

body {
  margin: 0;
}
</style>