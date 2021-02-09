---
title: Método GetAutoInsertExtensions
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 24fd5768a9eafa4a023aeabf21c862ea1a0d1891
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931520"
---
# <a name="getautoinsertextensions-method"></a>Método GetAutoInsertExtensions
  Obtém informações sobre os aplicativos para o Office que devem ser inseridos automaticamente durante a depuração.

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
|*psaExtensionNames*|Os nomes de extensão dos aplicativos para o Office.|

## <a name="return-value"></a>Valor retornado
 Um valor HRESULT que indica se o método foi concluído com êxito.

## <a name="remarks"></a>Comentários
 Cada aplicativo para o Office a ser inserido é retornado como um nome de extensão de aplicativo do Office, que corresponde a um valor em **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. O host deve procurar esses valores no registro e, em seguida, inserir as extensões automaticamente.
