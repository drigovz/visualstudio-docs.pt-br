---
title: Visão geral do protocolo do servidor de idiomas | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703110"
---
# <a name="language-server-protocol"></a>Language Server Protocol

## <a name="what-is-the-language-server-protocol"></a>O que é o Protocolo do Servidor de Idiomas?

Apoiar recursos de edição ricos, como auto-conclusões de código fonte ou **Ir à Definição** para uma linguagem de programação em um editor ou IDE é tradicionalmente muito desafiador e demorado. Normalmente requer escrever um modelo de domínio (um scanner, um analisador, um verificador de tipo, um construtor e muito mais) na linguagem de programação do editor ou IDE. Por exemplo, o plugin Eclipse CDT, que fornece suporte para C/C++ no Eclipse IDE é escrito em Java desde que o próprio Eclipse IDE é escrito em Java. Após essa abordagem, significaria implementar um modelo de domínio C/C++ no TypeScript for Visual Studio Code e um modelo de domínio separado em C# para O Visual Studio.

Criar modelos de domínio específicos para linguagem também é muito mais fácil se uma ferramenta de desenvolvimento puder reutilizar bibliotecas específicas de idiomas existentes. No entanto, essas bibliotecas geralmente são implementadas na própria linguagem de programação (por exemplo, bons modelos de domínio C/C++ são implementados em C/C++). Integrar uma biblioteca C/C++ em um editor escrito no TypeScript é tecnicamente possível, mas difícil de fazer.

### <a name="language-servers"></a>Servidores de idiomas

Outra abordagem é executar a biblioteca em seu próprio processo e usar a comunicação interprocesse para falar com ela. As mensagens enviadas de um lado para o outro formam um protocolo. O protocolo de servidor de idiomas (LSP) é o produto da padronização das mensagens trocadas entre uma ferramenta de desenvolvimento e um processo de servidor de idiomas. Usar servidores de linguagem ou demônios não é uma idéia nova ou nova. Editores como Vim e Emacs vêm fazendo isso há algum tempo para fornecer suporte semântico de auto-conclusão. O objetivo do PSL era simplificar esses tipos de integrações e fornecer uma estrutura útil para expor os recursos linguísticos a uma variedade de ferramentas.

Ter um protocolo comum permite a integração de recursos de linguagem de programação em uma ferramenta de desenvolvimento com mínimo barulho, reutilizando uma implementação existente do modelo de domínio do idioma. Um back-end de servidor de idiomas pode ser escrito em PHP, Python ou Java e o LSP permite que ele seja facilmente integrado em uma variedade de ferramentas. O protocolo funciona em um nível comum de abstração para que uma ferramenta possa oferecer serviços de linguagem ricos sem precisar entender completamente as nuances específicas do modelo de domínio subjacente.

## <a name="how-work-on-the-lsp-started"></a>Como começou o trabalho no PSL

O PSL evoluiu ao longo do tempo e hoje está na Versão 3.0. Tudo começou quando o conceito de um servidor de idiomas foi captado pela OmniSharp para fornecer recursos de edição ricos para C#. Inicialmente, a OmniSharp usou o protocolo HTTP com uma carga json e foi integrada a vários editores, incluindo [visual studio code](https://code.visualstudio.com).

Na mesma época, a Microsoft começou a trabalhar em um servidor de idiomas TypeScript, com a ideia de suportar TypeScript em editores como Emacs e Sublime Text. Nesta implementação, um editor se comunica através do stdin/stdout com o processo do servidor TypeScript e usa uma carga JSON inspirada no protocolo de depurador V8 para solicitações e respostas. O servidor TypeScript foi integrado ao plugin TypeScript Sublime e ao CÓDIGO VS para edição rica do TypeScript.

Depois de ter integrado dois servidores de idiomas diferentes, a equipe do VS Code começou a explorar um protocolo de servidor de idioma comum para editores e IDEs. Um protocolo comum permite que um provedor de idiomas crie um único servidor de idiomas que pode ser consumido por diferentes IDEs. Um consumidor de servidor de idiomas só precisa implementar o lado cliente do protocolo uma vez. Isso resulta em uma situação ganha-ganha tanto para o provedor de idiomas quanto para o consumidor de idiomas.

O protocolo do servidor de idiomas começou com o protocolo usado pelo servidor TypeScript, expandindo-o com mais recursos de idioma inspirados na API de linguagem de código VS. O protocolo é apoiado com JSON-RPC para invocação remota devido à sua simplicidade e bibliotecas existentes.

A equipe do VS Code protótipou o protocolo implementando vários servidores de linguagem linter que respondem a solicitações de fiapos (scan) um arquivo e retornam um conjunto de avisos e erros detectados. O objetivo era fisar um arquivo como o usuário edita em um documento, o que significa que haverá muitas solicitações de fiação durante uma sessão de editor. Fazia sentido manter um servidor funcionando para que um novo processo de fiação não precisasse ser iniciado para cada edição do usuário. Vários servidores linter foram implementados, incluindo as extensões ESLint e TSLint do VS Code. Esses dois servidores linter são implementados no TypeScript/JavaScript e executados no Node.js. Eles compartilham uma biblioteca que implementa a parte do cliente e do servidor do protocolo.

## <a name="how-the-lsp-works"></a>Como funciona o PSL

