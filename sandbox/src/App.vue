<template>
  <main>
    <div id="app">
      <h3> CHartrt bender type {{ statsDisplay.length }}</h3>
      <p v-if="characterList.length === 0">There are no characters</p>
      <ul v-else-if="characterList.length % 2 === 0">
        <li v-for="character in characterList">
          <p>{{ character.name }}</p>
          <button @click="favoriteCharacter(character)">⭐ Favorite</button>
        </li>
      </ul>
      <h2>Favorite Characters</h2>
      <ul v-if="favoriteList.length > 0">
        <li v-for="character in favoriteList">{{ character }}</li>
      </ul>
      <p v-else>No favorite characters yet!</p>
      <h2>New Character</h2>
      <pre>{{ newCharacter }}</pre>

      <label for="character-name">Name</label>
      <input type="text" v-model="newCharacter.name" @keyup.enter="addNewCharacter" />

      <p>
        <span v-for="(character, index) in characterList">{{ character.name }}{{ index === characterList.length - 1 ? ''
          : ', '
          }}
        </span>
      </p>

    </div>
  </main>
</template>

<script>
export default {
  data: () => ({
    chartype: [],
    newCharacter: {
      name: ''
    },
    characterList: [
      {
        name: 'Aang',
        type: 'Waterbender'
      },
      {
        name: 'Zuko',
        type: 'Waterbender'
      },
      {
        name: 'Toph',
        type: 'bender'
      },
      {
        name: 'Katara',
        type: 'bender'
      }
    ],
    favoriteList: [],

  }),
  computed: {
    statsDisplay() {
      return this.characterList.filter(item => item.type === 'bender')


    },
  },
  methods: {
    addNewCharacter() {
      this.characterList.push(this.newCharacter)
      this.newCharacter = { name: '' }
    },
    favoriteCharacter(character) {
      this.favoriteList.push(character)
    }
  }
}
</script>
