---
title: 'VsgDbg:: VsgDbg (Construtor) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157436"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Construtor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Constrói uma instância da `VsgDbg` classe com ou sem preparar o componente no aplicativo de diagnóstico de gráficos para capturar e gravar ativamente informações de gráficos por padrão, com base no parâmetro booliano especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bDefaultInit`  
 `true` para especificar que o componente no aplicativo do diagnóstico de gráficos seja preparado para capturar e registrar informações de gráficos ativamente; `false` para especificar que o aplicativo não deve estar preparado para capturar e registrar informações de gráficos ativamente neste momento.  
  
## <a name="remarks"></a>Comentários  
 Quando o construtor é chamado com `bDefaultInit` definido como `true` , o nome de arquivo do arquivo de log de gráficos é determinado pelo modo como os `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` símbolos de pré-processador e são definidos antes de `vsgcapture.h` serem incluídos em seu aplicativo.  
  
 Quando o construtor é chamado com `bDefaultInit` definido como `false` , o componente no aplicativo do diagnóstico de gráficos pode ser preparado para capturar e gravar ativamente informações de gráficos em um momento posterior chamando a `Init` função.  
  
## <a name="see-also"></a>Consulte Também  
 [VsgDbg:: ~ VsgDbg (destruidor)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Iniciar](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
