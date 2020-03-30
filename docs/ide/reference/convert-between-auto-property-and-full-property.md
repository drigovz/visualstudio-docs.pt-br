---
title: Converter entre propriedade automática e propriedade completa
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395408"
---
# <a name="convert-between-auto-property-and-full-property"></a>Converter entre propriedade automática e propriedade completa

Esta refatoração aplica-se a:

- C#

**O que é isso?** Converta entre uma propriedade auto-implementada em uma propriedade completa.

**Quando:** A lógica da propriedade mudou.

**Por que:** Você pode converter entre uma propriedade implementada automaticamente para uma propriedade completa manualmente, no entanto, esse recurso fará o trabalho automaticamente para você. 

## <a name="how-to"></a>Como fazer

1. Coloque seu cursor no nome da propriedade.
2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione entre as duas opções a seguir: 

    Selecione **Converter para propriedade completa**.

   ![Converter a propriedade automática em propriedade completa](media/convert-auto-property-to-full-property.png) 

    Selecione **Usar propriedade automática**. 

    ![Converter propriedade completa em propriedade automática](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
