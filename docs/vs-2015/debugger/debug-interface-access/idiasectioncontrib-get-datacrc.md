---
title: IDiaSectionContrib::get_dataCrc | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_dataCrc method
ms.assetid: 33b7488f-dc9c-47b3-b08c-737e0eb1bf7d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 309ecc0269b911afb1f8e1b753811ac0b1c36e6f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576542"
---
# <a name="idiasectioncontribget_datacrc"></a>IDiaSectionContrib::get_dataCrc
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera a CRC (verificação de redundância cíclica) dos dados na seção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_dataCrc (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna o CRC dos dados na seção.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não há suporte para essa propriedade. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
