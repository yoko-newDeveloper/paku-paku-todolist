<template>
  <v-container class="grey lighten-5">
    <v-row>
      <v-col>
        <v-text-field label="TODO" hint="入力してEnterキー" v-model="todoInput" clearable @keydown.enter="add"></v-text-field>
        {{ todoInput }}
      </v-col>
      <v-col>
        <v-btn fab @click="del"><v-icon>mdi-delete-forever-outline</v-icon></v-btn>
      </v-col>
    </v-row>
    <v-row no-gutters>
      <v-col>

      <!-- <v-card>の中に文字を書く -->
      <v-card>
        <v-list dense>
          <v-list-item-group>
            <!-- todo1件のtitleを1つのkey（情報を特定する）にして、配列をループで回す -->
            <v-list-item v-for="todo in todos" :key="todo.title">
              <!-- labelの前に:を付けると件数を扱えるようになる -->
              <!-- todo.tsのtitleを1件ずつ取り出す -->
              <v-checkbox :label="todo.title" v-model="todo.done" v-bind:class="{ done: todo.done }"></v-checkbox>
            </v-list-item>
          </v-list-item-group>
        </v-list>
      </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { Todo } from '@/models/todo'
import Vue from 'vue'
import { Component } from 'vue-property-decorator'
import HelloWorld from '../components/HelloWorld.vue'

@Component({ components: { HelloWorld } })
export default class HomeView extends Vue {
  todos: Todo[] = []
  todoInput = ''

  add () {
    this.todos.push(new Todo(this.todoInput))
    this.todoInput = ''
  }

  del () {
    this.todos = this.todos.filter(item => item.done === false)
  }
}
</script>
<style lang="sass">
.done
  text-decoration: line-through
</style>
