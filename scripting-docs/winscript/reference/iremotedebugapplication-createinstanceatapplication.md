---
title: IRemoteDebugApplication::CreateInstanceAtApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29cbcebc5bdc51be4223b2592bbe6ac3ae76525d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086353"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Permite a criação de objetos no processo do aplicativo pelo código que é out-of-process para o aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rclsid`  
 [in] Classe CLSID (identificador) do objeto a ser criado.  
  
 `pUnkOuter`  
 [in] Se `NULL`, o objeto não está sendo criado como parte de uma agregação. Caso contrário, `pUnkOuter` é um ponteiro para o objeto agregado `IUnknown` interface (o controlando `IUnknown`).  
  
 `dwClsContext`  
 [in] Contexto de execução do código executável. Os valores são obtidos da enumeração `CLSCTX`.  
  
 `riid`  
 [in] O identificador de interface usado para se comunicar com o objeto.  
  
 `ppvObject`  
 [out] Endereço da variável de ponteiro que recebe o ponteiro de interface solicitado no `riid`. No retorno bem-sucedido, *`ppvObject` contém o ponteiro de interface solicitado. Em caso de falha, \* `ppvObject` contém `NULL`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Este método delega ao `CoCreateInstance`.  
  
## <a name="see-also"></a>Consulte também  
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)