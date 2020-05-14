---
title: Bitflags usados por comandos específicos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740016"
---
# <a name="bitflags-used-by-specific-commands"></a>Bitflags usados por comandos específicos
O comportamento de uma série de funções na API plug-in de controle de fonte pode ser modificado definindo um ou mais bits em um único valor. Esses valores são conhecidos como bitflags. As várias bitflags usadas pela API plug-in de controle de fonte são detalhadas aqui, agrupadas pela função que as utiliza.

## <a name="checked-out-flag"></a>Bandeira verificada
 Este sinalizador pode ser definido para o [SccAdd](../extensibility/sccadd-function.md) ou [SccCheckin](../extensibility/scccheckin-function.md).

|Sinalizador|Valor|Descrição|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantenha o arquivo verificado.|

## <a name="add-flags"></a>Adicionar bandeiras
 Essas bandeiras são usadas pelo [SccAdd](../extensibility/sccadd-function.md).

|Sinalizador|Valor|Descrição|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|Espera-se que o plug-in de controle de origem detecte automaticamente se o arquivo é texto ou binário.|
|`SCC_FILETYPE_TEXT`|0x01|Tipo de arquivo é texto.|
|`SCC_FILETYPE_BINARY`|0x04|O tipo de arquivo é binário. **Nota:** `SCC_FILETYPE_TEXT` e `SCC_FILETYPE_BINARY` as bandeiras são mutuamente exclusivas.   Definir exatamente um ou nenhum.|
|`SCC_ADD_STORELATEST`|0x02|Armazene apenas a versão mais recente (sem deltas).|

## <a name="diff-flags"></a>Bandeiras difusas
 O [SccDiff](../extensibility/sccdiff-function.md) usa essas bandeiras para definir o escopo de uma operação diff. As `SCC_DIFF_QD_xxx` bandeiras são mutuamente exclusivas. Se algum deles for especificado, então nenhum feedback visual deve ser dado. Em um "quick diff" (QD), o plug-in não determina como o arquivo é diferente, apenas se for diferente. Se nenhuma dessas bandeiras for especificada, um "diferencial visual" é feito; diferenças detalhadas de arquivo são calculadas e exibidas. Se o QD solicitado não for suportado, o plug-in passa para o próximo melhor. Por exemplo, se o IDE solicitar uma soma de verificação e o plug-in não for suportado, o plug-in faz uma verificação de conteúdo completo (ainda muito mais rápida do que um display visual).

|Sinalizador|Valor|Descrição|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|Ignore as diferenças de casos.|
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignore as diferenças de espaço branco. **Nota:**  As `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` bandeiras são bandeiras opcionais.|
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD comparando o conteúdo inteiro do arquivo.|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD por cheques.|
|`SCC_DIFF_QD_TIME`|0x0040|QD por data/hora do arquivo.|
|`SCC_DIFF_QUICK_DIFF`|0x0070|Esta é uma máscara usada para verificar todas as bandeiras qd. Não deve ser passado para uma função; as três bandeiras QD são mutuamente exclusivas. QD sempre significa nenhuma exibição de UI.|

## <a name="populatelist-flag"></a>Bandeira PopulateList
 Este sinalizador é usado pelo [SccPopulateList](../extensibility/sccpopulatelist-function.md) no `fOptions` parâmetro.

|Sinalizador|Valor|Descrição|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|O IDE está passando diretórios, não arquivos.|

## <a name="populatedirlist-flags"></a>Bandeiras PopulateDirList
 Essas bandeiras são usadas pelo [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) no `fOptions` parâmetro.

|Valor de Opção|Valor|Descrição|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|Examine apenas um nível de diretórios para diretórios (este é o padrão).|
|SCC_PDL_RECURSIVE|0x0001|Examine recursivamente todos os diretórios sob cada diretório dado.|
|SCC_PDL_INCLUDEFILES|0x0002|Inclua nomes de arquivos no processo de exame.|

## <a name="openproject-flags"></a>Sinalizadores OpenProject
 Essas bandeiras são usadas pelo [SccOpenProject](../extensibility/sccopenproject-function.md) no `dwFlags` parâmetro.

|Valor de Opção|Valor|Descrição|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|Se o projeto não existe no controle de origem, crie-o. Se este sinalizador não estiver definido, solicitará `SCC_OP_SILENTOPEN` ao usuário para que o projeto seja criado (a menos que o sinalizador seja especificado).|
|SCC_OP_SILENTOPEN|0x00000002L|Não solicitar ao usuário a criação de um projeto; apenas `SCC_E_UNKNOWNPROJECT`retornar .|

## <a name="get-flags"></a>Obter bandeiras
 Essas bandeiras são usadas pelo [SccGet](../extensibility/sccget-function.md) e pelo [SccCheckout](../extensibility/scccheckout-function.md).

|Sinalizador|Valor|Descrição|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|O IDE está passando diretórios, não arquivos: Obtenha todos os arquivos nestes diretórios.|
|`SCC_GET_RECURSIVE`|0x00000002L|O IDE está passando diretórios: obtenha esses diretórios e todos os seus subdiretórios.|

## <a name="noption-values"></a>nValorções de opção
 Esses sinalizadores são usados pela `nOption` [Opção SccSet](../extensibility/sccsetoption-function.md) no parâmetro.

|Sinalizador|Valor|Descrição|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Defina o status da fila de eventos.|
|`SCC_OPT_USERDATA`|0x00000002L|Especifique `SCC_OPT_NAMECHANGEPFN`os dados do usuário para .|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|O IDE pode lidar com o cancelamento.|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Defina um retorno de chamada para alterações de nome.|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Desativar o check-out de ia plug-in do controle de origem e não definir o diretório de trabalho.|
|`SCC_OPT_SHARESUBPROJ`|0x0000006L|Adicione do sistema de controle de origem para especificar um diretório de trabalho. Tente compartilhar no projeto associado se ele é um descendente direto.|

## <a name="dwval-bitflags"></a>bitflags dwVal
 Esses sinalizadores são usados pela `dwVal` [Opção SccSet](../extensibility/sccsetoption-function.md) no parâmetro.

|Sinalizador|Valor|Descrição|Usado `nOption` pelo valor|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|Suspende a atividade da fila de eventos.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita o registro da fila de eventos.|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|(Padrão) Não tem modo de cancelamento; plug-in deve fornecer se desejar.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE lida com cancelamento.|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|(Padrão) OK para sair da ui plug-in; diretório de trabalho está definido.|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|Sem check-out de ia plug-in, sem diretório de trabalho.|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>Confira também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
