<template>
  <v-app>
    <v-form>
      <v-card>
        <v-card-title>How old are you?</v-card-title>
        <v-card-actions>
          <v-radio-group v-model="form.ageGroup">
            <v-radio
              v-for="age in ageGroups"
              :key="age"
              :label="`${age}`"
              :value="age"
            ></v-radio>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title>What is your tenure in the organisation?</v-card-title>
        <v-card-text
          >Please round down, e.g. for 1 year and 10 months, please select 1
          year.</v-card-text
        >
        <v-card-actions>
          <v-radio-group v-model="form.tenureGroup">
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
          <v-radio-group v-model="form.genderGroup">
            <v-radio
              v-for="gender in genderGroups"
              :key="gender"
              :label="`${gender}`"
              :value="gender"
            ></v-radio>

            <v-radio value="Other"></v-radio>
            <v-text-field
              :disabled="!form.genderGroup === 'Other'"
              label="Other"
            ></v-text-field>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title
          >Do you identify as transgender (or another non-cisgender
          identity)?</v-card-title
        >
        <v-card-actions>
          <v-radio-group v-model="form.transGroup">
            <v-radio
              v-for="trans in transGroups"
              :key="trans"
              :label="`${trans}`"
              :value="trans"
            ></v-radio>

            <v-radio value="Other"></v-radio>
            <v-text-field
              :disabled="!form.transGroup === 'Other'"
              label="Other"
            ></v-text-field>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title>What is your sexual orientation?</v-card-title>
        <v-card-actions>
          <v-radio-group v-model="form.sexidGroup">
            <v-radio
              v-for="sexid in sexidGroups"
              :key="sexid"
              :label="`${sexid}`"
              :value="sexid"
            ></v-radio>

            <v-radio value="Other"></v-radio>
            <v-text-field
              :disabled="!form.sexidGroup === 'Other'"
              label="Other"
            ></v-text-field>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title
          >What is your racial or ethnic identity? (Select all that
          apply)</v-card-title
        >
        <v-card-actions>
          <v-container fluid>
            <v-checkbox
              v-for="race in raceGroups"
              :key="race"
              :label="`${race}`"
              :value="race"
            ></v-checkbox>
            <v-row align="center">
              <v-checkbox value="Other"></v-checkbox>
              <v-text-field
                :disabled="!form.raceGroup === 'Other'"
                label="Other"
              ></v-text-field>
            </v-row>
          </v-container>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title>Is English your first language?</v-card-title>
        <v-card-actions>
          <v-radio-group v-model="form.languageGroup">
            <v-radio
              v-for="language in languageGroups"
              :key="language"
              :label="`${language}`"
              :value="language"
            ></v-radio>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title>What language do you speak at home?</v-card-title>
        <v-card-actions>
          <v-text-field label="Language" single-line></v-text-field>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title
          >Do you consider yourself to have a disability under the Equality Act
          2010?</v-card-title
        >
        <v-card-actions>
          <v-radio-group v-model="form.disabilityGroup">
            <v-radio
              v-for="disability in disabilityGroups"
              :key="disability"
              :label="`${disability}`"
              :value="disability"
            ></v-radio>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title
          >Do you identify with any of the following religions? (Select all that
          apply)</v-card-title
        >
        <v-card-actions>
          <v-container fluid>
            <v-checkbox
              v-for="religion in religionGroups"
              :key="religion"
              :label="`${religion}`"
              :value="religion"
            ></v-checkbox>
            <v-row align="center">
              <v-checkbox value="Other"></v-checkbox>
              <v-text-field
                :disabled="!form.religionGroup === 'Other'"
                label="Other"
              ></v-text-field>
            </v-row>
          </v-container>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title>Are you a parent or caretaker of children?</v-card-title>
        <v-card-actions>
          <v-radio-group v-model="form.parentGroup">
            <v-radio
              v-for="parent in parentGroups"
              :key="parent"
              :label="`${parent}`"
              :value="parent"
            ></v-radio>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title>Are you a caretaker of adults?</v-card-title>
        <v-card-actions>
          <v-radio-group v-model="form.carerGroup">
            <v-radio
              v-for="carer in carerGroups"
              :key="carer"
              :label="`${carer}`"
              :value="carer"
            ></v-radio>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title
          >What is your legal marital or civil partnership status
          group?</v-card-title
        >
        <v-card-actions>
          <v-radio-group v-model="form.maritalGroup">
            <v-radio
              v-for="marital in maritalGroups"
              :key="marital"
              :label="`${marital}`"
              :value="marital"
            ></v-radio>

            <v-radio value="Other"></v-radio>
            <v-text-field
              :disabled="!form.maritalGroup === 'Other'"
              label="Other"
            ></v-text-field>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card
        >for (let element of submitEvent.target.elements) {
        console.log(element.value); }
        <v-card-title>What is your highest level of education?</v-card-title>
        <v-card-actions>
          <v-radio-group v-model="form.educationGroup">
            <v-radio
              v-for="education in educationGroups"
              :key="education"
              :label="`${education}`"
              :value="education"
            ></v-radio>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title
          >What is your parents highest level of education?</v-card-title
        >
        <v-card-actions>
          <v-radio-group v-model="form.parentEduGroup">
            <v-radio
              v-for="parentEdu in parentEduGroups"
              :key="parentEdu"
              :label="`${parentEdu}`"
              :value="parentEdu"
            ></v-radio>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title
          >What type of secondary school did you attend?</v-card-title
        >
        <v-card-actions>
          <v-radio-group v-model="form.schoolGroup">
            <v-radio
              v-for="school in schoolGroups"
              :key="school"
              :label="`${school}`"
              :value="school"
            ></v-radio>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-title
          >Have you ever served on active duty in the U.K. Armed
          Forces?</v-card-title
        >
        <v-card-actions>
          <v-radio-group v-model="form.forcesGroup">
            <v-radio
              v-for="forces in forcesGroups"
              :key="forces"
              :label="`${forces}`"
              :value="forces"
            ></v-radio>
          </v-radio-group>
        </v-card-actions>
      </v-card>

      <v-card>
        <v-card-actions>
          <v-btn color="success" class="mr-4" @click="submit">
            Submit
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-form>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';

