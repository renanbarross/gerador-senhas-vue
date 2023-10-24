<script>
import InstrucoesGerador from '@/components/InstrucoesGerador.vue';

export default {
  components: {
    InstrucoesGerador
  },
  data() {
    return {
      senha: "",
      numCaracteres: "",
      marcadoMaiusculas: false,
      marcadoMinusculas: false,
      marcadoNumeros: false,
      marcadoSimbolos: false,
      marcadoEmojis: false,
      forca: "",
      cores: {
        forte: {
          backgroundColor: "#98FB98",
          color: "#006400"
        },
        moderada: {
          backgroundColor: "#FFA500",
          color: "#8B4500"
        },
        fraca: {
          backgroundColor: "#FFC0CB",
          color: "#8B0000"
        }
      }
    }
  },
  methods: {
    gerarSenha() {
      this.senha = "";
      let caracteres = [];
      if (this.marcadoMaiusculas) {
        caracteres = caracteres.concat(["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"]);
      }
      if (this.marcadoMinusculas) {
        caracteres = caracteres.concat(["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"]);
      }
      if (this.marcadoNumeros) {
        caracteres = caracteres.concat(["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]);
      }
      if (this.marcadoSimbolos) {
        caracteres = caracteres.concat(["!", "@", "#", "$", "%", "&", "*", "(", ")", "-", "_", "+", "=", "[", "]", "{", "}", "|", ";", ":", "\'", "\"", "<", ">", ",", ".", "/", "\\", "?"]);
      }
      if (this.marcadoEmojis) {
        caracteres = caracteres.concat(["😀", "😘", "😂", "😁", "😉", "😋", "😆", "😊", "😎", "😍"]);
      }

      for (let i = 0; i < this.numCaracteres; i++) {
        this.senha += caracteres[Math.floor(Math.random() * caracteres.length)];
      }

      this.mostrarForcaSenha();
    },
    redefinir() {
      this.numCaracteres = "";
      this.marcadoMaiusculas = false;
      this.marcadoMinusculas = false;
      this.marcadoNumeros = false;
      this.marcadoSimbolos = false;
      this.marcadoEmojis = false;
    },
    limpar() {
      this.senha = "";
      this.forca = "";
    },
    copiar() {
      navigator.clipboard.writeText(this.senha).then(() => {
        alert("Texto copiado para a área de transferência.");
      }).catch((err) => {
        alert("Erro ao copiar o texto: " + err);
      });
    },
    mostrarForcaSenha() {
      const regexMaius = /[a-z]/;
      const regexMinus = /[A-Z]/;
      const regexNum = /[0-9]/;
      const regexSimb = /[!@#$%&*()\-_+=\[\]{}|;:\'\"<>,./\\?]/;
      const regexEmoji = /[😀😘😂😁😉😋😆😊😎😍]/;

      if (
        this.numCaracteres >= 8 &&
        regexMaius.test(this.senha) == true &&
        regexMinus.test(this.senha) == true &&
        regexNum.test(this.senha) == true &&
        regexSimb.test(this.senha) == true &&
        regexEmoji.test(this.senha) == true
      ) {
        this.forca = "Forte";

      } else {
        if (
          this.numCaracteres >= 6 &&
          regexMaius.test(this.senha) == true &&
          regexMinus.test(this.senha) == true &&
          regexSimb.test(this.senha) == true
        ) {
          this.forca = "Moderada";
        } else {
          this.forca = "Fraca";
        }
      }
    }
  },
  computed: {
    corDinamica() {
      switch (this.forca) {
        case "Forte":
          return {
            color: this.cores.forte.color,
            backgroundColor: this.cores.forte.backgroundColor
          }
        case "Moderada":
          return {
            color: this.cores.moderada.color,
            backgroundColor: this.cores.moderada.backgroundColor
          }
        case "Fraca":
          return {
            color: this.cores.fraca.color,
            backgroundColor: this.cores.fraca.backgroundColor
          }
      }
    }
  }
}
</script>

<template>
  <div id="conteudo">
    <h1>Gerador de Senhas</h1>
    <div id="layout">
      <InstrucoesGerador />
      <form>
        <label for="quant-carac">Quantidade de caracteres</label>
        <input type="text" id="quant-carac" name="quant-carac" v-model="numCaracteres">

        <div>
          <input type="checkbox" id="maius" name="maius" v-model="marcadoMaiusculas">
          <label for="maius">Incluir letras maiúsculas</label>
        </div>

        <div>
          <input type="checkbox" id="minus" name="minus" v-model="marcadoMinusculas">
          <label for="minus">Incluir letras minúsculas</label>
        </div>

        <div>
          <input type="checkbox" id="num" name="num" v-model="marcadoNumeros">
          <label for="num">Incluir números</label>
        </div>

        <div>
          <input type="checkbox" id="simb" name="simb" v-model="marcadoSimbolos">
          <label for="simb">Incluir símbolos</label>
        </div>

        <div>
          <input type="checkbox" id="emoji" name="emoji" v-model="marcadoEmojis">
          <label for="emoji">Incluir emojis</label>
        </div>

        <button type="button" @click="gerarSenha()">Gerar senha</button>
        <button type="button" @click="redefinir()">Redefinir opções</button>

        <textarea name="senha" id="senha" cols="30" rows="10" v-model="senha" @input="mostrarForcaSenha()"> </textarea>
        <div id="barra-forca" :style="corDinamica">{{ forca }}</div>
        <button type="button" @click="limpar()">Limpar</button>
        <button type="button" @click="copiar()">Copiar para a área de transferência</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
#conteudo {
  height: 100vh;
  width: 50vw;
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  text-align: center;
}

#layout {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  margin-top: 30px;
}

form {
  display: flex;
  flex-direction: column;
}

button {
  margin-top: 5px;
  margin-bottom: 5px;
}

#barra-forca {
  height: 20px;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

i {
  font-size: 20px;
  margin-right: 10px;
}

h2 {
  color: black;
  margin: 0 10px 0;
}
</style>
