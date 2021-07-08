<template>
  <div class="container">
    <div class="row">
      <div class="col-md-12">
        <h3>{{ question.title }}</h3>
        <p v-html="question.description"></p>
      </div>
      <div class="col-md-12">
        <div class="row" style="border: 1px solid red" v-for="ques in question.student_exam_question_answers">
          <div class="col-md-6">
            {{ ques.title }}
          </div>

          <div class="col-md-6 mb-5">
            <draggable v-model="ques.given_answer" @change="checkChange(ques.given_answer,ques)" class="list-group"
                       group="answer">
              <transition-group>
                <div v-for="q_ans in ques.given_answer" :key="q_ans.id">
                  {{ q_ans.is_correct }}
                </div>
              </transition-group>
            </draggable>
          </div>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12">
        <draggable v-model="answer_list" class="p-5 list-group d-inline" group="answer">
          <transition-group>
            <div v-for="answer in answer_list" :key="answer.id">
              {{ answer.is_correct }}
            </div>
          </transition-group>
        </draggable>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import draggable from 'vuedraggable'
import question  from './matcing_type.json'

export default {
  name      : 'Home',
  components: {
    draggable
  },
  data      : () => {
    return {
      question       : '',
      answer_list    : [],
      student_answers: []
    }
  },
  methods   : {
    checkChange(given_answer, ques) {
      if (given_answer.length > 1) {
        this.answer_list.push(given_answer[0])
        given_answer.shift()
      }
    }
  },
  mounted() {
    this.question              = question;
    this.answer_list           = question.answer_list
    this.question.given_answer = []
  },
}
</script>

<style lang="scss">


.list-group {
  &.d-inline {
    span {
      display: inline-flex;

      div {

      }
    }
  }

  span {
    div {
      border: 1px solid rgba(0, 0, 0, 0.66);
      padding: 5px;
    }
  }
}

.student-answer {
  border: 1px solid;
  padding: 15px 5px;
}
</style>