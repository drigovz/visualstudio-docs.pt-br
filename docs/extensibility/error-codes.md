---
title: Códigos de erro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711838"
---
# <a name="error-codes"></a>Códigos do Erro
Quando uma função de API de controle de fonte retorna um erro, espera-se que seja um dos seguintes códigos de erro. Todos os erros são negativos, avisos ou códigos de erro informativo são positivos, e o sucesso é 0.

|Código do Erro|Valor|Descrição|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|O plug-in suporta a adição de arquivos do controle de origem em duas etapas. Para obter mais informações, consulte [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|O arquivo local é diferente do arquivo no banco de dados de controle de origem (por exemplo, [o SccDiff](../extensibility/sccdiff-function.md) pode retornar esse valor).|
|`SCC_I_RELOADFILE`|5|O arquivo local foi alterado durante a operação de controle de origem; o IDE deve recarregar o arquivo, se possível.|
|`SCC_I_FILENOTAFFECTED`|4|O arquivo não é afetado.|
|`SCC_I_PROJECTCREATED`|3|O Projeto foi criado durante a operação de controle de origem (por exemplo, durante uma chamada para [SccOpenProject](../extensibility/sccopenproject-function.md) quando `SCC_OP_CREATEIFNEW` o sinalizador é especificado).|
|`SCC_I_OPERATIONCANCELED`|2|A operação foi cancelada.|
|`SCC_I_ADV_SUPPORT`|1|O plug-in suporta opções avançadas para o comando especificado. Para obter mais informações, consulte [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Sucesso.|
|`SCC_E_INITIALIZEFAILED`|-1|Erro: falha na inicialização.|
|`SCC_E_UNKNOWNPROJECT`|-2|Erro: o projeto é desconhecido.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Erro: o projeto não pôde ser criado.|
|`SCC_E_NOTCHECKEDOUT`|-4|Erro: o arquivo não é verificado.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Erro: o arquivo já foi verificado.|
|`SCC_E_FILEISLOCKED`|-6|Erro: o arquivo está bloqueado.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Erro: o arquivo é exclusivamente verificado.|
|`SCC_E_ACCESSFAILURE`|-8|Houve um problema de acesso ao sistema de controle de origem, provavelmente devido a problemas de rede ou contenção. Recomenda-se uma nova tentativa.|
|`SCC_E_CHECKINCONFLICT`|-9|Erro: houve um conflito durante o check-in.|
|`SCC_E_FILEALREADYEXISTS`|-10|Erro: o arquivo já existe.|
|`SCC_E_FILENOTCONTROLLED`|-11|Erro: o arquivo não está sob controle de origem.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Erro: o arquivo é verificado.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Erro: não há uma versão especificada.|
|`SCC_E_OPNOTSUPPORTED`|-14|Erro: a operação não é suportada.|
|`SCC_E_NONSPECIFICERROR`|-15|Erro inespecífico.|
|`SCC_E_OPNOTPERFORMED`|-16|Erro, a operação não foi realizada.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Erro: o tipo do arquivo, por exemplo, binário, não é suportado pelo sistema de controle de código-fonte.|
|`SCC_E_VERIFYMERGE`|-18|O arquivo foi mesclado automaticamente, mas não foi verificado porque está pendente de verificação do usuário.|
|`SCC_E_FIXMERGE`|-19|O arquivo foi mesclado automaticamente, mas não foi verificado devido a um conflito de mesclagem que deve ser resolvido manualmente.|
|`SCC_E_SHELLFAILURE`|-20|Erro devido a uma falha na concha.|
|`SCC_E_INVALIDUSER`|-21|Erro: o usuário é inválido.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Erro: o projeto já está aberto.|
|`SCC_E_PROJSYNTAXERR`|-23|Erro de sintaxe do projeto.|
|`SCC_E_INVALIDFILEPATH`|-24|Erro: o caminho do arquivo é inválido.|
|`SCC_E_PROJNOTOPEN`|-25|Erro: o projeto não está aberto.|
|`SCC_E_NOTAUTHORIZED`|-26|Erro: o usuário não está autorizado a realizar esta operação.|
|`SCC_E_FILESYNTAXERR`|-27|Erro de sintaxe de arquivo.|
|`SCC_E_FILENOTEXIST`|-28|Erro, o arquivo local não existe.|
|`SCC_E_CONNECTIONFAILURE`|-29|Erro: houve uma falha na conexão.|
|`SCC_E_UNKNOWNERROR`|-30|Erro desconhecido.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|A operação de antecedentes está em andamento.|

## <a name="macros-provided-for-quick-checking"></a>Macros fornecidas para verificação rápida

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Comentários
 Todas as funções de API plug-in de controle de fonte (exceto o [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)e [SccDiff](../extensibility/sccdiff-function.md)) são esperadas para ter sucesso quando os arquivos locais que são passados como argumentos não existem na pasta de trabalho. Por exemplo, o IDE pode emitir uma chamada para o [SccCheckout](../extensibility/scccheckout-function.md) ou [SccUncheckout](../extensibility/sccuncheckout-function.md) em um arquivo que não existe na pasta de trabalho, mas existe no sistema de controle de origem. Esta chamada teria sucesso. Somente quando não há nenhum arquivo na pasta de trabalho ou no sistema de controle de origem é que a função deverá falhar.

 Certas funções, `SccAdd` como `SccCheckin`e , `SCC_E_FILENOTEXIST` devem retornar especificamente quando o arquivo na pasta de trabalho não existe. Espera-se que outras funções tenham sucesso quando o arquivo de trabalho não existir, se as funções funcionarem em um nome de arquivo válido no sistema de controle de origem.

 O plug-in de controle de origem não deve fazer suposições sobre privilégios em um arquivo na pasta de trabalho, mesmo que o plug-in tenha marcado a leitura do arquivo somente durante alguma operação. Um arquivo na pasta de trabalho pode ser movido, excluído e alterado fora do controle do plug-in.

## <a name="see-also"></a>Confira também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
