<template>
  <div id="inputTable">
      <table>
          <tr>
              <input-button class="colspan2" :buttonText="'C'" :type="'clear'" />
              <input-button :buttonText="'⌫'" :type="'backspace'" />
              <input-button :buttonText="'÷'" :type="'op'" />

              <input-button :buttonText="'7'" :type="'num'" />
              <input-button :buttonText="'8'" :type="'num'" />
              <input-button :buttonText="'9'" :type="'num'" />
              <input-button :buttonText="'×'" :type="'op'" />

              <input-button :buttonText="'4'" :type="'num'" />
              <input-button :buttonText="'5'" :type="'num'" />
              <input-button :buttonText="'6'" :type="'num'" />
              <input-button :buttonText="'-'" :type="'op'" />

              <input-button :buttonText="'1'" :type="'num'" />
              <input-button :buttonText="'2'" :type="'num'" />
              <input-button :buttonText="'3'" :type="'num'" />
              <input-button :buttonText="'+'" :type="'op'" />

              <input-button class="colspan3" :buttonText="'0'" :type="'num'"/>
              <input-button :buttonText="'='" :type="'enter'" />
          </tr>
      </table>
  </div>
</template>

<script>
import InputButton from './InputButton.vue'
export default {
  components: { 
      InputButton 
  },
  data() {
      return {
        
      }
  }

}
</script>

<style>

</style>