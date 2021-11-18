<template>
  <div class="principal">
    <div class="entradaDados">
      <label for="entradaBinario">valor binario</label>
      <input @input="adicionarBit" name="entradaBinario" type="text">
    </div>
    <button @click="converter" class="btConversor">Converter</button>
    <div class="saidaDados">
      <label for="saidaDecimal">Valor decimal</label>
      <input v-model="valorDecimal" disabled name="saidaDecimal" type="text">
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      valorBinario: '',
      valorDecimal: ''
    }
  },
  methods: {
    bin2dec(valor) {
      const valorInvertido = valor.split("").reverse();
      let total = 0, pos = 0;
      for (const bit of valorInvertido) {
        total += bit * 2 ** pos;
        pos++;
      }
      return total;
    },
    converter() {
      this.valorDecimal = this.bin2dec(this.valorBinario)
    },
    adicionarBit(e){
          let erro = false
          for (const bit of e.target.value) {
              if (bit!=='0' && bit!== '1') {
                  erro = true
              }
          }
          if (erro) {
              e.target.value = this.valorBinario
          }
          this.valorBinario = e.target.value
      }

  }
  

}
</script>

<style>

</style>