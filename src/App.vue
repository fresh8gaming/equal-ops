<template>
  <v-app>
    <v-card>
      <v-card-title>How old are you?</v-card-title>
      <v-card-actions>
        <v-radio-group v-model="ageGroup">
          <v-radio v-for="age in ageGroups" :key="age" :label="`${age}`" :value="age"></v-radio>
        </v-radio-group>
      </v-card-actions>
    </v-card>

    <v-card>
      <v-card-title>What is your tenure in the organisation?</v-card-title>
      <v-card-text>Please round down, e.g. for 1 year and 10 months, please select 1 year.</v-card-text>
      <v-card-actions>
        <v-radio-group v-model="tenureGroup">
          <v-radio
            v-for="tenure in tenureGroups"
            :key="tenure"
            :label="`${tenure}`"
            :value="tenure"
          ></v-radio>
        </v-radio-group>
      </v-card-actions>
    </v-card>

    <v-card>
      <v-card-title>What is your gender identity?</v-card-title>
      <v-card-actions>
        <v-radio-group v-model="genderGroup">
          <v-radio
            v-for="gender in genderGroups"
            :key="gender"
            :label="`${gender}`"
            :value="gender"
          ></v-radio>

          <v-radio value="Other"></v-radio>
          <v-text-field :disabled="!genderGroup === 'Other'" label="Other"></v-text-field>
        </v-radio-group>
      </v-card-actions>
    </v-card>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';

export default {
  name: "App",
  components: {
    // HelloWorld,
  },
  // methods: () => ({
  //   genderOther: () => {
  //     // eslint-disable-next-line
  //     console.log(this.genderGroup);
  //     return this.genderGroup === "Other";
  //   }
  // }),
  data: () => ({
    ageGroup: "",
    ageGroups: ["16-24", "25-34", "35-44", "45-54", "55-64", "65+"],

    tenureGroup: "",
    tenureGroups: [
      "Less than 1 year",
      "1 year",
      "2 years",
      "3 years",
      "4 years",
      "5 years or more"
    ],

    genderGroup: "",
    genderGroups: ["Woman", "Man", "Genderqueer or non-binary", "Agender"]
  })
};
</script>
