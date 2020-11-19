---
title: Conclusão do IntelliSense para tipos & métodos de extensão
description: Como usar a conclusão do IntelliSense para tipos e métodos de extensão que você ainda não importou com uma `using` diretiva.
ms.custom: SEO-VS-2020
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d2ac806b4a83b23a783c59eeee5df801c9237685
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94900914"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>Conclusão do IntelliSense para tipos não importados e métodos de extensão

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** O IntelliSense dá a conclusão para tipos não importados e métodos de extensão.

**Quando:** Você deseja usar um tipo ou métodos de extensão que já têm uma dependência em seu projeto, mas a instrução using ainda não foi adicionada ao seu arquivo.

**Por que:** Você não precisa adicionar manualmente a instrução using ao seu arquivo.

## <a name="how-to"></a>Como fazer

1. Depois de começar a digitar o nome de um método de tipo ou de extensão que tenha uma dependência em seu projeto, o IntelliSense fornecerá sugestões. Os itens de namespaces não importados teriam o namespace contido mostrado como sufixo.

   > [!TIP]
   > Você pode mostrar/ocultar itens de namespaces não importados sob demanda, usando o **botão de expansão (Alt + A)** que aparece na parte inferior esquerda da lista de conclusão. Para alterar o comportamento padrão, vá para **ferramentas**  >  **Opções**  >  **Editor de texto**  >  **C#**  /  **Basic**  >  **IntelliSense** e procure **Mostrar itens de namespaces não importados**.

2. Selecione e confirme um item não importado.

   A instrução using será adicionada automaticamente ao seu arquivo.

   ![Preenchimento do IntelliSense para tipos não importados](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Confira também

- [IntelliSense](../using-intellisense.md)
- [Refatoração](../refactoring-in-visual-studio.md)
