<template>
   <v-list-group>
      <template v-slot:activator>
          <v-list-item-icon>
            <v-icon>mdi-server</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ solution.name }}</v-list-item-title>
          </v-list-item-content>
      </template>
      <v-list-group sub-group v-for="(app, index) in solution.applications">
        <template v-slot:activator>
          <v-list-item-content>
              <v-list-item-title>{{ app.name }}</v-list-item-title>
          </v-list-item-content>
        </template>
        <v-card>
          <v-card-text>
            <v-row>
              <v-col>
                <b>Status: </b>{{app.status.status}}<br>
                <b>Id: </b>{{app.id}}<br>
              </v-col>
              <v-col>
                <b>Autheur: </b>{{app.config.host}}<br>
                <b>App: </b>{{app.config.path}}<br>
                <b>Version: </b>{{app.config.version}}
              </v-col>
            </v-row>
          </v-card-text>

        </v-card>
      </v-list-group>
    </v-list-group>

</template>

<script>
export default {
  name: "SolutionListItem",
  props: {
    solution: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>

</style>