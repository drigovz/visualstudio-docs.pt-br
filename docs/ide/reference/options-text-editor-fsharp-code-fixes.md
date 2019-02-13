---
title: Opções, Editor de Texto, F#, Correções de Código
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bb9daee86fec058fca68740eaea3b9436e5570d6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933409"
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