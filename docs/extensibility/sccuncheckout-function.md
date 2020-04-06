---
title: Função SccUncheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700240"
---
# <a name="sccuncheckout-function"></a>Função SccUncheckout
Esta função desfaz uma operação de checkout anterior, restaurando assim o conteúdo do arquivo ou arquivos selecionados para o estado antes do checkout. Todas as alterações feitas no arquivo desde o checkout são perdidas.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
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

[em] Matriz de nomes de arquivos de caminho sumidos totalmente qualificados para os quais desfazer um checkout.

 fOpções

[em] Bandeiras de comando (não utilizadas).

 pvOpções

[em] Opções específicas de plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Desfazer checkout foi bem sucedido.|
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle de código fonte.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica. Desfazer checkout não teve sucesso.|
|SCC_E_NOTCHECKEDOUT|O usuário não tem o arquivo verificado.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_PROJNOTOPEN|O projeto não foi aberto a partir do controle de origem.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|

## <a name="remarks"></a>Comentários
 Após esta operação, os `SCC_STATUS_CHECKEDOUT` e `SCC_STATUS_MODIFIED` as bandeiras serão liberados para os arquivos em que o check-out desfazer foi realizado.

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
