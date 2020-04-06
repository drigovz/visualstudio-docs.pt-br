---
title: Função SccRunScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700403"
---
# <a name="sccrunscc-function"></a>Função SccRunScc
Esta função invoca a ferramenta de administração de controle de origem.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
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

[em] Matriz de nomes de arquivos selecionados.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação plug-in de controle de origem desta função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A ferramenta de administração de controle de origem foi invocada com sucesso.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada.|
|SCC_E_INITIALIZEFAILED|Falhou em inicializar o sistema de controle de origem.|
|SCC_E_ACCESSFAILURE|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção.|
|SCC_E_CONNECTIONFAILURE|Falha ao conectar-se ao sistema de controle de origem.|
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está sob controle de origem.|
|SCC_E_NONSPECIFICERROR|Falha inespecífica.|

## <a name="remarks"></a>Comentários
 Esta função permite que o chamador acesse toda a gama de recursos do sistema de controle de origem através de uma ferramenta de administração externa. Se o sistema de controle de origem não tiver interface de usuário, o plug-in de controle de origem pode implementar uma interface para executar as funções de administração necessárias.

 Esta função é chamada com uma contagem e uma matriz de nomes de arquivos para os arquivos selecionados no momento. Se a ferramenta de administração o suportar, a lista de arquivos pode ser usada para pré-selecionar arquivos na interface de administração; caso contrário, a lista pode ser ignorada.

 Essa função é normalmente invocada quando o usuário seleciona o>do Servidor de Controle de Origem de **Origem \<** do menu Controle de**Origem** de **Arquivo.** ->  Esta opção de menu **Iniciar** pode ser sempre desativada ou até mesmo oculta definindo uma entrada de registro. [Veja como: Instale um plug-in de controle de origem](../extensibility/internals/how-to-install-a-source-control-plug-in.md) para obter detalhes. Esta função é chamada apenas se `SCC_CAP_RUNSCC` [SccInitialize](../extensibility/sccinitialize-function.md) retornar o bit de capacidade (consulte [Sinalizadores de capacidade](../extensibility/capability-flags.md) para obter detalhes sobre este e outros bits de capacidade).

## <a name="see-also"></a>Confira também
- [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [Como instalar um plug-in de controle do código-fonte](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Sinalizadores de capacidade](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
