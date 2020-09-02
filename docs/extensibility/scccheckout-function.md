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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701100"
---
# <a name="scccheckout-function"></a>Função SccCheckout
Dada uma lista de nomes de arquivo totalmente qualificados, essa função os verifica na unidade local. O comentário se aplica a todos os arquivos cujo check-out está sendo feito. O argumento comment pode ser uma `null` cadeia de caracteres.

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

### <a name="parameters"></a>Parâmetros
 pvContext

no A estrutura de contexto do plug-in de controle do código-fonte.

 hWnd

no Um identificador para a janela do IDE que o plug-in de controle do código-fonte pode usar como um pai para qualquer caixa de diálogo que ele fornecer.

 nFiles

no Número de arquivos selecionados para check-out.

 lpFileNames

no Matriz de nomes de caminho locais totalmente qualificados dos arquivos cujo check-out será feito.

 lpComment

no Comentário a ser aplicado a cada um dos arquivos selecionados cujo check-out está sendo feito.

 fOptions

no Sinalizadores de comando (consulte [Bitflags usado por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

no Opções específicas de plug-ins de controle do código-fonte.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|O check-out foi bem-sucedido.|
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está no controle do código-fonte.|
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente devido a problemas de rede ou de contenção. Uma nova tentativa é recomendada.|
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|
|SCC_E_NONSPECIFICERROR|Falha não específica. Não foi feito o check-out do arquivo.|
|SCC_E_ALREADYCHECKEDOUT|O usuário já tem o arquivo extraído.|
|SCC_E_FILEISLOCKED|O arquivo está bloqueado, proibindo a criação de novas versões.|
|SCC_E_FILEOUTEXCLUSIVE|Outro usuário fez um check-out exclusivo nesse arquivo.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|

## <a name="see-also"></a>Confira também
- [Funções da API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags usado por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)
