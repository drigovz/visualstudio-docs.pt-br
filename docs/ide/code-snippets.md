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
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 98dadaed75cf16ae6ae35da9d6589355a63bd35c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975225"
---
# <a name="code-snippets"></a>Snippets de código

Snippets de código são pequenos blocos de código reutilizável que podem ser inseridos em um arquivo de código usando um comando do menu do clique com o botão direito (menu de contexto) ou uma combinação de teclas de atalho. Eles geralmente contêm os blocos de código mais usados, como `try-finally` ou `if-else`, mas podem ser usados para inserir métodos ou classes inteiras.

> [!NOTE]
> Este tópico aplica-se ao Visual Studio no Windows. Para o Visual Studio para Mac, confira [Snippet de código (Visual Studio para Mac)](/visualstudio/mac/snippets).

Os snippets de código estão disponíveis para uma variedade de linguagens, incluindo C#, C++, Visual Basic, XML e T-SQL, entre outras. Para exibir todos os snippets instalados disponíveis para uma linguagem, abra o **Gerenciador de Snippets de Código** no menu **Ferramentas** do Visual Studio e escolha a linguagem no menu suspenso na parte superior.

![Caixa de diálogo Gerenciador de Snippets de Código](media/code-snippets-manager.png)

Em geral, os snippets de código podem ser acessados das seguintes maneiras:

- Na barra de menus, escolha **Editar** > **IntelliSense** > **Inserir Snippet**

- No menu de contexto ou clicando com o botão direito do mouse no editor de códigos, escolha **Trecho** > **Inserir Snippet de Código**

- Usando o teclado, pressione **Ctrl**+**K**+**X**

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

Para inserir esse snippet, clique em **Inserir Snippet** no menu do clique com o botão direito (menu de contexto) da janela de código; depois, em **Visual C#** , digite `tryf` e, por fim, pressione **Tab**. Ou, você pode digitar `tryf` e pressionar **Tab** duas vezes.

Um exemplo de um snippet “envolver com”: em C++, o atalho `if` pode ser usado como um snippet de inserção ou um snippet “envolver com”. Se você selecionar uma linha de código (por exemplo `return FALSE;`) e, em seguida, escolher **Envolver Com** > **if**, o snippet de código será expandido na linha:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parâmetros de substituição de snippet

Snippets podem conter parâmetros de substituição, que são espaços reservados que você deve substituir de acordo com o código exato que você está escrevendo. No exemplo anterior, `true` é um parâmetro de substituição, que você poderia substituir pela condição apropriada. A substituição feita é repetida para cada instância do mesmo parâmetro de substituição no snippet.

Por exemplo, no Visual Basic, há um snippet de código que insere uma propriedade. Para inserir o snippet de código, escolha **Trecho** > **Inserir Snippet** no menu de contexto ou clicando com o botão direito do mouse em um arquivo de código do Visual Basic. Em seguida, escolha **Padrões de Código** > **Propriedades, Procedimentos, Eventos** > **Definir uma Propriedade**.

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

## <a name="see-also"></a>Consulte também

- [Passo a passo: Criando um snippet de código](../ide/walkthrough-creating-a-code-snippet.md)
- [Como: Distribuir snippets de código](../ide/how-to-distribute-code-snippets.md)
- [Melhores práticas para usar snippets de código](../ide/best-practices-for-using-code-snippets.md)
- [Solução de problemas de snippets](../ide/troubleshooting-snippets.md)
- [Snippets de código C#](../ide/visual-csharp-code-snippets.md)
- [Snippets de código do Visual C++](../ide/visual-cpp-code-snippets.md)
- [Referência de esquema dos snippets de código](../ide/code-snippets-schema-reference.md)
- [Snippets de código (Visual Studio para Mac)](/visualstudio/mac/snippets)