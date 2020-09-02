---
title: ToggleHUD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144572"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alterna entre ativar ou desativar a sobreposição de *HUD* de diagnóstico de gráficos (exibição de cabeçalho).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Comentários  
 O HUD de diagnóstico de gráficos é exibido no canto superior esquerdo do aplicativo que está sendo executado em diagnóstico de gráficos. Ele exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de gráficos e mensagens que são adicionadas chamando a função de membro [AddMessage](../debugger/addmessage.md) .  
  
 Para alternar o HUD, você não precisa estar ativamente capturando informações gráficas, ou seja, ela pode ser alternada por meio de uma instância da `VsgDbg` classe, mas a função de membro [init](../debugger/init.md) não precisa ser chamada primeiro.
