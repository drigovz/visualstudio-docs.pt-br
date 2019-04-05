---
title: 'Vsgdbg:: Vsgdbg (construtor) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924255"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Construtor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Constrói uma instância do `VsgDbg` classe com ou sem Preparando o componente no aplicativo de diagnóstico de gráficos para capturar ativamente e gravar informações de gráficos por padrão, com base no parâmetro booliano especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bDefaultInit`  
 `true` para especificar que o componente no aplicativo de diagnóstico de gráficos é estar preparado para capturar ativamente e registrar informações de gráficos; `false` para especificar que o aplicativo não deve estar preparado para capturar e registrar informações de gráficos no momento ativamente.  
  
## <a name="remarks"></a>Comentários  
 Quando o construtor é chamado com `bDefaultInit` definido como `true`, o nome do arquivo do arquivo de log de gráficos é determinado por como o `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME` símbolos de pré-processamento são definidos antes de `vsgcapture.h` está incluído no seu aplicativo.  
  
 Quando o construtor é chamado com `bDefaultInit` definido como `false`, o componente no aplicativo de diagnóstico de gráficos pode estar preparado para capturar ativamente e registrar informações de gráficos em um momento posterior chamando o `Init` função.  
  
## <a name="see-also"></a>Consulte também  
 [VsgDbg::~VsgDbg (Destruidor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
