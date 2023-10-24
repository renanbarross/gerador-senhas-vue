<template>
  <div id="instrucoes">
    <p>
      <span id="titulo-instrucoes">INSTRUÇÕES:</span>
      <br><br>
      Para gerar uma senha preencha a quantidade de caracteres que ela deve possuir e selecione os tipos
      de caracteres que deseja incluir.
      <br><br>
      Em seguida, clique no botão "Gerar senha" e veja o resultado no campo em branco logo abaixo. Se quiser gerar
      uma senha nova sob as mesmas condições o botão "Gerar senha" pode ser clicado de novo. Se desejado,
      modifique os critérios antes de clicar no botão. Caso queira limpar todas opções escolhidas, clique em
      "Redefinir opções".
      <br><br>
      Dada a aleatoriedade do processo, nem sempre a senha gerada conterá necessariamente todos os tipos de
      caracteres selecionados. Sendo assim, a senha pode ser gerada de novo ou modificada manualmente, até ficar
      da forma desejada. Tanto após a geração como durante a modificação, uma barra mostrando a
      força da senha poderá ser vista abaixo do campo da senha. Os critérios de força estão assim estabelecidos:
      <br><br>
      FORTE - 8 caracteres ou mais, inclui letras maiúsculas, letras minúsculas, números, símbolos e inclui emojis.
      <br>
      MODERADA - 6 ou 7 caracteres, inclui letras maiúsculas, letras minúsculas e símbolos.
      <br>
      FRACA - Quando deixa de atender os critérios acima.
      <br><br>
      O botão "Limpar" pode ser usado quando se quiser limpar o campo da senha e o botão "Copiar para a área de
      transferência" pode ser usado para copiar a senha gerada.
    </p>
  </div>
</template>
<style>
#instrucoes {
  height: fit-content;
  width: 500px;
  margin-right: 120px;
  padding: 10px;
  border: 4px double black;
  font-size: 12px;
}

p {
  text-align: center;
}

#titulo-instrucoes {
  font-weight: bold;
}
</style>