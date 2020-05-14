---
title: O que&#39;novidade na API plug-in de controle de fonte Versão 1.3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703368"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>O que&#39;é novidade na API plug-in de controle de fonte versão 1.3
A versão 1.3 do Plug-in Source Control Plug-in introduz as seguintes novas funções para fornecer controle mais avançado.

## <a name="changes"></a>Alterações
 As seguintes funções são novas na versão 1.3 da API plug-in de controle de fonte:

|Função|Visão geral|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permite que bits adicionais de capacidade sejam relatados|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permite o exame de arquivos que têm versões mais recentes no banco de dados de controle de versão do que no disco local|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permite examinar o estado das alterações de nome (renomes, adições e exclusões) para arquivos especificados|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permite o exame de diretórios e arquivos no banco de dados de controle de versão|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Adiciona uma lista especificada de arquivos do banco de dados de controle de versão ao projeto atual|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Executa um "Get" silencioso dos arquivos especificados (nenhuma interface de usuário é mostrada)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permite acesso a opções específicas do usuário|

## <a name="see-also"></a>Confira também
- [Introdução](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novidades na API do plug-in de controle do código-fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
