---
title: IDiaAddressMap::put_addressMapEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198679"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica se o mapa de endereço deve ser usado para converter endereços de símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 NewVal  
 no Defina como `TRUE` para habilitar a tradução de símbolos ou `FALSE` para desabilitar.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Os pós-processadores executáveis às vezes atualizam o executável. DIA contém um mecanismo para dar suporte à tradução de símbolos para o novo layout.  
  
 Quando um arquivo PDB é carregado, o mapa de endereços armazenado no arquivo é habilitado. No entanto, há ocasiões em que um aplicativo cliente pode precisar fornecer seu próprio mapa de endereços chamando o método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Se o `set_addressMap` método for bem-sucedido, o aplicativo cliente deverá chamar o `put_addressMapEnabled` método com um `NewVal` parâmetro de `TRUE` para habilitar o uso desse mapa de endereço.  
  
 O estado atual do mapa de endereços que está sendo habilitado pode ser recuperado com uma chamada para o método [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
