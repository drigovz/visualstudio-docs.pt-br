---
title: Função SccBackgroundGet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701237"
---
# <a name="sccbackgroundget-function"></a>Função SccBackgroundGet
Essa função recupera do controle do código-fonte cada um dos arquivos especificados sem interação do usuário.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parâmetros
 pContext

no O ponteiro de contexto do plug-in de controle do código-fonte.

 nFiles

no Número de arquivos especificados na `lpFileNames` matriz.

 lpFileNames

[entrada, saída] Matriz de nomes de arquivos a serem recuperados.

> [!NOTE]
> Os nomes devem ser nomes de filelocais totalmente qualificados.

 dwFlags

no Sinalizadores de comando ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).

 dwBackgroundOperationID

no Um valor exclusivo associado a esta operação.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Operação concluída com sucesso.|
|SCC_E_BACKGROUNDGETINPROGRESS|Uma recuperação em segundo plano já está em andamento (o plug-in de controle do código-fonte deve retornar somente se não oferecer suporte a operações simultâneas em lote).|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes de ser concluída.|

## <a name="remarks"></a>Comentários
 Essa função é sempre chamada em um thread diferente daquele que carregou o plug-in de controle do código-fonte. Essa função não deve retornar até que seja concluída; no entanto, ele pode ser chamado várias vezes com várias listas de arquivos, tudo ao mesmo tempo.

 O uso do `dwFlags` argumento é o mesmo que o [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Confira também
- [Funções da API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
