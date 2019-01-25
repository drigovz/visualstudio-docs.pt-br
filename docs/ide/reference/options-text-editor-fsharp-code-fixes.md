---
title: Opções, Editor de Texto, F#, Correções de Código
ms.date: 01/16/2019
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.FSharp.Code_Fixes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bbe6b49d7b80138c7fc465e1c86aa13e6bc5e92d
ms.sourcegitcommit: 8bfabab73b39b3b3e68a3e8dc225515e8b310fed
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/18/2019
ms.locfileid: "54398350"
---
# <a name="options-text-editor-f-code-fixes"></a>Opções, Editor de Texto, F#, Correções de Código

Use a página de opções **Correções de Código** para especificar as configurações que podem ajudar a identificar erros de código e oferecer soluções. Para acessar essa página de opções, escolha **Ferramentas** > **Opções** e, em seguida, **Editor de Texto** > **F#** > **Correções de Código**.

## <a name="code-fixes"></a>Correções de Código

- **Simplificar nomes (remover qualificadores desnecessários)**

   Se essa caixa de seleção estiver marcada, os nomes totalmente qualificados serão simplificados quando as qualificações não forem necessárias, por exemplo, para um membro de um namespace usado com frequência.

- **Sempre colocar instruções abertas no nível superior**

   Se essa caixa de seleção estiver marcada e você digitar uma instrução aberta no código, ela será colocada no nível superior.

- **Remover instruções abertas não utilizadas**

   Se essa caixa de seleção estiver marcada, as instruções abertas no arquivo atual que não são usadas serão removidas.

- **Analisar e sugerir correções para valores não usados**

   Se essa caixa de seleção for selecionada, a ferramenta reconhecerá um valor que não está sendo usado no código. Depois, se você passar o mouse sobre o valor não usado, ele recomendará maneiras de uso do valor.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
- [Localizar alterações de código e outro histórico com o CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)