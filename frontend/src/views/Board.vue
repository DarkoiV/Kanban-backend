<template>
  <div v-show="!loading">
    <div class="main-body">
      <List v-for="list in lists"
        :id = "list.id"
        :pos="list.pos"
        :title="list.title"
        :key="list.id"
        :tasks="list.tasks" 
      />
      <div>
      <p id="newlist" @click="newList"> Create new list </p>
      </div>
    </div>
  </div>
</template>

<script>
import List from '../components/List.vue'
import { mapActions, mapGetters } from 'vuex'

export default {
  name: 'Board',

  props: {
    id: Number,
  },

  components: {
    List
  },

  computed: mapGetters(['name', 'lists', 'loading']),
 
  created() {
    this.fetchBoard(this.id)
  },

  methods: mapActions(["fetchBoard", "newList", 'setNavTitle']),


}
</script>

<style scope>
.main-body {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;

  padding: 25px;
  padding-top: 60px;
}
#newlist {
  font-family: Monaco, monospace;
  font-weight: 500;
  font-size: 20px;

  min-width: 300px;
  margin: 15px;
}
#newlist:hover {
  color: salmon;
  cursor: pointer;
}
</style>
