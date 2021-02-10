---
title: Inserir comentários da documentação XML
description: Saiba como inserir comentários de documentação XML em seu código que você pode usar para criar um arquivo XML gerado pelo compilador para distribuir junto com seu assembly .NET.
ms.custom: SEO-VS-2020
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2c203d9a445d9426a8079801a856e20f7be82229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946560"
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

   - No menu de contexto ou clique com o botão direito do mouse ou logo acima do elemento de código, escolha **trecho**  >  **Inserir Comentário**

   O modelo XML é gerado imediatamente acima do elemento de código. Por exemplo, ao comentar um método, ele gera o **\<summary\>** elemento, um **\<param\>** elemento para cada parâmetro e um **\<returns\>** elemento para documentar o valor de retorno.

   ![Modelo de comentário XML – C#](media/doc-preview-cs.png)

   ![Modelo de comentário XML – Visual Basic](media/doc-preview-vb.png)

3. Insira descrições para cada elemento XML para documentar totalmente o elemento de código.

   ![Captura de tela mostrando o comentário concluído.](media/doc-result-cs.png)

Você pode usar estilos em comentários XML que serão renderizados em informações rápidas ao passar o mouse sobre o elemento. Esses estilos incluem: itálico, negrito, marcadores e um link clicável.

   ![Captura de tela mostrando o comentário concluído com marcas de estilo para itálico, negrito, marcadores e um link clicável.](media/doc-style-cs.png) 

> [!NOTE]
> Há um [opção](../../ide/reference/options-text-editor-csharp-advanced.md) para ativar/desativar os comentários da documentação XML depois de digitar `///` em C# ou `'''` em Visual Basic. Na barra de menus, escolha **ferramentas**  >  **Opções** para abrir a caixa de diálogo **Opções** . Em seguida, navegue até o **Editor de texto**  >  **C#** ou **Basic**  >  **Advanced**. Na seção **Ajuda do Editor**, procure a opção **Gerar comentários da documentação XML**.

## <a name="see-also"></a>Confira também

- [Comentários da documentação XML (Guia de Programação em C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Documentando seu código com comentários em XML (Guia do C#)](/dotnet/csharp/codedoc)
- [Como criar documentação XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Comentários do C++](/cpp/cpp/comments-cpp)
- [Documentação XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Geração de código](../code-generation-in-visual-studio.md)
