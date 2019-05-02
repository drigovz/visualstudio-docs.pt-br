---
title: Função SccCloseProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0420aa4d7148e6409dd6edab903ffbc3e7644f35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62803019"
---
# <a name="scccloseproject-function"></a>Função SccCloseProject
Essa função fecha um projeto, marca o final de uma determinada sessão.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parâmetros
 pvContext a estrutura de contexto de plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O projeto foi fechado com êxito.|
|SCC_E_PROJNOTOPEN|Nenhum projeto estiver aberto no momento.|
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|
|SCC_E_NONSPECIFICERROR|Falha não específica.|

## <a name="remarks"></a>Comentários
 O [SccOpenProject](../extensibility/sccopenproject-function.md) é sempre chamado antes que essa função. Uma chamada para essa função é seguida por uma chamada para o `SccOpenProject` função ou o [SccUninitialize](../extensibility/sccuninitialize-function.md), que termina a conexão para o sistema de controle do código-fonte completamente.

## <a name="see-also"></a>Consulte também
- [Funções de API de plug-in da controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)