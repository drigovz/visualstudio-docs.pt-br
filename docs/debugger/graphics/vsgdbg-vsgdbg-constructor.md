---
title: 'Vsgdbg:: Vsgdbg (construtor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e282e63b81ecee4023934a235d4f524f8372311e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945568"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Construtor)
Constrói uma instância do `VsgDbg` classe com ou sem Preparando o componente no aplicativo de diagnóstico de gráficos para capturar ativamente e gravar informações de gráficos por padrão, com base no parâmetro booliano especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
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
 [VsgDbg::~VsgDbg (Destruidor)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)