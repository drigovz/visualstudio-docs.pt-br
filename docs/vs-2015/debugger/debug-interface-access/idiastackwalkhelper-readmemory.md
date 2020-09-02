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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150068"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lê um bloco de dados da imagem do executável na memória.  
  
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
 no Um valor da enumeração de [Enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) especificando o tipo de memória a ser lido.  
  
 va  
 no Endereço virtual na imagem a partir da qual começar a ler.  
  
 `cbData`  
 no O tamanho do buffer de dados em bytes.  
  
 `pcbData`  
 fora Retorna o número de bytes realmente lidos. Se `pbData` for `NULL` , este é o número total de bytes de dados disponíveis.  
  
 `pbData`  
 [entrada, saída] Um buffer que é preenchido com a leitura de memória.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)
