---
title: Converter o método Get em ou de uma propriedade
description: Saiba como usar o menu ações rápidas e refatoração para converter um método Get (e, opcionalmente, o método Set) em uma propriedade.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3aa7831c56068c826c9bbecf97d7115331243251
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039817"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Refatorações para converter o método Get em propriedade/converter uma propriedade no método Get

Essas refatorações aplicam-se a:

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Converter o método Get em propriedade

**O quê:** permite converter um método Get em uma propriedade (e opcionalmente seu método Set).

**Quando:** você tem um método Get que não contêm nenhuma lógica.

### <a name="how-to"></a>Como fazer

1. coloque o cursor no nome do seu método Get.

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Substituir método por propriedade** no pop-up da janela Visualização.
   - **Mouse**
      - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Substituir método por propriedade** no pop-up da janela Visualização.

1. (Opcional) Se houver um método Set, você também poderá convertê-lo neste momento selecionando **Substituir método Get e método Set por propriedade**.

1. Se você estiver satisfeito com a alteração na visualização do código, pressione **Enter** ou clique na correção no menu e as alterações serão confirmadas.

Exemplo:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Converter propriedade em método Get

**O quê:** permite converter uma propriedade em um método Get

**Quando:** você tem uma propriedade que envolve mais do que imediatamente configurar e obter um valor

### <a name="how-to"></a>Como fazer

1. coloque o cursor no nome do seu método Get.

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Substituir propriedade por métodos** no pop-up da janela Visualização.
   - **Mouse**
      - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Substituir propriedade por métodos** no pop-up da janela Visualização.

1. Se você estiver satisfeito com a alteração na visualização do código, pressione **Enter** ou clique na correção no menu e as alterações serão confirmadas.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
