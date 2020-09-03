---
title: Opções, Editor de Texto, C/C++, Experimental | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e4f239c5be290f6d79f52f55dbcb6da60d10785
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851699"
---
# <a name="options-text-editor-cc-experimental"></a>Opções, Editor de Texto, C/C++, Experimental
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ao alterar essas opções, você pode alterar o comportamento relacionado ao IntelliSense e ao banco de dados de navegação quando estiver programando em C ou C++.

 Para acessar essa página, na caixa de diálogo **Opções**, no painel esquerdo, expanda **Editor de Texto**, expanda **C/C++** e escolha **Experimental**.

 Esses recursos estão disponíveis em uma instalação do Visual Studio 2015 Atualização 1 RC.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Navegação
 **Habilitar novo mecanismo de banco de dados** Isso deve acelerar automaticamente a população do banco de dados e tornar todas as operações do banco de dados mais rápidas (sem perda de precisão) para operações como **ir para definição** e **Localizar todas as referências**. (Apenas feche e reabra a solução para aplicar as alterações, você não precisa reiniciar o Visual Studio.)

## <a name="intellisense"></a>IntelliSense
 **Lista de membros ponto-a-seta** Substitui '. ' por '-> ' quando aplicável para a lista de membros.

## <a name="refactoring"></a>Refatoração
 **Habilitar a função de extração** Extraia o código selecionado para sua própria função e substitua o código por uma chamada para a nova função. Para acessar esse recurso, clique com botão direito do mouse no código selecionado e selecione **Ações Rápidas** ou simplesmente pressione o atalho padrão Ctrl+Ponto [Ctrl+.].

 **Habilitar a assinatura de alteração** Adicionar, reordenar e excluir parâmetros de uma função e propagar as alterações para todos os sites de chamada. Para acessar esse recurso, clique com botão direito do mouse em qualquer uso da função e selecione **Ações Rápidas** ou simplesmente pressione o atalho padrão Ctrl+Ponto [Ctrl+.].

## <a name="text-editor"></a>Editor de Texto
 **Habilitar escopos de expansão** Se habilitada, você pode colocar o texto selecionado entre chaves digitando ' {' no editor de texto.

 **Habilitar precedência de expansão** Se habilitada, você pode colocar o texto selecionado entre parênteses digitando ' (' no editor de texto.

 Para recursos adicionais do editor de texto na Galeria do Visual Studio, consulte a lista [aqui](https://marketplace.visualstudio.com/). Um exemplo é [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f) (Correções Rápidas C++), que dá suporte ao seguinte:

- **Add missing #include (Adicionar #include ausente)** –sugere #include relevantes para símbolos desconhecidos no seu código

- **Add using namespace/Fully qualify symbol (Adicionar usando namespace/símbolo totalmente qualificado)** – semelhante ao item anterior, mas para namespaces

- **Add missing semicolon (adicionar ponto e vírgula ausente)**

- **Ajuda do MSDN** – pesquisa as mensagens de erro no MSDN

  Você pode passar o mouse sobre um rabisco para obter uma lâmpada ou usar o atalho de teclado padrão Ctrl+Ponto (Ctrl+.). Observe que para o atalho de teclado, o cursor do sistema não precisa ser posicionado sobre o erro específico ou o token, você pode simplesmente estar na mesma linha do erro para invocar sugestões para qualquer item nessa linha.

## <a name="see-also"></a>Consulte Também
 [Configurando a](../../ide/reference/setting-language-specific-editor-options.md) [refatoração de opções do editor de idioma específico no C++ (blog do vc)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
