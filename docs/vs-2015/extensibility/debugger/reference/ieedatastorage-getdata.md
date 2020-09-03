---
title: 'IEEDataStorage:: GetData | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a58f644a71601b16317c4fe63271f4f816da77d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149295"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera o número especificado de bytes do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dataSize`  
 no O número de bytes a serem recuperados (a `data` matriz deve conter pelo menos esse número de bytes).  
  
 `sizeGotten`  
 fora Retorna o número de bytes realmente recuperados.  
  
 `data`  
 [entrada, saída] Matriz a ser preenchida com os dados solicitados.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O uso recomendado desse método é recuperar todos os bytes de dados em uma matriz local, já que não há nenhuma maneira de ignorar os bytes no processo de recuperação. Nesse caso, o parâmetro `dataSize` deve ser o valor retornado pelo método [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
