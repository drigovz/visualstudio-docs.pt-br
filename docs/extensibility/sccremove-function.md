---
title: Função SccRemove | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17889d50dbdcf68dd4cca161d6703b8b6d69ad47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700450"
---
# <a name="sccremove-function"></a>Função SccRemove
Esta função exclui arquivos do sistema de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 nArquivos

[em] Número de arquivos especificados na `lpFileNames` matriz.

 lpFileNames

[em] Matriz de nomes de caminhos locais totalmente qualificados de arquivos a serem removidos.

 lpComment

[em] O comentário a ser aplicado a cada arquivo a ser removido.

 fOpções

[em] Bandeiras de comando (não utilizadas).

 pvOpções

[em] Opções específicas de plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A remoção foi bem sucedida.|
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle de origem.|
|SCC_E_OPNOTSUPPORTED|O sistema de controle de origem não suporta esta operação.|
|SCC_E_ISCHECKEDOUT|Não é possível remover um arquivo porque um usuário atualmente o tem verificado.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_NONSPECIFICERROR|Falha não específica; arquivo não foi removido.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|

## <a name="remarks"></a>Comentários
 Esta função remove os arquivos do sistema de controle de origem, mas não os exclui do disco rígido local do usuário.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
