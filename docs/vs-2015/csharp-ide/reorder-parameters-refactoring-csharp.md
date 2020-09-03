---
title: Reordenação de parâmetros de refatoração (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e39564fb108b63859620e2c4a650608cdf1e7e82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673139"
---
# <a name="reorder-parameters-refactoring-c"></a>Refatoração Reordenar Parâmetros (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Reorder Parameters` é uma operação de refatoração do Visual C# que fornece uma maneira fácil de alterar a ordem dos parâmetros para métodos, indexadores e delegados. `Reorder Parameters` altera a declaração e em qualquer local em que o membro é chamado, os parâmetros são reorganizados para refletir o novo pedido.

 Para executar a `Reorder Parameters` operação, coloque o cursor sobre ou ao lado de um método, indexador ou delegado. Quando o cursor estiver na posição, invoque a `Reorder Parameters` operação pressionando o atalho de teclado ou clicando no comando no menu de atalho.

> [!NOTE]
> Não é possível reordenar o primeiro parâmetro em um método de extensão.

### <a name="to-reorder-parameters"></a>Para reordenar parâmetros

1. Crie uma biblioteca de classes chamada `ReorderParameters` e, em seguida, substitua `Class1` pelo código de exemplo a seguir.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. Coloque o cursor sobre `MethodB` , na declaração do método ou na chamada do método.

3. No menu **refatorar** , clique em **Reordenar parâmetros**.

     A caixa de diálogo **Reordenar parâmetros** é exibida.

4. Na caixa de diálogo **Reordenar parâmetros** , selecione `int i` na lista **parâmetros** e, em seguida, clique no botão para baixo.

     Como alternativa, você pode arrastar `int i` depois `bool b` na lista de **parâmetros** .

5. Na caixa de diálogo **Reordenar parâmetros** , clique em **OK**.

     Se a opção **Visualizar alterações de referência** for selecionada na caixa de diálogo **Reordenar parâmetros** , a caixa de diálogo **Visualizar alterações – reordenar parâmetros** será exibida. Ele fornece uma visualização das alterações na lista de parâmetros para `MethodB` tanto na assinatura quanto na chamada do método.

    1. Se a caixa de diálogo **Visualizar alterações – reordenar parâmetros** for exibida, clique em **aplicar**.

         Neste exemplo, a declaração de método e todos os sites de chamada de método para `MethodB` são atualizados.

## <a name="remarks"></a>Comentários
 Você pode reordenar os parâmetros de uma declaração de método ou de uma chamada de método. Posicione o cursor sobre ou ao lado do método ou da declaração de delegado, mas não no corpo.

## <a name="see-also"></a>Consulte Também
 [Refatoração (C#)](../csharp-ide/refactoring-csharp.md)