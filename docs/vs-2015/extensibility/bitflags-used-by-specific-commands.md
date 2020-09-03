---
title: Bitflags usado por comandos específicos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43dc083812bc172fe4a9f80335742b3faab2e1f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184691"
---
# <a name="bitflags-used-by-specific-commands"></a>Sinalizadores de bit usados por comandos específicos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O comportamento de várias funções na API de plug-in de controle do código-fonte pode ser modificado pela definição de um ou mais bits em um único valor. Esses valores são conhecidos como bitflags. Os vários bitflags usados pela API de plug-in de controle do código-fonte são detalhados aqui, agrupados pela função que os utiliza.  
  
## <a name="checked-out-flag"></a>Sinalizador de check-out  
 Esse sinalizador pode ser definido para [SccAdd](../extensibility/sccadd-function.md) ou [SccCheckin](../extensibility/scccheckin-function.md).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Mantenha o check-out do arquivo.|  
  
## <a name="add-flags"></a>Adicionar sinalizadores  
 Esses sinalizadores são usados pelo [SccAdd](../extensibility/sccadd-function.md).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|Espera-se que o plug-in de controle do código-fonte detecte automaticamente se o arquivo é texto ou binário.|  
|`SCC_FILETYPE_TEXT`|0x01|O tipo de arquivo é texto.|  
|`SCC_FILETYPE_BINARY`|0x04|O tipo de arquivo é binário. **Observação:** `SCC_FILETYPE_TEXT` e os `SCC_FILETYPE_BINARY` sinalizadores são mutuamente exclusivos.   Defina exatamente um ou nenhum.|  
|`SCC_ADD_STORELATEST`|0x02|Armazenar somente a versão mais recente (sem deltas).|  
  
## <a name="diff-flags"></a>Sinalizadores de comparação  
 O [SccDiff](../extensibility/sccdiff-function.md) usa esses sinalizadores para definir o escopo de uma operação de comparação. Os `SCC_DIFF_QD_xxx` sinalizadores são mutuamente exclusivos. Se qualquer um deles for especificado, nenhum comentário visual será fornecido. Em uma "diferença rápida" (QD), o plug-in não determina como o arquivo é diferente, somente se ele for diferente. Se nenhum desses sinalizadores for especificado, uma "diferença visual" será feita; diferenças de arquivo detalhadas são computadas e exibidas. Se o QD solicitado não for suportado, o plug-in passará para o próximo melhor. Por exemplo, se o IDE solicitar uma soma de verificação e o plug-in não oferecer suporte a ela, o plug-in fará uma verificação de conteúdo completo (ainda muito mais rápido do que uma exibição Visual).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorar diferenças de maiúsculas e minúsculas.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorar diferenças de espaço em branco. **Observação:**  Os `SCC_DIFF_IGNORECASE` `SCC_DIFF_IGNORESPACE` sinalizadores e são opcionais bitflags.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD ao comparar todo o conteúdo do arquivo.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD por soma de verificação.|  
|`SCC_DIFF_QD_TIME`|0x0040|QD por carimbo de data/hora do arquivo.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Essa é uma máscara usada para verificar todos os QD bitflags. Ele não deve ser passado para uma função; os três QD bitflags são mutuamente exclusivos. QD sempre significa que não há exibição da interface do usuário.|  
  
## <a name="populatelist-flag"></a>Sinalizador Population  
 Esse sinalizador é usado pelo [SccPopulateList](../extensibility/sccpopulatelist-function.md) no `fOptions` parâmetro.  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|O IDE está passando diretórios, não arquivos.|  
  
## <a name="populatedirlist-flags"></a>Sinalizadores de PopulateDirList  
 Esses sinalizadores são usados pelo [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) no `fOptions` parâmetro.  
  
|Valor de Opção|Valor|Descrição|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Examine apenas um nível de diretório para diretórios (esse é o padrão).|  
|SCC_PDL_RECURSIVE|0x0001|Examine recursivamente todos os diretórios em cada diretório especificado.|  
|SCC_PDL_INCLUDEFILES|0x0002|Inclua nomes de arquivo no processo de exame.|  
  
## <a name="openproject-flags"></a>Sinalizadores de OpenProject  
 Esses sinalizadores são usados pelo [SccOpenProject](../extensibility/sccopenproject-function.md) no `dwFlags` parâmetro.  
  
|Valor de Opção|Valor|Descrição|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Se o projeto não existir no controle do código-fonte, crie-o. Se esse sinalizador não for definido, solicite ao usuário para que o projeto seja criado (a menos que o `SCC_OP_SILENTOPEN` sinalizador seja especificado).|  
|SCC_OP_SILENTOPEN|0x00000002L|Não solicitar que o usuário crie um projeto; Basta retornar `SCC_E_UNKNOWNPROJECT` .|  
  
## <a name="get-flags"></a>Obter sinalizadores  
 Esses sinalizadores são usados pelo [SccGet](../extensibility/sccget-function.md) e pelo [SccCheckout](../extensibility/scccheckout-function.md).  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|O IDE está passando diretórios, não arquivos: obter todos os arquivos nesses diretórios.|  
|`SCC_GET_RECURSIVE`|0x00000002L|O IDE está passando diretórios: Obtenha esses diretórios e todos os seus subdiretórios.|  
  
## <a name="noption-values"></a>Valores de nOption  
 Esses sinalizadores são usados pelo [SccSetOption](../extensibility/sccsetoption-function.md) no `nOption` parâmetro.  
  
|Sinalizador|Valor|Descrição|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Defina o status da fila de eventos.|  
|`SCC_OPT_USERDATA`|0x00000002L|Especifique os dados do usuário para `SCC_OPT_NAMECHANGEPFN` .|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|O IDE pode manipular cancelar|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Defina um retorno de chamada para as alterações de nome.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Desabilitar o check-in da IU de plug-in de controle do código-fonte e não definir o diretório de trabalho|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Adicione do sistema de controle do código-fonte para especificar um diretório de trabalho. Tente compartilhar no projeto associado se ele for um descendente direto.|  
  
## <a name="dwval-bitflags"></a>dwVal Bitflags  
 Esses sinalizadores são usados pelo [SccSetOption](../extensibility/sccsetoption-function.md) no `dwVal` parâmetro.  
  
|Sinalizador|Valor|Descrição|Usado pelo `nOption` valor|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00l|Suspende a atividade da fila de eventos.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Habilita o log da fila de eventos.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|Os Não tem modo de cancelamento; o plug-in deve fornecer, se desejado.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|O IDE manipula o cancelamento.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|Os OK para fazer check-out da interface do usuário de plug-in; o diretório de trabalho está definido.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Nenhum check-in da interface do usuário de plug-in, nenhum diretório de trabalho.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Consulte Também  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
