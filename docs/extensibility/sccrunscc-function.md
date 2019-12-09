---
title: Função SccRunScc | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e577af3ce70280b81681cb72295c3511dd3ab4a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720550"
---
# <a name="sccrunscc-function"></a>Função SccRunScc
Essa função invoca a ferramenta de administração do controle do código-fonte.

## <a name="syntax"></a>Sintaxe

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>Parâmetros
 pvContext

no A estrutura de contexto do plug-in de controle do código-fonte.

 hWnd

no Um identificador para a janela do IDE que o plug-in de controle do código-fonte pode usar como um pai para qualquer caixa de diálogo que ele fornecer.

 nFiles

no Número de arquivos especificados na matriz de `lpFileNames`.

 lpFileNames

no Matriz de nomes de arquivo selecionados.

## <a name="return-value"></a>Valor retornado
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:

|Valor|Descrição|
|-----------|-----------------|
|SCC_OK|A ferramenta de administração do controle do código-fonte foi invocada com êxito.|
|SCC_I_OPERATIONCANCELED|A operação foi cancelada.|
|SCC_E_INITIALIZEFAILED|Falha ao inicializar o sistema de controle do código-fonte.|
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente devido a problemas de rede ou de contenção.|
|SCC_E_CONNECTIONFAILURE|Falha ao conectar ao sistema de controle do código-fonte.|
|SCC_E_FILENOTCONTROLLED|O arquivo selecionado não está no controle do código-fonte.|
|SCC_E_NONSPECIFICERROR|Falha não específica.|

## <a name="remarks"></a>Comentários
 Essa função permite que o chamador acesse a gama completa de recursos do sistema de controle do código-fonte por meio de uma ferramenta de administração externa. Se o sistema de controle do código-fonte não tiver nenhuma interface do usuário, o plug-in de controle do código-fonte poderá implementar uma interface para executar as funções de administração necessárias.

 Essa função é chamada com uma contagem e uma matriz de nomes de arquivo para os arquivos selecionados no momento. Se a ferramenta de administração oferecer suporte a ela, a lista de arquivos poderá ser usada para preselecionar arquivos na interface de administração; caso contrário, a lista poderá ser ignorada.

 Essa função é normalmente invocada quando o usuário seleciona a **inicialização \<Source servidor de controle >** no menu de**controle do código-fonte**  ->  do **arquivo** . Essa opção de menu **Iniciar** pode ser sempre desabilitada ou até mesmo oculta com a definição de uma entrada de registro. Consulte [como: instalar um plug-in de controle do código-fonte](../extensibility/internals/how-to-install-a-source-control-plug-in.md) para obter detalhes. Essa função será chamada somente se [SccInitialize](../extensibility/sccinitialize-function.md) retornar o bit de recurso de `SCC_CAP_RUNSCC` (consulte os [sinalizadores de capacidade](../extensibility/capability-flags.md) para obter detalhes sobre esse e outros bits de funcionalidade).

## <a name="see-also"></a>Consulte também
- [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
- [Como instalar um plug-in de controle do código-fonte](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Sinalizadores de recurso](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)