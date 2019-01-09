---
title: Converter um método Get em uma propriedade e converter uma propriedade em um método Get
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
ms.devlang: csharp
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0af901ed6a51b962b7b2999b04909136bbb0f3e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861141"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Refatorações para converter o método Get em propriedade/converter uma propriedade no método Get

Essas refatorações aplicam-se a:

- C#

## <a name="convert-get-method-to-property"></a>Converter o método Get em propriedade

**O quê:** Permite converter um método Get em uma propriedade (e, opcionalmente, no método Set).

**Quando:** Você tem um método Get que não contêm nenhuma lógica.

### <a name="how-to"></a>Como fazer

1. coloque o cursor no nome do seu método Get.

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Substituir método por propriedade** no pop-up da janela Visualização.
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

**O quê:** Permite converter uma propriedade em um método Get

**Quando:** Você tem uma propriedade que envolve mais do que imediatamente configurar e obter um valor

### <a name="how-to"></a>Como fazer

1. coloque o cursor no nome do seu método Get.

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Substituir propriedade por métodos** no pop-up da janela Visualização.
   - **Mouse**
      - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Substituir propriedade por métodos** no pop-up da janela Visualização.

1. Se você estiver satisfeito com a alteração na visualização do código, pressione **Enter** ou clique na correção no menu e as alterações serão confirmadas.

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)