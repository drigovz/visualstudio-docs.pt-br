---
title: AddMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f01d4e80c3740ae27b5df8badbc74989c2da2c60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156522"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Adiciona uma mensagem personalizada ao *HUD* de diagnóstico de gráficos (exibição de cabeçalho).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szMessage`  
 A mensagem a ser adicionada ao HUD.  
  
## <a name="remarks"></a>Comentários  
 O HUD de diagnóstico de gráficos é exibido no canto superior esquerdo do aplicativo que está sendo executado em diagnóstico de gráficos. Ele exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de gráficos e mensagens que são adicionadas chamando essa função.  
  
 Para adicionar uma mensagem ao HUD, você não precisa estar ativamente capturando informações gráficas, ou seja, uma mensagem pode ser adicionada por meio de uma instância da `VsgDbg` classe, mas a função de membro [init](../debugger/init.md) não deve ser chamada primeiro. As mensagens são exibidas apenas no HUD, elas não são registradas no arquivo de log de gráficos.
