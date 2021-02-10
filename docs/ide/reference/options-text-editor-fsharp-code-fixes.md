---
title: Opções, Editor de Texto, F#, Correções de Código
description: 'Saiba como usar a página de correções de código na seção F # para especificar as configurações que podem ajudar a identificar erros de código e oferecer soluções.'
ms.custom: SEO-VS-2020
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ca1b3816786ab611af8acb1cb99eea406ca6ad45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943946"
---
# <a name="options-text-editor--f--code-fixes"></a>Opções: o editor de texto > F # > correções de código

Use a página de opções Correções de Código para especificar as configurações que podem ajudar a identificar erros de código e oferecer soluções. Para acessar essa página de opções, escolha **ferramentas**  >  **Opções** e, em seguida, escolha o **Editor de texto**  >  **F #**  >  **correções de código**.

## <a name="code-fixes"></a>Correções de Código

- **Simplificar nomes (remover qualificadores desnecessários)**

  Se essa caixa de seleção estiver marcada, os nomes totalmente qualificados serão simplificados quando as qualificações não forem necessárias, por exemplo, para um membro de um namespace usado com frequência.

- **Sempre colocar instruções abertas no nível superior**

  Se essa caixa de seleção estiver marcada e você digitar uma instrução `open` no código, ela será colocada no nível superior.

- **Remover instruções abertas não utilizadas**

  Se esta caixa de controle estiver selecionada, os documentos serão analisados ​​para localizar instruções `open` não utilizadas e será exibida uma lâmpada de [Ação Rápida](../quick-actions.md) com uma ação para remover todas as instruções `open` não utilizadas.

- **Analisar e sugerir correções para valores não usados**

  Se essa caixa de seleção for selecionada, a ferramenta reconhecerá um valor que não está sendo usado no código. Depois, se você passar o mouse sobre o valor não usado, ele recomendará maneiras de uso do valor.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
- [Localizar alterações de código e outro histórico com o CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)
