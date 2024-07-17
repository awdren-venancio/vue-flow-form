<template>
  <span>
    <input
      ref="input"
      type="file"
      v-bind:accept="question.accept"
      v-bind:multiple="question.multiple"
      v-bind:required="question.required"
      v-on:keyup.enter.prevent="onEnter"
      v-on:keyup.tab.prevent="onEnter"
      v-on:focus="setFocus"
      v-on:blur="unsetFocus"
      v-on:change="onChange"
    />
  </span>
</template>

<script>
/*
  Copyright (c) 2020 - present, DITDOT Ltd. - MIT Licence
  https://github.com/ditdot-dev/vue-flow-form
  https://www.ditdot.hr/en
*/

import TextType from './TextType.vue'
import {QuestionType} from '../../models/QuestionModel'

export default {
  extends: TextType,
  name: QuestionType.File,
  methods: {
    validate() {
      return !this.question.required || this.hasValue
    },
    setAnswer(answer) {
      this.question.filelist = this.$refs.input.files
      this.question.answer = answer
      this.question.answered = this.isValid()
    },
  },
}
</script>
