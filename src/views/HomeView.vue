<template>
  <v-container class="grey lighten-5">
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
                <v-checkbox :label="todo.title"></v-checkbox>
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

  mounted () {
    this.todos.push(new Todo('ジャージャー麺食べたい'))
    this.todos.push(new Todo('餃子食べたい'))
  }
}
</script>
