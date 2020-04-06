---
title: Função SccCheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701100"
---
# <a name="scccheckout-function"></a>Função SccCheckout
Dada uma lista de nomes de arquivos totalmente qualificados, esta função os verifica para a unidade local. O comentário se aplica a todos os arquivos que estão sendo verificados. O argumento de `null` comentário pode ser uma string.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>parâmetros
 pvContext

[em] A estrutura de contexto plug-in de controle de origem.

 hWnd

[em] Uma alça para a janela IDE que o plug-in de controle de origem pode usar como pai para quaisquer caixas de diálogo que ele forneça.

 nArquivos

[em] Número de arquivos selecionados para serem verificados.

 lpFileNames

[em] Matriz de nomes de arquivos locais totalmente qualificados a serem verificados.

 lpComment

[em] Comentário a ser aplicado a cada um dos arquivos selecionados que estão sendo verificados.

 fOpções

[em] Bandeiras de comando (ver [Bitflags usadas por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOpções

[em] Opções específicas de plug-in de controle de origem.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O check-out foi bem sucedido.|
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle de código fonte.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a realizar esta operação.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica. O arquivo não foi verificado.|
|SCC_E_ALREADYCHECKEDOUT|O usuário já tem o arquivo verificado.|
|SCC_E_FILEISLOCKED|O arquivo está bloqueado, proibindo a criação de novas versões.|
|SCC_E_FILEOUTEXCLUSIVE|Outro usuário fez um checkout exclusivo neste arquivo.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|

## <a name="see-also"></a>Confira também
- [Funções de API plug-in de controle de origem](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
