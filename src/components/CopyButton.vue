<template>
  <span ref="dataToCopy">{{ data }}</span
  >&nbsp;<button
    class="copy-button hide--on-mobile"
    :data-tooltip="$t('general.copy')"
  >
    <img
      :alt="$t('general.copy')"
      class="icon"
      :src="require(`@/assets/icons/copy.png`)"
      v-on:click="copy(data)"
    /></button
  ><button
    class="copy-button hide--on-mobile"
    :data-tooltip="$t('general.copyCommand')"
  >
    <img
      :alt="$t('general.copyCommand')"
      class="icon"
      :src="require(`@/assets/icons/command.png`)"
      v-on:click="copy(command)"
    />
  </button>
</template>

<script>
export default {
  props: {
    data: String,
    command: String
  },
  methods: {
    copy(data) {
      const input = document.createElement("input");
      document.body.appendChild(input);
      input.setAttribute("value", data);
      input.select();
      if (document.execCommand("copy")) {
        document.execCommand("copy");
        console.log("复制成功");
      }
      document.body.removeChild(input);

      // let el = this.$refs.dataToCopy;
      // let range = document.createRange();
      // range.selectNode(el);
      // window.getSelection().addRange(range);
      // console.log(range, "fuck");
      // document.execCommand("copy");
      // window.getSelection().removeAllRanges();
    }
  }
};
</script>

<style scoped lang="scss">
.copy-button {
  padding: 4px;
  cursor: pointer;
  outline: none;
  border: none;
  background-color: #ffffff00;
  border-radius: 4px;

  &:hover {
    background-color: #52525220;
  }

  &:active {
    background-color: #52525240;
    transform: translateY(1px);
  }
}
</style>
