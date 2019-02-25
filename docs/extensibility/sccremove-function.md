---
title: Função SccRemove | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2183a73536e7e4251958680b25a8909ea2bb714e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696422"
---
# <a name="sccremove-function"></a>Função SccRemove
Esta função exclui os arquivos do sistema de controle de origem.

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

#### <a name="parameters"></a>Parâmetros
 pvContext

[in] A estrutura de contexto de plug-in de controle de origem.

 hWnd

[in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.

 nFiles

[in] Número de arquivos especificados no `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nomes de caminho local totalmente qualificado dos arquivos a serem removidos.

 lpComment

[in] O comentário a ser aplicado a cada arquivo que está sendo removido.

 fOptions

[in] Sinalizadores de comando (não usados).

 pvOptions

[in] Opções de plug-in específico de controle de origem.

## <a name="return-value"></a>Valor de retorno
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Remoção foi bem-sucedida.|
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle do código-fonte.|
|SCC_E_OPNOTSUPPORTED|O sistema de controle do código-fonte não suporta esta operação.|
|SCC_E_ISCHECKEDOUT|Não é possível remover um arquivo, porque um usuário tiver feito check-out no momento.|
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente devido a problemas de rede ou de contenção.|
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|
|SCC_E_NONSPECIFICERROR|Falha não específica; arquivo não foi removido.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|

## <a name="remarks"></a>Comentários
 Esta função remove os arquivos do sistema de controle de origem, mas não excluí-los da unidade de disco rígido local do usuário.

## <a name="see-also"></a>Consulte também
- [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)