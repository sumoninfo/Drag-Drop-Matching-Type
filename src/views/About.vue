<template>
  <div style="padding: 50px">
    <div class="row" style="" v-for="(element, index) in list1" :key="element.name">
      <div class="col-md-3">
        <div class="list-group-item">
          {{ element.name }} {{ index }}
        </div>
      </div>
      <div class="col-md-3">
        <draggable class="list-group" :list="list1" group="people">
          drop
        </draggable>
      </div>
    </div>

    <div class="row">
      <div class="col-md-3">
        <h3>Draggable 2</h3>
        <draggable class="list-group" :list="list2" group="people">
          <div class="list-group-item" v-for="(element, index) in list2" :key="element.name">
            {{ element.name }} {{ index }}
          </div>
        </draggable>
      </div>
    </div>
  </div>
</template>
<script>
import draggable from 'vuedraggable'

export default {
  name      : "two-lists",
  display   : "Two Lists",
  order     : 1,
  components: {
    draggable
  },
  data() {
    return {
      list1: [
        {name: "John", id: 1},
        {name: "Joao", id: 2},
        {name: "Jean", id: 3},
        {name: "Gerard", id: 4}
      ],
      list2: [
        {name: "Juan", id: 5},
        {name: "Edgard", id: 6},
        {name: "Johnson", id: 7}
      ]
    };
  },
  methods: {}
};
</script>