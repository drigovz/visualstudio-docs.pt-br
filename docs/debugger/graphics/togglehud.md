---
title: ToggleHUD | Microsoft Docs
description: Use o método ToggleHUD () de VsgDbg para alternar se a exibição de cabeçalho de diagnóstico de gráficos (HUD) é exibida quando o aplicativo é executado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6cde6549551156f3655f313c23dc66659d2830cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905057"
---
# <a name="togglehud"></a>ToggleHUD
Alterna entre ativar ou desativar a sobreposição de *HUD* de diagnóstico de gráficos (exibição de cabeçalho).

## <a name="syntax"></a>Sintaxe

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Comentários
 O HUD de diagnóstico de gráficos é exibido no canto superior esquerdo do aplicativo que está sendo executado em diagnóstico de gráficos. Ele exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de gráficos e mensagens que são adicionadas chamando a função de membro [AddMessage](addmessage.md) .

 Para alternar o HUD, você não precisa estar ativamente capturando informações gráficas, ou seja, ela pode ser alternada por meio de uma instância da `VsgDbg` classe, mas a função de membro [init](init.md) não precisa ser chamada primeiro.