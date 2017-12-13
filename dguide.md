# Developer Guide

![Roadmap](/images/plano_comlegenda.png)

### Instalação

1. instalar nativescript (docs.nativescript.org)
2. instalar dependências com `npm install` no root do projecto(não esquecer que temos um registo interno npm https://npm.dev.mysns.pt/)
3. usar nativescript para executar o projecto

### WebPack
Isso torna a aplicação do buraco muito mais rápida

Para construir com antecedência, deve executar comandos npm (ver o projeto package.json)

ex:`npm run build-android-bundle`

**Nota 1:** ISTO VAI MUDAR NA PRÓXIMA VERSÃO DE NATIVECRIPT (3.4)

**Nota 2:**

* para o cartão com pdf(Testamento vital) temos que especificar algumas entradas no webpack config(`webpack.config.js` da linha 166 a 171)

**Nota 3:** É necessário validar se é preciso atualizar dependências regularmente (sempre que possivel, **diariamente**)
### Testes

Executar e2e tests

	npm run e2e

Executar Unit tests

	test <Platform>

### Releasing process

#### iOS:

Para para uma release para iOS é necessária uma conta itunes e executar `npm run publish-ios-bundle`

#### Android:
*  *build* com webpack(`npm run build-android-bundle --release --key-store-path ./my-release-key.keystore --key-store-password 916265505 --key-store-alias MySNSstore --key-store-alias-password 916265505`)
* isto assinará automaticamente (*auto sign*) o apk e agora precisa fazer upload para a playstore console

## Notas Prioritárias

* Alguns dos plugins estão no nosso registro npm interno porque precisavam de modificações
* O plugin `nativescript-hook-debug-production` não funciona bem (não deteta o debug no modo de lançamento, mas recebemos um *pull request* para corrigir. Esperar pela nova versão do nativescript porque precisamos ter o Webpack a trabalhar com ele)
* há muitas coisas que podem ser otimizadas para o ngrx
* sentry plugin foi atualizado
* nativescript `advanced-webview-interface` também possui uma versão interna (internal release, pois o autor está inativo)
* Vendor.ts precisa de algumas otimizações, agora existem algumas bibliotecas repetidas nos diferentes módulos do aplicativo (https://docs.nativescript.org/best-practices/bundling-with-webpack)
* ngrx e componentes normais precisam de testes
* Testes e2e precisam de uma conta demo do backend

**Cartão Atividade Fisica / Medições de Saúde**
* o plugin `nativescript-health-data` também tem um *pull request* pendente para retornar dados uniformes (foi libertada internamente uma versão com as mudanças desse *pull request*)
* estamos a usar uma versão interna do circle plugin na **atividade fisica** por causa de um *pull request* que fizemos. Enquanto isso o autor lançou uma versão mais recente (então isso precisa ser atualizado)

