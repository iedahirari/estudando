# Primeiro projeto Angular

Aplicação de estudo com **Angular 22.3**, **TypeScript 6**, dois componentes de exemplo e organização com `NgModule`. O nome da pasta `Angular 2` reflete a organização original do repositório.

## Instalação e execução

Use Node.js **22.22.3+ na linha 22**, **24.15.0+ na linha 24**, ou **26+**, e npm **8.3+**.

Dentro desta pasta:

```sh
npm ci
npm start
```

Abra [http://localhost:4200](http://localhost:4200). Para parar o servidor, pressione `Ctrl+C`. O Angular CLI é instalado com o projeto; não é necessária uma instalação global.

## Build e testes

```sh
npm run build
npm test -- --watch=false --browsers=ChromeHeadless
npm audit
```

O build de produção fica em `dist/primeiro-projeto/`. Os testes usam Karma e Jasmine e exigem Google Chrome instalado. Configure `CHROME_BIN` com o caminho do executável se ele não for detectado. Para manter os testes em execução durante o desenvolvimento, use `npm test`.

Para criar um componente, execute `npx ng generate component nome-do-componente`.

## Estrutura

- `src/app/app.component.*`: página inicial.
- `src/app/meu-primeiro/` e `src/app/meu-primeiro2/`: exercícios de componentes.
- `src/app/app.module.ts`: declarações dos componentes e configuração de ZoneJS.
- `src/main.ts`: inicialização da aplicação.
- `angular.json`: configuração do builder `@angular/build`, servidor e testes.

## Atualização de segurança

A migração do Angular 13 para o 22 removeu a antiga cadeia de ferramentas que instalava uma versão vulnerável do `node-forge`. A auditoria de **24/11/2026** retornou **zero vulnerabilidades conhecidas**; o build, os quatro testes e a inicialização no Chrome foram validados.

O build mantém um aviso de tamanho do CSS inline da página inicial: aproximadamente **3,76 kB**, acima do aviso de **2 kB** e abaixo do erro de **4 kB**. Não há testes de ponta a ponta configurados.

Mais detalhes sobre a correção e os outros projetos estão no [README principal](../../README.md). Consulte também a [documentação do Angular CLI](https://angular.dev/tools/cli).
