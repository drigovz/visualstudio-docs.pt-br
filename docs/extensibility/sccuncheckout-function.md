---
title: Função SccUncheckout | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d50b321f96b6759d95a6d923222e5e0a92b2ee3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338467"
---
# <a name="sccuncheckout-function"></a>Função SccUncheckout
Essa função Desfaz uma operação de check-out anterior, restaurando assim o conteúdo de arquivos ou o arquivo selecionado para o estado antes do check-out. Todas as alterações feitas desde o check-out no arquivo serão perdidas.

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

#### <a name="parameters"></a>Parâmetros
 pvContext

[in] A estrutura de contexto de plug-in de controle de origem.

 hWnd

[in] Um identificador para a janela do IDE que o plug-in de controle de origem pode usar como um pai para todas as caixas de diálogo que ele oferece.

 nFiles

[in] Número de arquivos especificados no `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nomes de caminho local totalmente qualificado dos arquivos para os quais desfazer um check-out.

 fOptions

[in] Sinalizadores de comando (não usados).

 pvOptions

[in] Opções de plug-in específico de controle de origem.

## <a name="return-value"></a>Valor de retorno
 A implementação de plug-in de controle do código-fonte desta função deve retornar um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|Desfazer check-out foi bem-sucedida.|
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle do código-fonte.|
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente devido a problemas de rede ou de contenção. É recomendável uma nova tentativa.|
|SCC_E_NONSPECIFICERROR|Falha não específica. Desfazer check-out não foi bem-sucedida.|
|SCC_E_NOTCHECKEDOUT|O usuário não tem o arquivo de check-out.|
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|
|SCC_E_PROJNOTOPEN|O projeto não foi aberto do controle de origem.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada antes da conclusão.|

## <a name="remarks"></a>Comentários
 Depois dessa operação, o `SCC_STATUS_CHECKEDOUT` e `SCC_STATUS_MODIFIED` sinalizadores serão ambos ser desmarcados para os arquivos no qual o desfazer check-out foi executado.

## <a name="see-also"></a>Consulte também
- [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)