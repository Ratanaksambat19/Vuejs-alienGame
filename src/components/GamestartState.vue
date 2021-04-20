<template>
  <div class="modal">
    <h1 id="header">You're an alienzombie.</h1>
    <h1>hello</h1>
    <p>
      In order to survive on Earth, you have to pretend to be a human on this
      planet. You took over the body of a nearby hooman, but the trouble is,
      their best friend showed up!
    </p>
    <p>
      They look suspicious. Answer the questions right to make sure identity is
      kept secret!
    </p>
    <h2>Which hooman do you want to be?</h2>
      <p
        v-for="option in characterChoices"
        :key="option"
        class="character-choices"
      >
        <input
          v-model="characterinput"
          :id="option"
          :value="option"
          type="radio"
        />
        <label :for="option">{{ option }}</label>
        <br />
      </p>
     <button @click="pickcharacter">Pick Your Character</button>
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  data() {
    return {
      characterinput: '',
    }
  },
  methods: {
    pickcharacter() {
      this.$store.commit("pickCharacter", this.characterinput)
      this.$store.commit("updateUiState", "CharacterChosen")
    }
  },
    computed: {
        ...mapState([
            "characterChoices", 
            "character",
        ])
    },
};

</script>

<style lang="scss" scoped>
</style>