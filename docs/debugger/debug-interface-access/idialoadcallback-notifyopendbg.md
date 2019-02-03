---
title: IDiaLoadCallback::NotifyOpenDBG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a00a19e7c193aceafcb6134cb10cb0300162f582
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924607"
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
Chamado quando um arquivo do candidato. dbg foi aberto.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT NotifyOpenDBG (   
   LPCOLESTR dbgPath,  
   HRESULT   resultCode  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dbgPath`  
 [in] O caminho completo do arquivo. dbg.  
  
 `resultCode`  
 [in] Código que indica o êxito (`S_OK`) ou a falha da carga conforme aplicado a esse arquivo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. O código de retorno normalmente é ignorado.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)