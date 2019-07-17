---
title: Snippets de Código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e28ebd46a03983e60ebdd3fc22dd55d85249f710
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188850"
---
# <a name="code-snippets"></a>Snippets de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Snippets de código são pequenos blocos de código reutilizável que podem ser inseridos em um arquivo de código usando um comando de menu de contexto ou uma combinação de teclas de atalho. Eles geralmente contêm blocos de código comumente usados como try-finally ou blocos if-else, mas podem ser usados para inserir métodos ou classes inteiros.  
  
## <a name="expansion-snippets-and-surround-with-snippets"></a>Snippets de expansão e snippets Surround-With  
 Há dois tipos de snippet de código no Visual Studio: snippets de expansão, que são adicionados a um ponto de inserção especificado e podem substituir um atalho de snippet; e snippets Surround-with (somente C# e C++), que são adicionados ao redor de um bloco de código selecionado.  
  
 Um exemplo de um snippet de inserção: em C#, o atalho tryf é usado para inserir um bloco try-finally:  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 Você pode inserir esse snippet clicando em **Inserir Snippet** no menu de contexto da janela de código, então **Visual C#** , então digite `tryf` e, em seguida, TAB; ou você pode digitar `tryf` e pressionar TAB + TAB.  
  
 Um exemplo de um snippet “envolver com”: em C++, o atalho `if` pode ser usado como um snippet de inserção ou um snippet “envolver com”. Se você selecionar uma linha de código (por exemplo, `return FALSE;`) e, em seguida, clicar em **Envolver com** e então em **se**, o snippet de código será expandido ao redor da linha:  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## <a name="snippet-replacement-parameters"></a>Parâmetros de substituição de snippet  
 Snippets podem conter parâmetros de substituição, que são espaços reservados que você deve substituir de acordo com o código exato que você está escrevendo. No exemplo anterior, `true` é um parâmetro de substituição, que você poderia substituir pela condição apropriada. A substituição feita é repetida para cada instância do mesmo parâmetro de substituição no snippet.  
  
 Por exemplo, no Visual Basic, há um snippet de código que insere uma propriedade. Clique em **Inserir Snippet** no menu de contexto da janela de código, então em **Padrões de Código**, **Propriedades, Procedimentos, Eventos** e, em seguida, escolha Definir uma propriedade. O código a seguir é inserido:  
  
```  
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
  
## <a name="code-snippet-manager"></a>Gerenciador de snippet de código  
 Você pode ver todos os snippets de código que estão instalados no momento, além de sua localização no disco, clicando em **Ferramentas/Gerenciador de Snippets de Código**. Snippets são exibidos por idioma.  
  
 Você pode adicionar e remover diretórios de snippet com os botões **Adicionar** e **Remover** na caixa de diálogo **Gerenciador de Snippets de Código**. Para adicionar snippets de código individuais, use o botão **Importar**.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Criando um trecho de código](../ide/walkthrough-creating-a-code-snippet.md)   
 [Como: Distribuir trechos de código](../ide/how-to-distribute-code-snippets.md)   
 [Melhores práticas para usar snippets de código](../ide/best-practices-for-using-code-snippets.md)   
 [Solução de problemas de snippets](../ide/troubleshooting-snippets.md)   
 [Snippets de código do Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Snippets de código do Visual C++](../ide/visual-cpp-code-snippets.md)   
 [Referência de esquema dos snippets de código](../ide/code-snippets-schema-reference.md)
