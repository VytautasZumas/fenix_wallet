# Fenix Wallet

<p align="center">
  <img src="src/assets/fenix-wallet-logo.png" width="150" alt="Logo da Fenix Wallet">
</p>

<p align="center">
  <strong>Carteira-laboratório para capacitação em Bitcoin, Ethereum e TRON.</strong>
</p>

Desenvolvida por **Vytautas Zumas** para uso exclusivo em capacitações.

## Sobre o projeto

A **Fenix Wallet** é uma carteira educacional executada no navegador. Ela foi criada
para demonstrar, de forma prática, como uma carteira determinística funciona desde a
criação da seed até a assinatura e transmissão de uma transação.

O projeto permite que alunos explorem conceitos como BIP39, passphrase, caminhos de
derivação, contas, índices, endereços, saldos, taxas, recursos de rede, chaves privadas
e assinatura local.

> [!CAUTION]
> A Fenix Wallet **não foi auditada** e **não é uma carteira para uso pessoal,
> investimentos ou custódia de patrimônio**. Nunca utilize uma seed que já proteja
> fundos reais.

## Objetivos educacionais

A carteira pode ser utilizada para demonstrar:

- criação de mnemônicos BIP39 com 12 ou 24 palavras;
- restauração de uma carteira a partir de um mnemônico;
- efeito de uma passphrase BIP39 sobre os endereços derivados;
- funcionamento de carteiras HD e caminhos de derivação;
- diferenças entre conta, change e índice;
- derivação de caminhos exatos, listas e intervalos;
- criação de endereços em diferentes redes;
- consulta de saldos por meio de endpoints públicos;
- preparação e revisão de transações;
- assinatura local e transmissão para a rede;
- funcionamento de faucets e exploradores de blocos;
- necessidade de TRX para movimentar USDT TRC-20;
- diferenças práticas entre testnets e mainnets.

## Redes disponíveis

| Ecossistema | Rede de testes | Mainnet | Ativos |
| --- | --- | --- | --- |
| Bitcoin | Signet | Bitcoin Mainnet | sBTC / BTC |
| Ethereum | Sepolia | Ethereum Mainnet | Sepolia ETH / ETH |
| TRON | Shasta | TRON Mainnet | TRX e USDT TRC-20 |

As redes de testes possuem atalhos para faucets. A disponibilidade, as regras e o
funcionamento desses serviços dependem dos respectivos operadores.

## Principais recursos

### Seed e passphrase

- geração de mnemônicos com 12 ou 24 palavras;
- validação de palavras e checksum BIP39;
- suporte a passphrase BIP39 opcional;
- comparação do endereço produzido por diferentes passphrases;
- processamento do material secreto no navegador;
- encerramento manual da sessão.

### Derivação HD

- suporte a caminhos de derivação exatos;
- expansão de listas e intervalos de índices;
- visualização didática dos componentes do caminho;
- suporte a padrões BIP44, BIP49, BIP84 e BIP86, conforme a rede;
- exportação dos dados públicos derivados em CSV;
- exibição controlada da chave privada para demonstração.

### Recebimento e saldos

- endereço público e QR Code;
- consulta de saldo nativo;
- consulta de TRX e USDT nas redes TRON;
- links para exploradores de blocos;
- endpoints configuráveis durante a sessão;
- atalhos para faucets das redes de testes.

### Transações

- preparação da transação antes da assinatura;
- revisão de rede, origem, destino, valor e taxas;
- assinatura local no navegador;
- transmissão da transação para a rede selecionada;
- suporte a BTC, ETH, TRX e USDT TRC-20;
- avisos sobre Energy, Bandwidth e possível consumo de TRX;
- proteções adicionais antes de utilizar uma mainnet.

### Interface

- idiomas português e inglês;
- modos claro e escuro;
- layout responsivo;
- preferências visuais salvas localmente;
- versão compilada em um único arquivo HTML.

## Como os dados são processados

A seed, a passphrase e as chaves privadas são processadas localmente e permanecem
somente na memória da aba enquanto a sessão estiver aberta. O projeto não possui um
servidor próprio para receber ou armazenar esses segredos.

As únicas informações enviadas aos endpoints das redes são os dados públicos
necessários para operações como:

- consulta de saldos e UTXOs;
- estimativa de taxas e gas;
- consulta de recursos da rede TRON;
- preparação de chamadas de contrato;
- transmissão de transações assinadas.

> [!IMPORTANT]
> Um provedor RPC pode registrar endereços consultados, endereço IP, horário e outros
> metadados. Ele não recebe a seed, mas pode relacionar os endereços consultados na
> mesma sessão.

Apenas as preferências de idioma e tema são gravadas no armazenamento local do
navegador. A seed e a passphrase não são salvas por esse mecanismo.

## O que não se deve fazer

Não utilize a Fenix Wallet para:

- guardar patrimônio;
- criar sua carteira pessoal definitiva;
- importar uma seed usada em outra carteira;
- movimentar quantias que você não aceita perder integralmente;
- operar em computador público, compartilhado ou não confiável;
- projetar, fotografar ou compartilhar seeds e chaves privadas;
- copiar material secreto sem considerar o histórico da área de transferência;
- substituir uma hardware wallet ou uma carteira auditada;
- assumir que o código está livre de falhas, vulnerabilidades ou dependências
  comprometidas.

> [!WARNING]
> Extensões do navegador, malwares, captura de tela, histórico da área de transferência
> e alterações no código podem expor o material secreto. O processamento local reduz
> alguns riscos, mas não transforma esta aplicação em uma carteira segura para
> patrimônio.

## Uso de mainnets

As mainnets estão disponíveis somente para demonstrações com transações reais de
pequeno valor. Antes de liberá-las, a interface exige confirmações de risco e mantém a
autorização ativa por tempo limitado.

Mesmo com essas proteções:

1. crie uma seed exclusiva para a aula;
2. não reutilize essa seed em outra carteira;
3. envie apenas uma quantia pequena que você aceita perder;
4. confira rede, endereço, valor e taxa;
5. encerre a sessão ao final da demonstração;
6. considere a seed utilizada no laboratório inadequada para custódia futura.

Transações confirmadas em blockchain são, em regra, irreversíveis.

## Executar o projeto

### Requisitos

- Node.js `20.19` ou mais recente;
- npm;
- navegador moderno com suporte a JavaScript e Web Crypto;
- conexão com a internet para consultas e transmissões.

### Desenvolvimento

```bash
npm install
npm run dev
```

O terminal mostrará o endereço local que deve ser aberto no navegador.

### Testes

```bash
npm test
```

### Gerar o HTML distribuível

```bash
npm run build
```

O arquivo final será criado em:

```text
dist/index.html
```

Esse arquivo contém os scripts, estilos e recursos necessários para a interface em um
único HTML. Para melhor compatibilidade entre navegadores e políticas de segurança,
recomenda-se servi-lo por HTTP ou HTTPS.

Uma forma simples de testar a versão compilada é:

```bash
npm run preview
```

## Tecnologias utilizadas

- JavaScript com módulos ES;
- Vite e `vite-plugin-singlefile`;
- `@scure/bip39` e `@scure/bip32`;
- `@scure/btc-signer`;
- Viem;
- TronWeb;
- QRCode;
- Vitest.

## Aviso de responsabilidade

Este software é fornecido para fins exclusivamente educacionais, sem garantias de
segurança, disponibilidade, adequação ou ausência de erros. O usuário é responsável
por revisar o código, compreender os riscos e decidir se deve executar qualquer
operação.

**Não use a Fenix Wallet como carteira de custódia.**
