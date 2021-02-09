---
title: Converter entre propriedade automática e completa
description: Saiba como usar o menu ações rápidas e refatoração para converter entre uma propriedade implementada automaticamente e uma propriedade completa.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 3680444c07658da8e77b6058f5a71b9dcf119193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907602"
---
# <a name="convert-between-auto-property-and-full-property"></a>Converter entre propriedade automática e completa

Esta refatoração aplica-se a:

- C#

**O que:** Converta entre uma propriedade implementada automaticamente em uma propriedade completa.

**Quando:** A lógica da propriedade foi alterada.

**Por que:** Você pode converter entre uma propriedade implementada automaticamente em uma propriedade completa manualmente, no entanto, esse recurso fará o trabalho automaticamente para você. 

## <a name="how-to"></a>Como fazer

1. Coloque o cursor sobre o nome da propriedade.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione uma das duas opções a seguir: 

    Selecione **converter para Propriedade completa**.

   ![Converter a propriedade automática em propriedade completa](media/convert-auto-property-to-full-property.png) 

    Selecione **usar Propriedade automática**. 

    ![Converter Propriedade completa em Propriedade automática](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
