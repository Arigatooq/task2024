<template>
  <div class="container">
    <div class="poem">
      <div class="poem-center">
        <div>
          <span class="squares">
            <span :class="quatrain1Visible ? 'square' : 'whiteSquare'">
              <input type="checkbox" class="checkbox" v-model="quatrain1Visible" :disabled="disableCheckbox(1)"
                @change="checkVisibility" />
            </span>
            <span :class="quatrain2Visible ? 'square' : 'whiteSquare'">
              <input type="checkbox" class="checkbox" v-model="quatrain2Visible" :disabled="disableCheckbox(2)"
                @change="checkVisibility" />
            </span>
            <span :class="quatrain3Visible ? 'square' : 'whiteSquare'">
              <input type="checkbox" class="checkbox" v-model="quatrain3Visible" :disabled="disableCheckbox(3)"
                @change="checkVisibility" />
            </span>
            <span :class="quatrain4Visible ? 'square' : 'whiteSquare'">
              <input type="checkbox" class="checkbox" v-model="quatrain4Visible" :disabled="disableCheckbox(4)"
                @change="checkVisibility" />
            </span>
          </span>
        </div>

        <div class="poem-text">
          <div class="author">
            <div class="poem-name">
              <h2>Invictus</h2>
            </div>
            <div class="poem-author">
              <p class="william">By William Ernest Henley</p>
            </div>
          </div>
          <div class="quatrain" v-if="quatrain1Visible">
            <p>Out of the night that covers me,<br />
              <span> Black as the pit from pole to pole,<br /> </span>
              I thank whatever gods may be <br />
              <span> For my unconquerable soul.<br /></span>
            </p>
          </div>
          <div class="quatrain" v-if="quatrain2Visible">
            <p>In the fell clutch of circumstance <br />
              <span>I have not winced nor cried aloud. <br /></span>
              Under the bludgeonings of chance <br />
              <span>My head is bloody, but unbowed.</span>
            </p>
          </div>
          <div class="quatrain" v-if="quatrain3Visible">
            <p>Beyond this place of wrath and tears <br />
              <span>Looms but the Horror of the shade,</span> <br />
              And yet the menace of the years <br />
              <span>Finds and shall find me unafraid.</span>
            </p>
          </div>
          <div class="quatrain" v-if="quatrain4Visible">
            <p>It matters not how strait the gate, <br />
              <span>How charged with punishments the scroll,</span> <br />
              I am the master of my fate, <br />
              <span>I am the captain of my soul.</span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const quatrain1Visible = ref(true);
const quatrain2Visible = ref(true);
const quatrain3Visible = ref(true);
const quatrain4Visible = ref(true);
const visibleCount = ref([]);

const checkVisibility = () => {
  visibleCount.value = [
    quatrain1Visible.value,
    quatrain2Visible.value,
    quatrain3Visible.value,
    quatrain4Visible.value,
  ].filter(Boolean).length;
};

const disableCheckbox = (quatrainNumber) => {
  if (visibleCount.value === 1) {
    switch (quatrainNumber) {
      case 1:
        return quatrain1Visible.value;
      case 2:
        return quatrain2Visible.value;
      case 3:
        return quatrain3Visible.value;
      case 4:
        return quatrain4Visible.value;
      default:
        return false;
    }
  }
  return false;
};
</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
}

.container {
  max-width: 1080px;
  min-inline-size: 450px;
  max-inline-size: 4320px;
  font-family: serif;
}

.squares {
  display: flex;
  margin-top: 4.7vw;
}

.square {
  width: 1.9vw;
  height: 1.9vw;
  border: 1px solid black;
  background-color: black;
  margin-left: 2vw;
}

.whiteSquare {
  width: 1.9vw;
  height: 1.9vw;
  border: 1px solid black;
  margin-left: 2vw;
}

.poem h1 {
  margin-bottom: 10px;
}

h2 {
  font-weight: normal;
  display: flex;
  align-items: end;
  font-size: 4vw;
}

.author {
  display: flex;
  justify-content: center;
}

.william {
  display: flex;
  align-items: center;
  font-size: 1.8vw;
  height: 140%;
  margin-left: 2vw;
}

.quatrain {
  font-size: 2.5vw;
  margin-block-end: 2vw;
  line-height: 1;
}

.quatrain span {
  padding-left: 4vw;
}

.poem-center {
  display: flex;
  justify-content: center;
  gap: 50px;
}

.poem-text {
  width: 55vw;
  text-align: left;
}

.checkbox {
  opacity: 0;
  height: 1vw;
  width: 1vw;
}
</style>
