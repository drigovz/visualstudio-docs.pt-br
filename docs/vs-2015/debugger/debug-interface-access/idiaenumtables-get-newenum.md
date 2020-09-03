---
title: IDiaEnumTables::get__NewEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get__NewEnum method
ms.assetid: 7b1159c7-a5f0-4baa-861a-dc11437d8b93
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 04450a5c4be636c29a645cda0523cc910ab8b80f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202595"
---
# <a name="idiaenumtablesget__newenum"></a>IDiaEnumTables::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera a <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versão deste enumerador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna a `IUnknown` interface que representa a <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> versão deste enumerador.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
