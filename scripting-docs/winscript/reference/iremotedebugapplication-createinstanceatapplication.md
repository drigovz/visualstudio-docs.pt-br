---
title: 'IRemoteDebugApplication:: CreateInstanceAtApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 285e5df6960e3188ffe1ce17b1fc4f43626a3d74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572316"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
Permite a criação de objetos no processo do aplicativo por código que está fora do processo para o aplicativo.  
  
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
 no Identificador de classe (CLSID) do objeto a ser criado.  
  
 `pUnkOuter`  
 no Se `NULL`, o objeto não será criado como parte de uma agregação. Caso contrário, `pUnkOuter` é um ponteiro para a interface de `IUnknown` do objeto de agregação (o `IUnknown` de controle).  
  
 `dwClsContext`  
 no Contexto para execução do código executável. Os valores são obtidos do `CLSCTX` de enumeração.  
  
 `riid`  
 no O identificador de interface usado para se comunicar com o objeto.  
  
 `ppvObject`  
 fora Endereço da variável de ponteiro que recebe o ponteiro de interface solicitado em `riid`. Após o retorno bem-sucedido, * `ppvObject` conterá o ponteiro de interface solicitado. Após a falha, \* `ppvObject` contém `NULL`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método delega para `CoCreateInstance`.  
  
## <a name="see-also"></a>Consulte também  
 [IRemoteDebugApplication Interface](../../winscript/reference/iremotedebugapplication-interface.md)