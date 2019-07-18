---
title: Como restaurar snippets de refatoração C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9f81514db881ad26a5fa827b0bde11df2467f23d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186276"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Como restaurar snippets de refatoração C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Operações de refatoração C# dependem de snippets de código encontrados no seguinte diretório:  
  
 *Diretório de instalação*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID de idioma*\Refactoring  
  
 Se esse diretório de Refatoração, ou quaisquer arquivos nesse diretório, for excluído ou corrompido, as operações de refatoração C# poderão não funcionar no IDE. Os procedimentos a seguir podem ajudá-lo a restaurar snippets de código de refatoração C#.  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Para verificar se snippets de refatoração C# estão disponíveis por meio do Gerenciador de Snippets de Código  
  
1. No menu **Ferramentas**, selecione **Gerenciador de Snippet de Código**.  
  
2. Na caixa de diálogo **Gerenciador de Snippet de Código**, selecione **Visual C#** na lista suspensa **Linguagem**.  
  
     A pasta **Refatoração** deve aparecer na lista de pastas do modo de exibição de árvore.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Para restaurar a refatoração, consulte o comentário no Gerenciador de Snippets de Código  
  
1. Se a pasta **Refatoração** não aparecer na lista de pastas do modo de exibição de árvore do Gerenciador de Snippets de Código, use este procedimento para adicionar snippets de refatoração de volta ao Gerenciador de Snippets de Código.  
  
2. No menu **Ferramentas**, selecione **Gerenciador de Snippet de Código**.  
  
3. Na caixa de diálogo **Gerenciador de Snippet de Código**, selecione **Visual C#** na lista suspensa **Linguagem**.  
  
4. Clique em **Adicionar**. A caixa de diálogo **Diretório de Snippets de Código**, que ajuda a localizar e especificar o diretório a adicionar de volta ao Gerenciador de Snippets de Código, é exibida.  
  
5. Localize a pasta **Refatoração** cujo caminho de diretório é:  
  
     *Diretório de instalação*\Microsoft Visual Studio 14.0\VC#\Snippets\\*ID de idioma*\Refactoring  
  
     O caminho real é semelhante ao seguinte para uma instalação padrão:  
  
     C:\Program Files\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring.  
  
6. Clique em **Abrir** na caixa de diálogo **Diretório de Snippets de Código** e clique em **OK** no Gerenciador de Snippets de Código.  
  
## <a name="see-also"></a>Veja também  
 [Snippets de código do Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Refatoração (C#)](../csharp-ide/refactoring-csharp.md)   
 [Snippets de código](../ide/code-snippets.md)
