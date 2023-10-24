# Gerador de senhas

Trata-se de um gerador de senhas em que o usuário pode especificar condições em tela e solicitar a geração de uma senha aleatória. Ele pode escolher a quantidade de caracteres que a senha terá, se ela incluirá ou não letras maiúsculas, letras minúsculas, números, símbolos ou emojis. É possível ainda editar a senha gerada manualmente conforme o gosto da pessoa, copiar a senha através de um botão, além de observar sua força após uma geração ou modificação.

## Descrição do projeto

Para gerar uma senha o usuário deve preencher a quantidade de caracteres que ela deve possuir e selecionar os tipos
de caracteres que deseja incluir.

Em seguida, deve clicar no botão "Gerar senha" e ver o resultado no campo em branco logo abaixo. Se quiser gerar
uma senha nova sob as mesmas condições o botão "Gerar senha" pode ser clicado de novo. Se desejado,
pode modificar os critérios antes de clicar no botão. Caso queira limpar todas opções escolhidas, deve clicar em
"Redefinir opções".

Dada a aleatoriedade do processo, nem sempre a senha gerada conterá necessariamente todos os tipos de
caracteres selecionados. Sendo assim, a senha pode ser gerada de novo ou modificada manualmente, até ficar
da forma desejada. Tanto após a geração como durante a modificação, uma barra mostrando a
força da senha poderá ser vista abaixo do campo da senha. Os critérios de força estão assim estabelecidos:

FORTE - 8 caracteres ou mais, inclui letras maiúsculas, letras minúsculas, números, símbolos e inclui emojis.
MODERADA - 6 ou 7 caracteres, inclui letras maiúsculas, letras minúsculas e símbolos.
FRACA - Quando deixa de atender os critérios acima.

O botão "Limpar" pode ser usado quando caso o usuário queira limpar o campo da senha e o botão "Copiar para a área de transferência" pode ser usado para copiar a senha gerada.

Essas instruções também estão presentes na interface do gerador.

## Tecnologia utilizada

Framework Vue.js 3 (Options API).

## Configuração Recomendada da IDE

VSCode + Volar (e desative o Vetur)

## Personalização da Configuração
Consulte Referência de Configuração do Vite.

## Configuração do Projeto
```sh
npm install
```

### Compilação e Recarga Automática para Desenvolvimento
```sh
npm run dev
```

### Compilação e Minificação para Produção
```sh
npm run build
```
