<template>
  <div>
    
    <!-- Navbar -->

    <!-- Main Page -->
    <div class="row" >
       
        <!-- Left Sidebar -->
        <div class="col-lg-3 mt-2">
           <SideBar  :toggleMonthView="toggleMonthView" v-on:togglePlanningView="togglePlanningView"></SideBar>
        </div>

        <!-- Center -->
        <div class="col-lg-9 mt-2">
            <div v-if="!isPlanningViewMonth()">
                <PlanningWeek class="planning" :planning='planning'  />
            </div>
            <div v-else>
                <PlanningMonth class="planning" :planning='planning'  />
            </div>
            
        </div>
    </div>
    

    
  </div>
</template>

<script>
import SideBar from '../components/SideBar.vue'
import PlanningWeek from '../components/PlanningWeek.vue'
import PlanningMonth from '../components/PlanningMonth.vue'

export default {
  components: {
    SideBar, PlanningWeek, PlanningMonth
  },
  name: 'planning',
  data () {
    return {
      planning: [],
      selectedDateBegin: "20",
      selectedDateEnd: "",
      selectedMonth: "",
      toggleMonthView : true,
      users: []
    }
  },
  created(){
    if (localStorage.getItem('planning')) {
      try {
        this.planning = JSON.parse(localStorage.getItem('planning'));
      } catch(e) {
        localStorage.removeItem('planning');
      }
    }
    if (localStorage.getItem('users')) {
      try {
        this.users = JSON.parse(localStorage.getItem('users'));
      } catch(e) {
        localStorage.removeItem('users');
      }
    }
  },
  mounted() {
    if (localStorage.getItem('planning')) {
      try {
        this.planning = JSON.parse(localStorage.getItem('planning'));
      } catch(e) {
        localStorage.removeItem('planning');
      }
    }
    if (localStorage.getItem('users')) {
      try {
        this.users = JSON.parse(localStorage.getItem('users'));
      } catch(e) {
        localStorage.removeItem('users');
      }
    }
  },
  methods: {
    // Others
    isPlanningViewMonth:function(){
      return this.toggleMonthView
    },
    togglePlanningView:function(){
        this.toggleMonthView = !this.toggleMonthView
    },
  }
}
</script>

<style>

.planning{
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 12px;
}

.sidebar{
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 12px;
  
}

</style>