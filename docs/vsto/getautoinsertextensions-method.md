---
title: Método GetAutoInsertExtensions
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a12adf6e83e58b877e36dd65d98b617cda3a39b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647204"
---
# <a name="getautoinsertextensions-method"></a>Método GetAutoInsertExtensions
  Obtém informações sobre os aplicativos do Office que serão inseridos automaticamente durante a depuração.  
  
 Este método está reservado para uso futuro.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|*psaExtensionNames*|Os nomes de extensão dos aplicativos para Office.|  
  
## <a name="return-value"></a>Valor retornado  
 Um valor HRESULT que indica se o método concluída com êxito.  
  
## <a name="remarks"></a>Comentários  
 Cada aplicativo do Office a ser inserido é retornado como um nome de extensão de aplicativo do Office, que corresponde a um valor em **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. O host deve pesquisar esses valores no registro e, em seguida, inserir automaticamente as extensões.  
  
  