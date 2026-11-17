# Acervo — canal de atualizações

Repositório público que distribui os instaladores do **Acervo** e o manifesto de atualização lido pelo aplicativo. O código-fonte fica no repositório privado `kauandonargas/coursevault`.

- **Instaladores**: cada versão é um [release](https://github.com/kauandonargas/coursevault-releases/releases) com o instalador para Windows e o arquivo `.sha256` correspondente.
- **`update.json`**: versão atual, link do instalador, SHA-256 e notas. O aplicativo consulta este arquivo, baixa o instalador e só o executa depois de conferir o SHA-256.

## Como uma versão chega aqui

O fluxo **Publicar Acervo** do repositório privado gera o instalador e, quando tem o segredo `COURSEVAULT_RELEASES_TOKEN`, cria o release e atualiza o `update.json` diretamente.

Sem esse segredo, a versão entra pelo fluxo **Importar versão do Acervo** (`.github/workflows/import.yml`): um branch `import/X.Y.Z` com um `import-request.json` aponta o instalador gerado e o manifesto; o fluxo confere o SHA-256, cria o release e ativa a versão. O formato do pedido está descrito no início do arquivo do fluxo.
