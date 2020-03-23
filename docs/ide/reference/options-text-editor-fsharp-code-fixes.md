---
title: Opções, Editor de Texto, F#, Correções de Código
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5c736be59c257d98085831971d6b7b9dc2a0ef3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72666280"
---
# <a name="options-text-editor--f--code-fixes"></a>Opções: Editor de texto > F# > Correções de Código

Use a página de opções Correções de Código para especificar as configurações que podem ajudar a identificar erros de código e oferecer soluções. Para acessar esta página de opções, escolha**Opções de** **ferramentas** > e, em seguida, escolha **'Correções de código' do**Editor > de **texto****F#** > .

## <a name="code-fixes"></a>Correções de Código

- **Simplificar nomes (remover qualificadores desnecessários)**

  Se essa caixa de seleção estiver marcada, os nomes totalmente qualificados serão simplificados quando as qualificações não forem necessárias, por exemplo, para um membro de um namespace usado com frequência.

- **Sempre colocar instruções abertas no nível superior**

  Se essa caixa de seleção estiver marcada e você digitar uma instrução `open` no código, ela será colocada no nível superior.

- **Remover instruções abertas não utilizadas**

  Se esta caixa de controle estiver selecionada, os documentos serão analisados ​​para localizar instruções `open` não utilizadas e será exibida uma lâmpada de [Ação Rápida](../quick-actions.md) com uma ação para remover todas as instruções `open` não utilizadas.

- **Analisar e sugerir correções para valores não usados**

  Se essa caixa de seleção for selecionada, a ferramenta reconhecerá um valor que não está sendo usado no código. Depois, se você passar o mouse sobre o valor não usado, ele recomendará maneiras de uso do valor.

## <a name="see-also"></a>Confira também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
- [Localizar alterações de código e outro histórico com o CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
