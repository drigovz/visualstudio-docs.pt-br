---
title: Quais &apos; s novidades na API de plug-in de controle do código-fonte versão 1,3 | Microsoft Docs
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
ms.openlocfilehash: ec24e9ee3079d3b02ac13759b6ab5bdee8c07a84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88706445"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>O que&#39;s New na API de plug-in de controle do código-fonte versão 1,3
A API de plug-in de controle do código-fonte versão 1,3 apresenta as novas funções a seguir para fornecer controle mais avançado.

## <a name="changes"></a>Alterações
 As seguintes funções são novas na API de plug-in de controle do código-fonte versão 1,3:

|Função|Visão geral|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permite que bits de funcionalidade adicionais sejam relatados|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permite o exame de arquivos que têm versões mais recentes no banco de dados de controle de versão do que no disco local|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permite o exame do estado de alterações de nome (renomeações, adições e exclusões) para arquivos especificados|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permite o exame de diretórios e arquivos no banco de dados do controle de versão|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Adiciona uma lista especificada de arquivos do banco de dados de controle de versão ao projeto atual|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Executa um "Get" silencioso dos arquivos especificados (nenhuma interface do usuário é mostrada)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permite o acesso a opções específicas do usuário|

## <a name="see-also"></a>Confira também
- [Introdução](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novidades na API do plug-in de controle do código-fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
