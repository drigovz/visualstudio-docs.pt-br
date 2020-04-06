---
title: Cordas usadas como chaves para encontrar um plug-in de controle de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9333ff1b6742ca14dc5541bd15e92b2eb39085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699711"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Cadeias de caracteres usadas como chaves para localizar um plug-in de controle do código-fonte
As seguintes strings são as chaves para acessar o registro para encontrar informações sobre o plug-in de controle de origem.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` `STR_SCCPROVIDERPATH`, `STR_SCCPROVIDERNAME` e são chaves de registro ou valores usados para registrar uma DLL como um plug-in de controle de origem para o Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE`, `SCC_STATUS_FILE` e são usados para descrever o formato do MSSCCPRJ. Arquivo SCC.

## <a name="string-keys-and-values"></a>Chaves e valores de cordas

|Chave|Valor|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProvedorRegkey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|Nome do servidor SCC|
|`STR_SCC_INI_SECTION`|Controle do Código-Fonte|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Um arquivo de controle de código fonte|
|`SCC_NSE`|Extensão de namespace|
|`SCC_NSE_PREFIX`|Prefixo protocal|
|`SCC_NSE_DisableOpenSCC`|DesativarOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Confira também
- [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
- [Como instalar um plug-in de controle do código-fonte](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Arquivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
