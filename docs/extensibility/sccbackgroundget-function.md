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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701237"
---
# <a name="sccbackgroundget-function"></a>Função SccBackgroundGet
Esta função recupera do controle de origem cada um dos arquivos especificados sem interação do usuário.

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

### <a name="parameters"></a>parâmetros
 pContext

[em] O ponteiro de contexto plug-in de controle de origem.

 nArquivos

[em] Número de arquivos especificados na `lpFileNames` matriz.

 lpFileNames

[dentro, fora] Matriz de nomes de arquivos a serem recuperados.

> [!NOTE]
> Os nomes devem ser nomes de arquivos locais totalmente qualificados.

 dwFlags

[em] Bandeiras`SCC_GET_ALL`de `SCC_GET_RECURSIVE`comando ( , ).

 dwBackgroundOperationID

[em] Um valor único associado a esta operação.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Operação concluída com sucesso.|
|SCC_E_BACKGROUNDGETINPROGRESS|Uma recuperação de fundo já está em andamento (o plug-in de controle de origem deve retornar isso somente se não suportar operações simultâneas em lote).|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes de ser concluída.|

## <a name="remarks"></a>Comentários
 Esta função é sempre chamada em um segmento diferente daquele que carregou o plug-in de controle de origem. Esta função não é esperada para retornar até que seja feita; no entanto, ele pode ser chamado várias vezes com várias listas de arquivos, tudo ao mesmo tempo.

 O uso `dwFlags` do argumento é o mesmo que o [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
