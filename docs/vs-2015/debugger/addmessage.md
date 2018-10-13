---
title: AddMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b60f8bac24b01e39327357b89e9e96c04765077
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248996"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Adiciona uma mensagem personalizada para o diagnóstico de gráficos *HUD* (Head-Up Display).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szMessage`  
 A mensagem a ser adicionado ao HUD.  
  
## <a name="remarks"></a>Comentários  
 O HUD do diagnóstico de gráficos é exibida no canto superior esquerdo do aplicativo que está em execução no diagnóstico de gráficos. Ele exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de gráficos e as mensagens que são adicionadas ao chamar essa função.  
  
 Para adicionar uma mensagem para o HUD, você não precisa ser ativamente capturando informações de gráficos — ou seja, uma mensagem pode ser adicionada por meio de uma instância das `VsgDbg` classe, mas o [Init](../debugger/init.md) função de membro não precisa ser chamado primeiro. As mensagens só são exibidas no HUD, eles não estão registrados no arquivo de log de gráficos.