Um servidor de idiomas é executado em seu próprio processo, e ferramentas como Visual Studio ou VS Code se comunicam com o servidor usando o protocolo de idioma sobre JSON-RPC. Outra vantagem do servidor de idiomas que opera em um processo dedicado é que problemas de desempenho relacionados a um único modelo de processo são evitados. O canal de transporte real pode ser stdio, sockets, chamados pipes, ou node ipc se o cliente e o servidor estiverem escritos em Node.js.

Abaixo está um exemplo de como uma ferramenta e um servidor de idiomas se comunicam durante uma sessão de edição de rotina:

![Diagrama de fluxo lsp](media/lsp-flow-diagram.png)

* **O usuário abre um arquivo (referido como documento) na ferramenta**: A ferramenta notifica o servidor de idiomas de que um documento está aberto ('textDocument/didOpen'). A partir de agora, a verdade sobre o conteúdo do documento não está mais no sistema de arquivos, mas mantida pela ferramenta na memória.

* **O usuário faz edições**: A ferramenta notifica o servidor sobre a alteração do documento ('textDocument/didChange') e as informações semânticas do programa são atualizadas pelo servidor de idiomas. Como isso acontece, o servidor de idiomas analisa essas informações e notifica a ferramenta com os erros e avisos detectados ('textDocument/publishDiagnostics').

* **O usuário executa "Ir para definição" em um símbolo no editor**: A ferramenta envia uma solicitação de 'textDocument/definition' com dois parâmetros: (1) o uri do documento e (2) a posição de texto de onde a solicitação Ir para Definição foi iniciada para o servidor. O servidor responde com o uri do documento e a posição da definição do símbolo dentro do documento.

* **O usuário fecha o documento (arquivo)**: Uma notificação 'textDocument/didClose' é enviada da ferramenta, informando ao servidor de idiomas que o documento não está mais na memória e que o conteúdo atual está agora atualizado no sistema de arquivos.

Este exemplo ilustra como o protocolo se comunica com o servidor de idiomas no nível de recursos do editor como "Ir para definição", "Encontrar todas as referências". Os tipos de dados usados pelo protocolo são 'tipos de dados' de editor ou IDE, como o documento de texto atualmente aberto e a posição do cursor. Os tipos de dados não estão no nível de um modelo de domínio de linguagem de programação que normalmente forneceria árvores de sintaxe abstratas e símbolos de compilador (por exemplo, tipos resolvidos, namespaces, ...). Isso simplifica significativamente o protocolo.

Agora vamos olhar para a solicitação 'textDocument/definition' com mais detalhes. Abaixo estão as cargas que vão entre a ferramenta cliente e o servidor de idiomas para a solicitação "Ir para definição" em um documento C++.

Este é o pedido:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Esta é a resposta:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

Em retrospectiva, descrever os tipos de dados no nível do editor e não no nível do modelo de linguagem de programação é uma das razões para o sucesso do protocolo do servidor de idiomas. É muito mais simples padronizar um URI de documento de texto ou uma posição de cursor em comparação com a padronização de uma árvore de sintaxe abstrata e símbolos de compilador em diferentes linguagens de programação.

Quando um usuário está trabalhando com idiomas diferentes, o VS Code normalmente inicia um servidor de idiomas para cada linguagem de programação. O exemplo abaixo mostra uma sessão onde o usuário trabalha em arquivos Java e SASS.

![java e sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Funcionalidades

Nem todos os servidores de idiomas podem suportar todos os recursos definidos pelo protocolo. Portanto, o cliente e o servidor anunciam seu recurso suportado definido através de 'recursos'. Como exemplo, um servidor anuncia que pode lidar com a solicitação 'textDocument/definition', mas pode não lidar com a solicitação 'espaço de trabalho/símbolo'. Da mesma forma, os clientes podem anunciar que são capazes de fornecer notificações 'prestes a salvar' antes que um documento seja salvo, para que um servidor possa calcular edições texuais para formatar automaticamente o documento editado.

## <a name="integrating-a-language-server"></a>Integrando um servidor de idiomas

A integração real de um servidor de idiomas em uma determinada ferramenta não é definida pelo protocolo do servidor de idiomas e é deixada aos implementores da ferramenta. Algumas ferramentas integram servidores de idioma genericamente, tendo uma extensão que pode iniciar e conversar com qualquer tipo de servidor de idioma. Outros, como o VS Code, criam uma extensão personalizada por servidor de idioma, de modo que uma extensão ainda seja capaz de fornecer alguns recursos de idioma personalizados.

Para simplificar a implementação de servidores de idiomas e clientes, existem bibliotecas ou SDKs para as partes do cliente e do servidor. Essas bibliotecas são fornecidas para diferentes idiomas. Por exemplo, há um [módulo npm cliente de idioma](https://www.npmjs.com/package/vscode-languageclient) para facilitar a integração de um servidor de idioma em uma extensão de código VS e outro módulo [npm do servidor de idiomas](https://www.npmjs.com/package/vscode-languageserver) para escrever um servidor de idiomas usando node.js. Esta é a [lista](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) atual de bibliotecas de suporte.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Usando o Protocolo do Servidor de Idiomas no Visual Studio

* [Adicionando uma extensão do Protocolo do Servidor de Idiomas](adding-an-lsp-extension.md) - Aprenda a integrar um servidor de idiomas ao Visual Studio.
