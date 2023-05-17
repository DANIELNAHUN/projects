<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />
      </div>
      <v-spacer></v-spacer>
      <div>Daniel Calcina</div>
    </v-app-bar>
    <v-row align="center">
      <v-item-group v-model="window" class="shrink mr-6" mandatory tag="v-flex">
        <v-item v-for="n in length" :key="n" v-slot="{ active, toggle }">
          <div class="pa-3">
            <v-btn :input-value="active" plain @click="toggle" class="text-h3">
              Proyecto {{ n }}
            </v-btn>
          </div>
        </v-item>
      </v-item-group>

      <v-col>
        <v-window v-model="window" class="elevation-1" vertical>
          <v-window-item v-for="n in length" :key="n">
            <v-card flat>
              <v-card-text>
                <v-row class="mb-4" align="center">
                  <v-col class="text-h6" cols="8">
                    <v-avatar color="grey" class="mr-4"></v-avatar>
                    <strong class="text-h6">Proyecto {{ n }}</strong>
                  </v-col>
                  <v-col class="text-h6" cols="2">
                    <v-text-field
                      v-model="date_i"
                      label="Fecha Inicial"
                      class="shrink"
                    ></v-text-field>
                  </v-col>
                  <v-col class="text-h6" cols="2">
                    <v-text-field
                      v-model="date_f"
                      label="Fecha Final"
                      class="shrink"
                    ></v-text-field>
                  </v-col>
                </v-row>
                <v-row v-for="t in task" :key="t">
                  <v-expansion-panels>
                    <v-expansion-panel>
                      <v-card>
                        <v-expansion-panel-header>
                          <div class="text-h6" v-text="t.title"></div>
                        </v-expansion-panel-header>
                        <v-expansion-panel-content>
                          <v-card-text>
                            <v-row align="center">
                              <v-col class="text-subtitle-1" cols="3">
                                <v-text-field
                                  v-model="t.fecha_i"
                                  label="Fecha Inicial"
                                  class="shrink"
                                ></v-text-field>
                              </v-col>
                              <v-col class="text-subtitle-1" cols="3">
                                <v-text-field
                                  v-model="t.fecha_f"
                                  label="Fecha Final"
                                  class="shrink"
                                ></v-text-field>
                              </v-col>
                              <v-col class="text-subtitle-1" cols="3">
                                <v-text-field
                                  v-model="t.user_id"
                                  label="Responsable"
                                  class="shrink"
                                ></v-text-field>
                              </v-col>
                              <v-col class="text-subtitle-1" cols="3">
                                <v-text-field
                                  v-model="t.estate"
                                  label="Estado"
                                  class="shrink"
                                ></v-text-field>
                              </v-col>
                            </v-row>
                            <v-row align="center">
                              <v-col class="text-subtitle-1" cols="6">
                                <v-text-field
                                  v-model="t.descripcion"
                                  label="Descripcion"
                                  class="shrink"
                                ></v-text-field>
                              </v-col>
                              <v-col class="text-subtitle-1" cols="6">
                                <v-text-field
                                  v-model="t.observacion"
                                  label="Observacion"
                                  class="shrink"
                                ></v-text-field>
                              </v-col>
                            </v-row>
                          </v-card-text>
                        </v-expansion-panel-content>
                      </v-card>
                    </v-expansion-panel>
                  </v-expansion-panels>
                </v-row>
              </v-card-text>
            </v-card>
          </v-window-item>
        </v-window>
      </v-col>
    </v-row>

    <!-- <v-main>
      <router-view/>
    </v-main> -->
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //
    length: 5,
    window: 0,
    task: [
      {
        title: "Planificacion",
        fecha_i: "01-05-23",
        fecha_f: "02-05-23",
        user_id: "Daniel - Diego",
        estate: "Terminado",
        color: "",
        descripcion: "Reunion 01-05-23 con Jaime",
        observacion: "",
        id_proy: 0,
      },
      {
        title: "Recojo de Datos",
        fecha_i: "03-05-23",
        fecha_f: "06-05-23",
        user_id: "Daniel",
        estate: "Terminado",
        color: "",
        descripcion: "",
        observacion: "",
        id_proy: 0,
      },
      {
        title: "Desarrollo",
        fecha_i: "10-05-23",
        fecha_f: "05-07-23",
        user_id: "Daniel",
        estate: "En Proceso",
        color: "",
        descripcion: "",
        observacion: "",
        id_proy: 0,
      },
    ],
    date_i: new Date().toISOString().substr(0, 7),
    date_f: new Date().toISOString().substr(0, 7),
    menu_i: false,
    menu_f: false,
  }),
};
</script>
