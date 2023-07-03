<template>
<div class="result">
  <div class="title">Jouw resultaat: <br>{{ results[resultIndex].title }} </div>
  <div class="desc"> {{ results[resultIndex].desc }} </div>
</div>
</template>

<script>
export default {
  props: ["results", "totalResult"],
  computed: {
    resultIndex() {
      let index = 0;
      this.results.forEach((element, i) => {
        if(element.min <= this.totalResult && element.max >= this.totalResult) {
          index = i;
        }
      });
      return index;
    }
  }
}
</script>t