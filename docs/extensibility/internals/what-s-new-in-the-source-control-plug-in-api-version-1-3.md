---
title: O que&#39;s novos na fonte de versão 1.3 da API plug-in de controle | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b61e56fcef8bbbe8e9f36a39580eae14ad582d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856712"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>O que&#39;s novos na fonte de controlar a versão 1.3 plug-in da API
A API de plug-in de controle do código-fonte versão 1.3 apresenta novas funções a seguir para fornecer mais avançados do controle.

## <a name="changes"></a>Alterações
 As funções a seguir são novas para a API de plug-in de controle do código-fonte versão 1.3:

|Função|Visão geral|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Permite que os bits de funcionalidade adicional a ser relatado|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Permite o exame dos arquivos que têm versões mais recentes no versão controle banco de dados que o disco local|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Permite o exame do estado das alterações de nome (renomeações, adições e exclusões) para arquivos especificados|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Permite o exame de diretórios e arquivos no banco de dados de controle de versão|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Adiciona uma lista especificada de arquivos do banco de dados de controle de versão para o projeto atual|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Executa um silenciosa "Get" dos arquivos especificados (sem interface do usuário é mostrado)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Permite o acesso às opções específicas do usuário|

## <a name="see-also"></a>Consulte também
- [Introdução](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novidades na Versão 1.2 da API do plug-in de controle de código-fonte](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)