---
title: IDiaFrameData::get_addressOffset | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_addressOffset method
ms.assetid: b68e2e68-6483-4936-bf97-1b0a13cb75e2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c1d7cb8ccf56ba3caf039f82618cce8df8b6e1dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197543"
---
# <a name="idiaframedataget_addressoffset"></a>IDiaFrameData::get_addressOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera a parte de deslocamento do endereço do código para o quadro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna a parte de deslocamento do endereço do código do quadro.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
