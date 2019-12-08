<script>
import Draggable from 'vuedraggable'

export default {
  components: {
    Draggable,
  },
  data() {
    return {
      phrases: [
        [],
        [],
        [],
      ],
      words: [
        'I', 'You', 'He', 'She',
        'was', 'am', 'are',
        'blue', 'tall', 'short',
      ],
    }
  },
  mounted() {
    const words = this.$route.query.words;

    if (words !== undefined) {
      this.words = this.$route.query.words.split(',')
    }
  },
  methods: {
    addPhrase() {
      this.phrases.push([])
    },
  },
}
</script>

<template>
  <div class="container">
    <div class="phrases">
      <div v-for="(phrase, index) in phrases" :key="index">
        Phrase #{{index}}
        <draggable v-model="phrases[index]" group="words" class="phrase">
          <span class="word" v-for="(phraseWord, w) in phrase" :key="w">{{phraseWord}}</span>
        </draggable>
      </div>
      <button type="button" @click="addPhrase()">Add</button>
    </div>
    <div class="words">
      <draggable v-model="words" group="words">
        <span class="word" v-for="(word, w) in words" :key="w">{{word}}</span>
      </draggable>
    </div>
  </div>
</template>

<style scoped>
  * {
    box-sizing: border-box;
  }

  .container {
    display: flex;
    flex-direction: row;
  }

  .phrases {
    width: 70%;
    padding: 20px;
    max-height: 100vh;
    overflow: scroll;
  }

  .words {
    padding: 20px;
  }

  .word {
    background: #eee;
    border: 1px solid #ccc;
    display: inline-block;
    padding: 5px 10px;
    margin: 3px;
  }

  .phrase {
    padding: 10px;
    border: 1px dashed #eee;
    min-height: 62px;
    margin-bottom: 10px;
  }
</style>
