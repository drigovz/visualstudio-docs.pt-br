---
title: 'VsgDbg:: ~ VsgDbg (destruidor) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200296"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruidor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Destrói uma instância da `VsgDbg` classe. Se as informações gráficas estiverem sendo registradas ativamente, o arquivo de log de gráficos será finalizado e fechado, e os recursos que foram usados durante a captura ativa das informações gráficas serão liberados.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Consulte Também  
 [VsgDbg::VsgDbg (Construtor)](../debugger/vsgdbg-vsgdbg-constructor.md)
