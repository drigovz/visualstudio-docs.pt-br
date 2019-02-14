---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aa23265c2f0d8d006d53faf575e2ea608c071d8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027523"
---
# <a name="addmessage"></a>AddMessage
Adiciona uma mensagem personalizada para o diagnóstico de gráficos *HUD* (Head-Up Display).  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szMessage`  
 A mensagem a ser adicionado ao HUD.  
  
## <a name="remarks"></a>Comentários  
 O HUD do diagnóstico de gráficos é exibida no canto superior esquerdo do aplicativo que está em execução no diagnóstico de gráficos. Ele exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de gráficos e as mensagens que são adicionadas ao chamar essa função.  
  
 Para adicionar uma mensagem para o HUD, você não precisa ser ativamente capturando informações de gráficos — ou seja, uma mensagem pode ser adicionada por meio de uma instância das `VsgDbg` classe, mas o [Init](init.md) função de membro não precisa ser chamado primeiro. As mensagens só são exibidas no HUD, eles não estão registrados no arquivo de log de gráficos.