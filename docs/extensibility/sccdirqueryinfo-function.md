---
title: Função SccDirQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700945"
---
# <a name="sccdirqueryinfo-function"></a>Função SccDirQueryInfo
Esta função examina uma lista de diretórios totalmente qualificados para o seu status atual.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>parâmetros
 pContext

[em] A estrutura de contexto plug-in de controle de origem.

 nDirs

[em] O número de diretórios selecionados para serem consultados.

 lpDirNames

[em] Uma série de caminhos totalmente qualificados dos diretórios a serem consultados.

 lpStatus

[dentro, fora] Uma estrutura de array para o plug-in de controle de origem para retornar os sinalizadores de status (consulte [código de status do diretório](../extensibility/directory-status-code-enumerator.md) para detalhes).

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A consulta foi bem sucedida.|
|SCC_E_OPNOTSUPPORTED|O sistema de controle de código fonte não suporta esta operação.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 A função preenche a matriz de retorno com `SCC_DIRSTATUS` uma máscara de bits da família (veja [código de status do Diretório),](../extensibility/directory-status-code-enumerator.md)uma entrada para cada diretório dado. A matriz de status é alocada pelo chamador.

 O IDE usa essa função antes que um diretório seja renomeado para verificar se o diretório está sob controle de origem, consultando se ele tem um projeto correspondente. Se o diretório não estiver sob controle de origem, o IDE pode fornecer o aviso adequado ao usuário.

> [!NOTE]
> Se um plug-in de controle de origem optar por não implementar um ou mais dos valores de status, os bits não implementados devem ser definidos como zero.

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [Código de status do diretório](../extensibility/directory-status-code-enumerator.md)