export default {
  name: "App",
  components: {
    // HelloWorld,
  },
  methods: {
    submit() {
      console.log(this.form);
    }
  },
  data: () => ({
    form: {
      ageGroup: "",
      tenureGroup: "",
      genderGroup: "",
      transGroup: "",
      sexidGroup: "",
      raceGroup: "",
      languageGroup: "",
      disabilityGroup: "",
      religionGroup: "",
      parentGroup: "",
      carerGroup: "",
      maritalGroup: "",
      educationGroup: "",
      parentEduGroup: "",
      schoolGroup: "",
      forcesGroup: ""
    },

    ageGroups: ["16-24", "25-34", "35-44", "45-54", "55-64", "65+"],

    tenureGroups: [
      "Less than 1 year",
      "1 year",
      "2 years",
      "3 years",
      "4 years",
      "5 years or more"
    ],

    genderGroups: ["Woman", "Man", "Genderqueer or non-binary", "Agender"],

    transGroups: ["Yes", "No"],

    sexidGroups: [
      "Asexual",
      "Bisexual",
      "Gay",
      "Heterosexual or straight",
      "Lesbian",
      "Pansexual",
      "Queer"
    ],

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

    languageGroups: ["Yes", "No"],

    disabilityGroups: ["Yes", "No"],

    religionGroups: [
      "Protestantism",
      "Catholicism",
      "Christianity",
      "Judaism",
      "Islam",
      "Buddhism",
      "Hinduism",
      "Sikhism",
      "Inter/Non-denominational",
      "No Religion"
    ],

    parentGroups: ["Yes", "No"],

    carerGroups: ["Yes", "No"],

    maritalGroups: [
      "Married",
      "Civil partnership",
      "Cohabiting",
      "Single (including divorced, widowed, separated"
    ],

    educationGroups: [
      "Post graduate level or equivalent",
      "University level or equivalent",
      "A levels or equivalent",
      "GCSE or equivalent",
      "None of the above"
    ],

    parentEduGroups: [
      "Post graduate level or equivalent",
      "University level or equivalent",
      "A levels or equivalent",
      "GCSE or equivalent",
      "None of the above"
    ],

    schoolGroups: [
      "State comprehensive/academy",
      "Grammar school",
      "Private/'Public school'",
      "Not sure"
    ],

    forcesGroups: ["Yes", "No"]
  })
};
</script>
