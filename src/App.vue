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

    <v-card>
      <v-card-title>Do you identify as transgender (or another non-cisgender identity)?</v-card-title>
      <v-card-actions>
        <v-radio-group v-model="transGroup">
          <v-radio v-for="trans in transGroups" :key="trans" :label="`${trans}`" :value="trans"></v-radio>

          <v-radio value="Other"></v-radio>
          <v-text-field :disabled="!transGroup === 'Other'" label="Other"></v-text-field>
        </v-radio-group>
      </v-card-actions>
    </v-card>

    <v-card>
      <v-card-title>What is your sexual orientation?</v-card-title>
      <v-card-actions>
        <v-radio-group v-model="sexidGroup">
          <v-radio v-for="sexid in sexidGroups" :key="sexid" :label="`${sexid}`" :value="sexid"></v-radio>

          <v-radio value="Other"></v-radio>
          <v-text-field :disabled="!sexidGroup === 'Other'" label="Other"></v-text-field>
        </v-radio-group>
      </v-card-actions>
    </v-card>

    <v-card>
      <v-card-title>What is your racial or ethnic identity? (Select all that apply)</v-card-title>
      <v-card-actions>
        <v-container fluid>
          <v-checkbox v-for="race in raceGroups" :key="race" :label="`${race}`" :value="race"></v-checkbox>
          <v-row align="center">
            <v-checkbox value="Other"></v-checkbox>
            <v-text-field :disabled="!raceGroup === 'Other'" label="Other"></v-text-field>
          </v-row>
        </v-container>
      </v-card-actions>
    </v-card>

    <v-card>
      <v-card-title>Is English your first language?</v-card-title>
      <v-card-actions>
        <v-radio-group v-model="languageGroup">
          <v-radio
            v-for="language in languageGroups"
            :key="language"
            :label="`${language}`"
            :value="language"
          ></v-radio>
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
    genderGroups: ["Woman", "Man", "Genderqueer or non-binary", "Agender"],

    transGroup: "",
    transGroups: ["Yes", "No"],

    sexidGroup: "",
    sexidGroups: [
      "Asexual",
      "Bisexual",
      "Gay",
      "Heterosexual or straight",
      "Lesbian",
      "Pansexual",
      "Queer"
    ],

    raceGroup: "",
    raceGroups: [
      "African-British/Black",
      "East Asian (including Chinese, Japanese, Korean, Mongolian, Tibetan and Taiwanese",
      "Hispanic/Latinx",
      "Middle Eastern",
      "Native American/Alaska Native/First Nations",
      "Pacific Islander",
      "South Asian (including Bangladeshi, Bhutanese, Indian, Nepali, Pakistani, and Sri Lankan",
      "Southeast Asian (including Burmese, Cambodian, Pilipino, Hmong, Indonesian, Laotian, Malaysian, Mien, Singaporean, Thai, and Vietnamese)",
      "White"
    ],

    lanuageGroup: "",
    languageGroups: ["Yes", "No"]
  })
};
</script>
