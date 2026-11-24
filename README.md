# Estudando

Repositório de exercícios para aprender TypeScript, Angular e Java. Cada pasta contém um exemplo independente.

## Estrutura

| Pasta | Conteúdo |
| --- | --- |
| [Angular 2/hello-typescript](<Angular 2/hello-typescript>) | Exemplos de variáveis, funções, classes, arrays e arrow functions em TypeScript, com JavaScript correspondente. |
| [Angular 2/primeiro-projeto](<Angular 2/primeiro-projeto>) | Aplicação Angular com a página inicial e dois componentes de estudo. |
| [Java/Comecando](Java/Comecando) | Programa de console que imprime `Olá Mundo!`. |
| [Java/OlaMundoSwing](Java/OlaMundoSwing) | Interface gráfica com Java Swing, criada no NetBeans. |

O nome da pasta `Angular 2` foi mantido para preservar a organização original. A aplicação `primeiro-projeto` agora usa **Angular 22.3**.

## Executar a aplicação Angular

Requisitos:

- Node.js **22.22.3 ou superior na linha 22**, **24.15.0 ou superior na linha 24**, ou **26 ou superior**.
- npm **8.3 ou superior**.
- Google Chrome instalado para executar os testes.

Não é necessário instalar o Angular CLI globalmente; os comandos usam a instalação do projeto.

```sh
git clone https://github.com/iedahirari/estudando.git
cd "estudando/Angular 2/primeiro-projeto"
npm ci
npm start
```

Abra [http://localhost:4200](http://localhost:4200). As alterações no código são recarregadas durante o desenvolvimento. Para encerrar o servidor, pressione `Ctrl+C`.

`npm ci` instala as versões registradas em `package-lock.json`, permitindo reproduzir a instalação validada.

### Comandos úteis

Execute dentro de `Angular 2/primeiro-projeto`:

| Comando | Função |
| --- | --- |
| `npm start` | Inicia o servidor de desenvolvimento. |
| `npm run build` | Gera a versão de produção em `dist/primeiro-projeto/`. |
| `npm run watch` | Recompila em modo de desenvolvimento quando os arquivos mudam. |
| `npm test` | Executa os testes com Karma e Jasmine no Chrome. |
| `npm test -- --watch=false --browsers=ChromeHeadless` | Executa os testes uma vez, sem abrir uma janela do Chrome. |
| `npm audit` | Consulta vulnerabilidades conhecidas nas dependências. |
| `npx ng generate component nome-do-componente` | Cria um componente com o Angular CLI local. |

Se o Chrome não for encontrado automaticamente, configure a variável `CHROME_BIN` com o caminho do executável. Não há uma suíte de testes de ponta a ponta configurada.

### Onde alterar o código

- `src/app/app.component.*`: componente principal e página inicial.
- `src/app/meu-primeiro/` e `src/app/meu-primeiro2/`: componentes dos exercícios.
- `src/app/app.module.ts`: registro dos componentes e configuração do módulo.
- `src/main.ts`: inicialização da aplicação.
- `angular.json`: configuração dos comandos de build, servidor e testes.

Veja também o [README da aplicação](<Angular 2/primeiro-projeto/README.md>).

## Exercícios de TypeScript

A pasta `Angular 2/hello-typescript` contém arquivos de estudo, sem instalação npm própria. Abra `main.ts` para acompanhar os exemplos. O arquivo JavaScript correspondente pode ser executado a partir da raiz do repositório:

```sh
node "Angular 2/hello-typescript/main.js"
```

Os exemplos não imprimem resultados no console. Para observar os valores, use um depurador ou acrescente chamadas a `console.log` durante o estudo.

## Projetos Java

Os dois projetos incluem configuração de NetBeans e arquivos de build Ant, com nível de linguagem Java 11.

1. Instale um JDK compatível com Java 11 e o NetBeans com suporte a Java.
2. Em **File > Open Project**, selecione `Java/Comecando` ou `Java/OlaMundoSwing`.
3. Confira o JDK configurado nas propriedades do projeto e execute **Run Project**.

O projeto Swing precisa de um ambiente gráfico para abrir a janela. Os projetos Java não usam as dependências npm da aplicação Angular.

## Correção de segurança

A aplicação usava Angular 13 e ferramentas antigas de desenvolvimento. A cadeia `webpack-dev-server → selfsigned → node-forge` instalava Forge 0.10.0, afetado pelo alerta de falsificação de assinatura RSA PKCS#1 v1.5 com `DigestInfo` não canônico ([GHSA-6qrw-m8cv-hcxf](https://github.com/digitalbazaar/forge/security/advisories/GHSA-6qrw-m8cv-hcxf)).

A atualização para **Angular 22.3 e TypeScript 6** substituiu o sistema de build antigo por `@angular/build`. Essa cadeia foi removida e o `node-forge` deixou de fazer parte das dependências. Os componentes de estudo foram preservados, mantendo a organização com `NgModule` e a detecção de mudanças por ZoneJS.

Na verificação de **24/11/2026**:

- `npm audit` passou de **133 para zero vulnerabilidades conhecidas**.
- O build de produção foi concluído.
- Os **quatro testes** passaram no Chrome sem interface.
- A aplicação iniciou e renderizou os dois componentes de estudo no Chrome.

Esses resultados se referem às versões do lockfile e à base de avisos consultada nessa data. Novos avisos podem surgir; execute `npm audit` periodicamente e valide build e testes ao atualizar dependências.

O build ainda emite um aviso sobre o CSS inline da página inicial: aproximadamente **3,76 kB**, acima do limite de aviso de **2 kB** e abaixo do limite de erro de **4 kB**. A atualização não incluiu validação dos projetos Java.
