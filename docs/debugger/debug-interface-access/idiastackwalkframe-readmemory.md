---
title: 'Idiastackwalkframe:: Readmemory | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97b1f58f31484084bff502d9ad6a019089ecfec8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992510"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Lê a memória da imagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `type`  
 [in] Um dos [enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) valores de enumeração que especifica o tipo de memória para acessar.  
  
 `va`  
 [in] Local de endereço virtual de imagem será iniciada a leitura.  
  
 `cbData`  
 [in] Tamanho do buffer de dados, em bytes.  
  
 `pcbData`  
 [out] Retorna o número de bytes retornados. Se `data` está `NULL`, em seguida, `pcbData` contém o número total de bytes de dados disponíveis.  
  
 `data`  
 [out] Um buffer que deve ser preenchido com dados do local especificado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)