---
title: UnInit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bec86a7f872057b7a0d652df6346e3a1ef2ff8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197934"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Finaliza o arquivo de log de gráficos, fecha-o e libera os recursos que foram usados enquanto o aplicativo gravava informações gráficas ativamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>Comentários  
 `UnInit` é chamado automaticamente quando uma instância da `VsgDbg` classe é destruída. Se a `VsgDbg` instância não estiver gravando ativamente as informações gráficas, isso não terá efeito.  
  
 Depois de `UnInit` ter sido chamado em uma instância da `VsgDbg` classe, um novo arquivo de log de elementos gráficos pode ser criado chamando `Init` e finalizado chamando `UnInit` . Você pode repetir isso quantas vezes quiser usar a mesma `VsgDbg` instância para criar vários arquivos de log de gráficos independentes.  
  
## <a name="see-also"></a>Consulte Também  
 [Iniciar](../debugger/init.md)
