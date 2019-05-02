---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848468"
---
# <a name="togglehud"></a>ToggleHUD
Alterna o diagnóstico de gráficos *HUD* de sobreposição (Head-Up Display) ativada ou desativada.

## <a name="syntax"></a>Sintaxe

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Comentários
 O HUD do diagnóstico de gráficos é exibida no canto superior esquerdo do aplicativo que está em execução no diagnóstico de gráficos. Ele exibe informações de tempo de execução sobre o aplicativo e captura de informações de gráficos e as mensagens que são adicionadas por meio da chamada a [AddMessage](addmessage.md) função de membro.

 Para ativar ou desativar o HUD, você não precisa ser ativamente capturando informações de gráficos — ou seja, ele pode ser alternado por meio de uma instância das `VsgDbg` classe, mas o [Init](init.md) função de membro não precisa ser chamado primeiro.