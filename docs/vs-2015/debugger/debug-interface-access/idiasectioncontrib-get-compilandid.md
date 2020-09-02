---
title: IDiaSectionContrib::get_compilandId | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_compilandId method
ms.assetid: 71ef2e63-d095-42b6-88d8-626e3129f0d9
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 80a42cda74c5ca4bd2b5a4552787422b07b32287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576640"
---
# <a name="idiasectioncontribget_compilandid"></a>IDiaSectionContrib::get_compilandId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o identificador de compiland para a seção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_compilandId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna o identificador compiland da seção.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
