---
title: Remover refatoração de parâmetrosC#() | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667489"
---
# <a name="remove-parameters-refactoring-c"></a>Refatoração Remover Parâmetros (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` é uma operação de refatoração que fornece uma maneira fácil de remover parâmetros de métodos, indexadores ou delegados. Remover parâmetros altera a declaração; em qualquer local onde o membro é chamado, o parâmetro é removido para refletir a nova declaração.

 Você executa a operação remover parâmetros, posicionando primeiro o cursor em um método, indexador ou delegado. Enquanto o cursor estiver na posição, para invocar a operação remover `Parameters`, clique no menu **refatorar** , pressione o atalho do teclado ou selecione o comando no menu de atalho.

> [!NOTE]
> Não é possível remover o primeiro parâmetro em um método de extensão.

### <a name="to-remove-parameters"></a>Para remover parâmetros

1. Crie um aplicativo de console chamado `RemoveParameters` e, em seguida, substitua `Program` pelo código a seguir.

    ```csharp
    class A
    {
        // Invoke on 'A'.
        public A(string s, int i) { }
    }

    class B
    {
        void C()
        {
            // Invoke on 'A'.
            A a = new A("a", 2);
        }
    }
    ```

2. Coloque o cursor no método `A`, na declaração do método ou na chamada do método.

3. No menu **refatorar** , selecione **Remover parâmetros** para exibir a caixa de diálogo **Remover parâmetros** .

     Você também pode digitar o atalho de teclado CTRL + R, V para exibir a caixa de diálogo **Remover parâmetros** .

     Você também pode clicar com o botão direito do mouse no cursor, apontar para **refatorar**e, em seguida, clicar em **Remover parâmetros** para exibir a caixa de diálogo **Remover parâmetros** .

4. Usando o campo **parâmetros** , posicione o cursor em `int i` e, em seguida, clique em **remover**.

5. Clique em **OK**.

6. Na caixa de diálogo **Visualizar alterações – remover parâmetros** , clique em **aplicar**.

## <a name="remarks"></a>Comentários
 Você pode remover parâmetros de uma declaração de método ou uma chamada de método. Posicione o cursor na declaração do método ou no nome do delegado e invoque os parâmetros de remoção.

> [!CAUTION]
> Remover parâmetros permite remover um parâmetro que é referenciado no corpo do membro, mas não remove as referências a esse parâmetro no corpo do método. Isso pode introduzir erros de compilação em seu código. No entanto, você pode usar a caixa de diálogo **Visualizar alterações** para examinar seu código antes de executar a operação de refatoração.

 Se um parâmetro que está sendo removido for modificado durante a chamada para um método, a remoção do parâmetro também removerá a modificação. Por exemplo, se uma chamada de método for alterada de

```csharp
MyMethod(param1++, param2);
```

 para

```csharp
MyMethod(param2);
```

 pela operação de refatoração, `param1` não será incrementada.

## <a name="see-also"></a>Consulte também
 [Refatoração (C#)](../csharp-ide/refactoring-csharp.md)