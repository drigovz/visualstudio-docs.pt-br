---
title: Bandeiras de capacidade | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739873"
---
# <a name="capability-flags"></a>Bandeiras de capacidade
Os SCC_CAP_*xxx* bandeiras são sinalizadores de bits usados para indicar as capacidades de um plug-in de controle de origem. As SCC_EXCAP_*bandeiras xxx* são bandeiras incrementais que indicam capacidades estendidas e resolvem valores inteiros.

|Código de capacidade|Valor|Descrição|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Suporta o [comando SccRemove](../extensibility/sccremove-function.md) e command.|
|`SCC_CAP_RENAME`|0x00000002L|Suporta o [SccRename](../extensibility/sccrename-function.md) e o comando.|
|`SCC_CAP_DIFF`|0x00000004L|Suporta o [Comando SccDiff](../extensibility/sccdiff-function.md) e o comando.|
|`SCC_CAP_HISTORY`|0x00000008L|Suporta o [SccHistory](../extensibility/scchistory-function.md) e o comando.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Suporta o [comando SccProperties](../extensibility/sccproperties-function.md) e o comando.|
|`SCC_CAP_RUNSCC`|0x00000020L|Suporta o [comando SccRunScc.](../extensibility/sccrunscc-function.md)|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Suporta o [comando SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e o comando.|
|`SCC_CAP_QUERYINFO`|0x0000080L|Suporta o [comando SccQueryInfo.](../extensibility/sccqueryinfo-function.md)|
|`SCC_CAP_GETEVENTS`|0x00000100L|Suporta o [comando SccGetEvents](../extensibility/sccgetevents-function.md) e o comando.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Suporta o [comando SccGetProjPath](../extensibility/sccgetprojpath-function.md) e o comando.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Suporta o [comando SccAddFromScc.](../extensibility/sccaddfromscc-function.md)|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Suporta um comentário sobre checkout.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Suporta um comentário sobre check-in.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Suporta um comentário sobre Add.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Suporta um comentário sobre Remover.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Grava texto em uma função de saída fornecida pelo IDE.|
|`SCC_CAP_ADD_STORELATEST`|0x0020000L|Suporta armazenar arquivos sem deltas.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Suporta histórico de arquivos múltiplos.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Suporta comparação de arquivos insensíveis a casos.|
|`SCC_CAP_IGNORESPACE`|0x0100000L|Suporta comparação de arquivos que ignora o espaço em branco.|
|`SCC_CAP_POPULATELIST`|0x0200000L|Suporta encontrar arquivos extras.|
|`SCC_CAP_COMMENTPROJECT`|0x0400000L|Suporta comentários sobre criar projeto.|
|`SCC_CAP_DIFFALWAYS`|0x1000000L|Suporta diff em todos os estados se estiver sob controle.|
|`SCC_CAP_GET_NOUI`|0x2000000L|O plug-in não suporta uma ida de ida para Get, mas o IDE ainda pode chamar [sccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x4000000L|O plug-in é reentrante e seguro para rosca. Na versão 1.0, não se presumia que os plug-ins fossem reentrantes e seguros para rosca. Se um plug-in 1.1 definir esse bit, o host poderá abrir vários projetos em paralelo.|

## <a name="capability-bits-added-in-version-12"></a>Bits de capacidade adicionados na versão 1.2

|Código de capacidade|Valor|Descrição|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x0001000L|Suporta o [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x0002000L|Suporta o [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Suporta o [SccBeginBatch](../extensibility/sccbeginbatch-function.md) e [o SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Suporta o [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x0010000L|Suporta o [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Suporta vários checkouts em um arquivo e o [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Suporta o arquivo *MSSCCPRJ.SCC* (sujeito à substituição do usuário/administrador) e o [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bits de capacidade adicionados na versão 1.3
 Esses sinalizadores são passados um de cada vez para a função [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) para determinar se o recurso é suportado.

|Código de capacidade estendida|Valor|Descrição|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Suporta a `SCC_CHECKOUT_LOCALVER` opção de checkouts.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Suporta o [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Suporta o [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Suporta encontrar diretórios extras.|
|`SCC_EXCAP_QUERYCHANGES`|5|Suporta enumeração de alterações de arquivo.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Suporta o [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Suporta a [opção SccGetUser .](../extensibility/sccgetuseroption-function.md)|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Suporta chamar SccQueryInfo em vários segmentos.|
|`SCC_EXCAP_REMOVE_DIR`|9|Suporta a função SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Pode excluir arquivos de check-out.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Pode renomear arquivos de check-out.|

## <a name="see-also"></a>Confira também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
