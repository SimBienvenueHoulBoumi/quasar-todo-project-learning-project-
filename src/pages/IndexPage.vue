<template>
  <q-page class="flex flex-center">
    <q-card class="my-card" style="width: 600px">
      <q-card-section>
        <div class="text-h4">My To-Do List</div>
      </q-card-section>

      <q-card-section>
        <div class="row justify-center">
          <div class="col-12 q-pb-md">
            <!-- zone de saisie + button -->
            <q-input v-model="todoTask" label="Input Task">
              <template v-slot:after>
                <!-- associer le bouton à la fonction -->
                <q-btn round dense flat icon="send" @click="addItem" />
              </template>
            </q-input>
          </div>
        </div>
      </q-card-section>

      <q-separator />

      <q-card-section>
        <!-- faire une liste de toute les tâches -->
        <div class="row justify-center" v-for="(item, index) in todoList" :key="index">
          <div class="col-8 q-py-md">
            {{ item.value }}
          </div>
          <div class="col-auto q-py-md">
            <q-btn round dense flat icon="done" @click="removeItem(index)" />
          </div>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "IndexPage",
  data() {
    return {
      todoTask: "",
      todoList: [{ value: "Create an app" }, { value: "Build an app" }], // charger les éléments à modifier
    };
  },
  methods: {
    addItem() {
      this.todoList.push({ value: this.todoTask });
    },
    removeItem(index) {
      this.todoList.splice(index, 1);
    },
  },
});
</script>
