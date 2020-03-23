---
title: Editor de Código-fonte
description: Usar o editor de código-fonte no Visual Studio para Mac
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: d1ea74b4893032252d04ebe5fe5e65ca1eedaeeb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68493268"
---
# <a name="source-editor"></a>Editor de código-fonte

Um editor de código-fonte confiável é essencial para escrever código eficiente sucintamente. O Visual Studio para Mac fornece um editor de código-fonte sofisticados que centraliza suas interações com o IDE. O editor de código-fonte fornece os recursos que você pode esperar e precisa para realizar seu trabalho com facilidade: desde itens básicos como realce de sintaxe, snippets de código e dobramento de código, até os benefícios da sua integração com o compilador Roslyn, como preenchimento de código do IntelliSense totalmente funcional.

O editor de código-fonte no Visual Studio para Mac proporciona uma experiência perfeita com todas as outras funcionalidades no IDE, como depuração, refatoração e integração de controle de versão.

Este artigo apresenta alguns dos principais recursos do editor de código-fonte e explora como você pode usar o Visual Studio para Mac para ser o mais produtivo possível.

## <a name="the-source-editor-experience"></a>A experiência do editor de origem

Exibir e mover com eficiência por todo o código faz parte integral do fluxo de trabalho de desenvolvimento. A maneira específica de como você decide exibir e manter o código é uma decisão pessoal, que varia entre os desenvolvedores e geralmente entre projetos.

O Visual Studio para Mac oferece muitos recursos poderosos para tornar o desenvolvimento de plataforma cruzada tão acessível e o mais útil possível. As seções abaixo descrevem alguns dos destaques.

## <a name="code-folding"></a>Dobramento de código

O dobramento de código facilita a tarefa de gerenciar arquivos de código-fonte grandes permitindo aos desenvolvedores mostrar ou ocultar seções completas do código, tal como o uso de diretivas, código clichê, comentários e instruções de #region. O dobramento de código é desativado por padrão no Visual Studio para Mac

Para ativar o dobramento de código, navegue até **o Visual Studio > Preferências > Editor de Texto > Código geral de > Dobrando**:

![Opções de dobramento de código](media/source-neweditor-image1.png)

Esse menu também inclui a opção de dobra #regions e comentários por padrão, exibindo uma dica nomeada, em vez de código.

Para mostrar ou ocultar seções, use o widget de divulgação de informações ao lado de número de linha:

![Mostrar ou ocultar seções no código](media/source-neweditor-image2.png)

Você também pode mudar entre mostrar e ocultar as dobras usando o item de menu **Exibir > Dobramento > Ativar/Desativar Dobra e Ativar/Desativar Todas as Dobras**:

![Item de Menu de Dobramento](media/source-editor-image19.png)

Este item de menu também pode ser usado para habilitar ou desabilitar o dobramento de código.

## <a name="word-wrap"></a>Quebra automática de linha

A quebra automática de linha pode ajudá-lo a gerenciar espaço ao trabalhar em linhas longas de código ou com espaço de exibição limitado. A quebra automática de linha também pode garantir que a exibição de código contenha o conteúdo completo do seu arquivo de origem, mesmo ao abrir painéis que possam obscurecer a visão ou reduzir a largura da exibição de origem. 

A quebra automática de linha é desabilitada por padrão, mas pode ser habilitada por meio de **Preferências** no Visual Studio para Mac. 

Para habilitar a quebra automática de linha, navegue até o **Visual Studio > Preferências > Editor de Texto > Novo Editor > Quebra Automática de Linha**:

![Opções de quebra automática de linha](media/source-neweditor-wordwrap1.png)

Com a quebra automática de linha habilitada, as linhas que excedem a largura do modo de exibição do editor de origem serão automaticamente encapsuladas para a próxima linha no arquivo de origem. Você também pode habilitar uma opção que exibirá um glifo visível ao lado de linhas encapsuladas. Isso permitirá que você diferencie entre as linhas que foram encapsuladas automaticamente e aquelas que você encapsulou manualmente.

![Texto encapsulado com quebra automática de linha habilitada](media/source-neweditor-wordwrap2.png)

## <a name="ruler"></a>Régua

A régua de coluna é útil para determinar os comprimentos de linhas, especialmente ao trabalhar em uma equipe com diretrizes de comprimento de linha. A régua de coluna pode ser habilitada ou desabilitada navegando até **Visual Studio > Preferências > Editor de Texto > Marcadores e Réguas** e marcando (ou desmarcando) **Mostrar régua de coluna**, conforme ilustrado no imagem a seguir:

![Caixa de diálogo de preferências com "mostrar régua de coluna" realçado](media/source-editor-image5.png)

 Ela é exibida como uma linha cinza clara vertical no editor de código-fonte.

## <a name="highlight-identifier-references"></a>Realçar as referências do identificador

Com a opção "Realçar as referências do identificador" ativada, você pode selecionar qualquer símbolo no código-fonte e o editor de código-fonte fornecerá um guia visual para todas as outras referências nesse arquivo. Para ativar essa opção, acesse **Visual Studio > Preferências > Editor de Texto > Marcadores e Réguas** e selecione _Realçar referências do identificador_, conforme ilustrado na imagem a seguir:

![Caixa de diálogo de preferências com "Referências de identificador de realce" realçado](media/source-editor-image6.png)

A cor de realce também útil para indicar que algo está sendo atribuído ou referenciado. Se algo for atribuído, ele será realçado em vermelho; se for referenciado, ele será realçado em azul:

![exemplo mostrando a cor do realce](media/source-editor-image7.png)

## <a name="see-also"></a>Confira também

- [Recursos do editor de código (Visual Studio no Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Estrutura de tópicos (Visual Studio no Windows)](/visualstudio/ide/outlining)
