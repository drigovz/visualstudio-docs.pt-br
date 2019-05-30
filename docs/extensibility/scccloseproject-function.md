---
title: Função SccCloseProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a5fe721a3b51f4d3f210e7f2d5450e4f4bc6f41
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333931"
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