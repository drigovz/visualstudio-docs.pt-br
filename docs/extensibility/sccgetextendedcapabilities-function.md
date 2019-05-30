---
title: Função SccGetExtendedCapabilities | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa6a067a0b9e8358f503228dbc53e20586b84468
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353662"
---
# <a name="sccgetextendedcapabilities-function"></a>Função SccGetExtendedCapabilities
Essa função retorna a recursos adicionais, compatíveis com o plug-in de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>Parâmetros
 pContext

[in] O ponteiro de contexto de plug-in de controle do código-fonte.

 lSccExCaps

[in] Um sinalizador que especifica uma funcionalidade estendida para o qual testar (consulte a tabela de código de funcionalidade estendida na [sinalizadores de recurso](../extensibility/capability-flags.md) para os possíveis sinalizadores).

 pbSupported

[out] Retorna não zero (`TRUE`) se houver suporte para o recurso especificado; caso contrário, retorna zero (`FALSE`).

## <a name="return-value"></a>Valor retornado
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A operação de recurso get foi concluída com êxito.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Erro desconhecido ou não especificado ocorreu.|

## <a name="remarks"></a>Comentários
 Esse método é chamado por demanda. ou seja, quando um recurso precisa ser testado, esse método é chamado para determinar se que o recurso tem suporte. Sinalizador de apenas um por vez é especificado.

## <a name="see-also"></a>Consulte também
- [Funções de API de plug-in da controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos de erro](../extensibility/error-codes.md)
- [Sinalizadores de recurso](../extensibility/capability-flags.md)