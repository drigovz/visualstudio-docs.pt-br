---
title: IDiaStackWalkHelper::readMemory | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bef01cd29bb2312bd682f2f1f1150ee78da293e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68150068"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lê um bloco de dados de imagem do arquivo executável na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `type`  
 [in] Um valor da [enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) enumeração que especifica o tipo de memória a ser lido.  
  
 va  
 [in] Endereço virtual na imagem a partir do qual será iniciada a leitura.  
  
 `cbData`  
 [in] O tamanho do buffer de dados em bytes.  
  
 `pcbData`  
 [out] Retorna o número de bytes realmente lidos. Se `pbData` é `NULL`, em seguida, isso é o número total de bytes de dados disponíveis.  
  
 `pbData`  
 [no, out] Um buffer que será preenchido com a memória de leitura.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)
