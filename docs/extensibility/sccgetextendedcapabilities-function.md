---
title: Função SccGetExtendedCapabilities | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700731"
---
# <a name="sccgetextendedcapabilities-function"></a>Função SccGetExtendedCapabilities
Esta função retorna recursos adicionais suportados pelo plug-in de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccGetExtendedCapabilities(
   LPVOID pContext,
   LONG lSccExCaps,
   LPBOOL pbSupported
);
```

### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 lSccExCaps

[em] Um sinalizador especificando um recurso estendido para o qual testar (consulte a tabela Código de capacidade estendida em [sinalizadores de capacidade](../extensibility/capability-flags.md) para os possíveis sinalizadores).

 pbSuportado

[fora] Retorna não-zero`TRUE`( ) se o recurso especificado for suportado; caso contrário, retorna`FALSE`zero ( ).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A operação de capacidade get concluída com sucesso.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Ocorreu erro desconhecido ou não especificado.|

## <a name="remarks"></a>Comentários
 Este método é chamado sob demanda; ou seja, quando uma capacidade precisa ser testada, esse método é chamado para determinar se esse recurso é suportado. Apenas uma bandeira de cada vez é especificada.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos do Erro](../extensibility/error-codes.md)
- [Bandeiras de capacidade](../extensibility/capability-flags.md)
