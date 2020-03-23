---
title: Snippets de código
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: c06f9f7dc7e5a672e3fd5da3f3fc834fe223a783
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585412"
---
# <a name="code-snippets"></a>Snippets de código

Snippets de código são pequenos blocos de código reutilizável que podem ser inseridos em um arquivo de código usando um comando do menu do clique com o botão direito (menu de contexto) ou uma combinação de teclas de atalho. Eles geralmente contêm os blocos de código mais usados, como `try-finally` ou `if-else`, mas podem ser usados para inserir métodos ou classes inteiras.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Snippet de código (Visual Studio para Mac)](/visualstudio/mac/snippets).

Os snippets de código estão disponíveis para uma variedade de linguagens, incluindo C#, C++, Visual Basic, XML e T-SQL, entre outras. Para visualizar todos os trechos instalados disponíveis para um idioma, abra o **Gerenciador de trechos** de código no menu **Ferramentas** (ou, **pressione Ctrl**+**K**, **Ctrl**+**B**), e escolha o idioma no menu suspenso na parte superior.

![Caixa de diálogo Gerenciador de Snippets de Código](media/code-snippets-manager.png)

Em geral, os snippets de código podem ser acessados das seguintes maneiras:

- Na barra de menu, escolha **Editar** > **IntelliSense** > **Inserir trecho**

- No menu com o botão direito do mouse ou contexto no editor de código, escolha **Snippet** > **Insert Snippet**

- Do teclado, **pressione Ctrl**+**K,****Ctrl**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Snippets de expansão e snippets de “envolver com”

Há dois tipos de snippet de código no Visual Studio: snippets de expansão, que são adicionados a um ponto de inserção especificado e podem substituir um atalho de snippet; e snippets Surround-with (somente C# e C++), que são adicionados ao redor de um bloco de código selecionado.

Um exemplo de um snippet de expansão: em C#, o atalho tryf é usado para inserir um bloco try-finally:

```csharp
try
{

}
finally
{

}
```

Você pode inserir este trecho clicando em **Inserir trecho** no menu com o botão direito do mouse (menu de contexto) da janela de código, em seguida, **Visual C#**, em seguida, digitar `tryf`e, em seguida, pressionar **Guia**. Ou, você `tryf` pode digitar e pressionar **Tab** duas vezes.

Um exemplo de um snippet “envolver com”: em C++, o atalho `if` pode ser usado como um snippet de inserção ou um snippet “envolver com”. Se você selecionar uma linha `return FALSE;`de código (por exemplo), e, em seguida, escolher **Surround With** > **if**, o trecho é expandido ao redor da linha:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parâmetros de substituição de snippet

Snippets podem conter parâmetros de substituição, que são espaços reservados que você deve substituir de acordo com o código exato que você está escrevendo. No exemplo anterior, `true` é um parâmetro de substituição, que você poderia substituir pela condição apropriada. A substituição feita é repetida para cada instância do mesmo parâmetro de substituição no snippet.

Por exemplo, no Visual Basic, há um snippet de código que insere uma propriedade. Para inserir o trecho, escolha > **'Snippet' Inserir trecho** do menu com o botão direito do mouse ou contexto em um arquivo de código Visual Basic. **Snippet** Em seguida, escolha **Propriedades de padrões de** > **código, procedimentos, eventos** > **definir uma propriedade**.

![Menu de snippet de código para Definir uma propriedade](media/code-snippets-vb-property.png)

O código a seguir é inserido:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Se você alterar `newPropertyValue` para `m_property`, cada instância de `newPropertyValue` será alterada. Se você alterar `String` para `Int` na declaração de propriedade, o valor no método conjunto também mudará para `Int`.

## <a name="see-also"></a>Confira também

- [Passo a passo: Criando um trecho de código](../ide/walkthrough-creating-a-code-snippet.md)
- [Como distribuir snippets de código](../ide/how-to-distribute-code-snippets.md)
- [Melhores práticas para o uso de trechos de código](../ide/best-practices-for-using-code-snippets.md)
- [Snippets de solução de problemas](../ide/troubleshooting-snippets.md)
- [C# trechos de código](../ide/visual-csharp-code-snippets.md)
- [Trechos de código C++](../ide/visual-cpp-code-snippets.md)
- [Referência de esquema dos snippets de código](../ide/code-snippets-schema-reference.md)
- [Snippets de código (Visual Studio para Mac)](/visualstudio/mac/snippets)
