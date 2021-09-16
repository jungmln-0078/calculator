<template>
  <td>
     <a href="#" @click="clickInput">{{ buttonText }}</a>
  </td>
</template>

<script>
export default {
    props: {
        buttonText: String,
        type: String
    },
    methods: {
        clickInput() {
            switch (this.type) {
                case 'num':
                    this.$parent.$parent.numberInput(this.buttonText, this.type);
                    break;
                case 'op':
                    this.$parent.$parent.operandInput(this.buttonText, this.type);
                    break;
                case 'enter':
                    this.$parent.$parent.compute('enter');
                    break;
                case 'backspace':
                    this.$parent.$parent.backspace();
                    break;
                case 'clear':
                    this.$parent.$parent.clear();
                    break;
            }
        }
    }
}
</script>

<style>

</style>