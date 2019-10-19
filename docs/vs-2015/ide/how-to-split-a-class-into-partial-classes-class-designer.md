---
title: Como dividir uma classe em classes parciais (Designer de Classe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e93ebc58e4e9b6092921e4155fe3d821bb552c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670710"
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Como dividir uma classe em classes parciais (Designer de Classe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode dividir a declaração de uma classe ou estrutura entre várias declarações usando a palavra-chave `Partial` no Visual Basic ou a palavra-chave `partial` no Visual C#. É possível usar quantas declarações parciais você desejar, em quantos arquivos de origem diferentes desejar ou em um único arquivo de origem. No entanto, todas as declarações devem estar no mesmo assembly e no mesmo namespace.

 Classes parciais são úteis em várias situações. Por exemplo, quando você estiver trabalhando em projetos grandes, separar uma classe em mais de um arquivo permite que mais de um programador trabalhe ao mesmo tempo. Quando estiver trabalhando com código gerado pelo Visual Studio, você pode alterar a classe sem precisar recriar o arquivo de origem. (Exemplos de códigos gerados pelo Visual Studio incluem código de wrapper do serviço Web e do Windows Forms). Portanto, você pode criar um código que usa classes geradas automaticamente sem precisar modificar o arquivo que o Visual Studio cria.

 Existem dois tipos de métodos parciais. No Visual C#, eles são chamados de declarar e implementar. No Visual Basic, são chamados de declaração e implementação.

 O Designer de Classe dá suporte a métodos e classes parciais. A forma de tipo no diagrama de classe se refere a um único local de declaração para a classe parcial. Se a classe parcial for definida em vários arquivos, você pode especificar qual local de declaração o Designer de Classe usará definindo a propriedade **Localização de Novo Membro** na janela **Propriedades**. Ou seja, quando você clica duas vezes em uma forma de classe, o Designer de Classe vai até o arquivo de origem que contém a declaração de classe identificada pela propriedade **Localização de Novo Membro**. Quando você clica duas vezes em um método parcial em uma forma de classe, o Designer de Classe vai para a declaração de método parcial. Além disso, na janela **Propriedades**, a propriedade **Nome de Arquivo** aponta para o local da declaração. Para classes parciais, **Nome de Arquivo** lista todos os arquivos que contêm código de implementação e declaração dessa classe. No entanto, para métodos parciais, **Nome de Arquivo** lista apenas o arquivo que contém a declaração de método parcial.

 Os exemplos a seguir dividem a definição da classe `Employee` em duas declarações, cada uma das quais define um procedimento diferente. As duas definições parciais nos exemplos podem estar em um arquivo de origem ou em dois arquivos de origem diferentes.

> [!NOTE]
> O Visual Basic usa definições de classe parcial para separar o código gerado pelo Visual Studio do código de autoria do usuário. O código é separado em arquivos de origem distintos. Por exemplo, o **Windows Form Designer** define classes parciais para controles, como `Form`. Você não deve modificar o código gerado nesses controles.

 Para obter mais informações sobre tipos parciais no Visual Basic, consulte [Parcial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448).

## <a name="example"></a>Exemplo
 Para dividir uma definição de classe no Visual Basic, use a palavra-chave `Partial`, conforme mostrado no exemplo a seguir.

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="example"></a>Exemplo
 Para dividir uma definição de classe no Visual C#, use a palavra-chave `partial`, conforme mostrado no exemplo a seguir.

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

## <a name="see-also"></a>Veja também
 [Classes parciais e métodos](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1) [parciais (tipo)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334) [parciais (C# método) (referência)](https://msdn.microsoft.com/library/43f40242-17e0-4452-8573-090503ad3137) [parciais](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)
