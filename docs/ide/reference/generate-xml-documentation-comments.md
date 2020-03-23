---
title: Inserir comentários da documentação XML
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77706382"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Como inserir comentários XML para geração de documentação

O Visual Studio pode ajudá-lo a documentar os elementos de código, como classes e métodos, gerando automaticamente a estrutura padrão de comentários da documentação XML. No tempo de compilação, você pode gerar um arquivo XML contendo os comentários da documentação.

> [!TIP]
> Para obter informações sobre como configurar o nome e o local do arquivo XML gerado, confira [Documentar seu código com comentários XML (Guia C#)](/dotnet/csharp/codedoc).

O arquivo XML gerado pelo compilador pode ser distribuído em conjunto com o assembly do .NET para que o Visual Studio e outros IDEs possam usar o IntelliSense para mostrar informações rápidas sobre os tipos e membros. Além disso, o arquivo XML pode ser executado por ferramentas como [DocFX](https://dotnet.github.io/docfx/) e [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) para gerar sites de referência de API.

> [!NOTE]
> O comando **Inserir Comentário**, que insere comentários da documentação XML automaticamente está disponível em [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) e em [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). No entanto, você pode inserir arquivos de [comentários da documentação XML em C++](/cpp/build/reference/xml-documentation-visual-cpp) manualmente e ainda gerar arquivos da documentação XML no tempo de compilação.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Para inserir comentários XML para um elemento de código

1. coloque o cursor de texto acima do elemento que você deseja documentar, por exemplo, um método.

2. Realize um dos seguintes procedimentos:

   - Digite `///` em C# ou `'''` em Visual Basic

   - No menu **Editar**, escolha **IntelliSense** > **Inserir Comentário**

   - No menu de clique com o botão direito do mouse ou contexto ou logo acima do elemento de código, escolha **'Inserir** > **comentário'**

   O modelo XML é gerado imediatamente acima do elemento de código. Por exemplo, ao comentar um método, ele gera ** \<\> ** o ** \<\> ** ** \<elemento sumário,\> ** um elemento param para cada parâmetro e um elemento de retorno para documentar o valor de retorno.

   ![Modelo de comentário XML – C#](media/doc-preview-cs.png)

   ![Modelo de comentário XML – Visual Basic](media/doc-preview-vb.png)

3. Insira descrições para cada elemento XML para documentar totalmente o elemento de código.

   ![Comentário concluído](media/doc-result-cs.png)

Você pode usar estilos em comentários XML que renderizarão em Informações Rápidas ao pairar sobre o elemento. Esses estilos incluem: itálico, negrito, balas e um link clicável.

   ![Comentário concluído](media/doc-style-cs.png) 

> [!NOTE]
> Há um [opção](../../ide/reference/options-text-editor-csharp-advanced.md) para ativar/desativar os comentários da documentação XML depois de digitar `///` em C# ou `'''` em Visual Basic. Na barra de menus, escolha **Opções de** > **ferramentas** para abrir a caixa de diálogo **Opções.** Em seguida, navegue até **o Editor de** > Texto**C#** ou **O Avançado Básico** > **Advanced**. Na seção **Ajuda do Editor**, procure a opção **Gerar comentários da documentação XML**.

## <a name="see-also"></a>Confira também

- [Comentários da documentação XML (Guia de Programação em C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentando seu código com comentários em XML (Guia do C#)](/dotnet/csharp/codedoc)
- [Como criar documentação XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Comentários c++](/cpp/cpp/comments-cpp)
- [Documentação XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Geração de código](../code-generation-in-visual-studio.md)
