---
title: Exibição de Linhas – Dados de Contenção | Microsoft Docs
description: Saiba como a exibição de linhas de dados de contenção lista dados de desempenho para as instruções que estavam sendo executadas quando as amostras foram coletadas na execução da criação de perfil.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 863cd741833082ddfac400d86edeba574b4dcb09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917884"
---
# <a name="lines-view---contention-data"></a>Exibição de Linhas – dados de contenção
A exibição de Linhas de dados de contenção lista os dados de desempenho das instruções que estavam em execução quando as amostras foram coletadas na criação de perfil. Em um arquivo de origem, uma instrução pode abranger mais de uma linha em um arquivo de origem, e uma única linha pode incluir mais de uma instrução.

 Uma instrução é identificada pelos seguintes dados:

- O arquivo de origem que contém a instrução da função.

- A função que contém a instrução.

- A linha de origem em que a instrução se inicia.

- O caractere na linha de origem em que a instrução se inicia.

- A linha de origem em que a instrução termina.

- O caractere na linha de origem em que a instrução termina.

  A coluna de Nome de Linha fornece uma concatenação classificável dos dados do identificador.

  A tabela a seguir descreve as colunas do relatório de Exibição de Linhas.

|Coluna|Descrição|
|------------|-----------------|
|**Tempo Bloqueado Exclusivo**|A quantidade de tempo durante o qual a instrução foi impedida de executar o código na instrução em virtude de um evento de contenção. O tempo bloqueado em funções chamadas pela instrução não está incluído.|
|**% de Tempo Bloqueado Exclusivo**|O percentual de todo o tempo bloqueado no processo de tempo bloqueado exclusivo da instrução.|
|**Contenções Exclusivas**|O número de vezes que essa instrução foi impedida de executar o código na instrução em virtude de um evento de contenção. Os eventos de contenção em funções chamadas pela instrução não estão incluídos.|
|**% de Contenções Exclusivas**|O percentual de todos os eventos de contenção no processo que eram contenções exclusivas da instrução.|
|**Endereço da função**|O endereço da função que contém essa instrução.|
|**Nome da função**|O nome totalmente qualificado da função que contém a instrução.|
|**Tempo Bloqueado Inclusivo**|O tempo bloqueado na instrução e funções chamadas na instrução.|
|**% de Tempo Bloqueado Inclusivo**|O percentual de todo o tempo bloqueado no processo de tempo bloqueado inclusivo da instrução.|
|**Contenções Inclusivas**|O número de vezes que a execução da instrução e das funções que foram chamadas nela foi impedida.|
|**% de Contenções Inclusivas**|O percentual de todos os eventos de contenção no processo que eram contenções inclusivas da instrução.|
|**Nome da Linha**|Um identificador gerado pelo criador de perfil da linha. O identificador usa a seguinte sintaxe: `SourceFile` **; [** `LineNumberStart` **,**`CharacterStart` **]->; [**`LineNumberEnd`**,**`CharacterEnd`**]**|
|**Número de linha da função**|O número de linha do início dessa função no arquivo de origem.|
|**Nome do módulo**|O nome do módulo que contém a instrução.|
|**Caminho do Módulo**|O caminho do módulo que contém a instrução.|
|**ID do Processo**|A PID (ID do processo) do processo analisado.|
|**Nome do processo**|O nome do processo.|
|**Início do Caractere de Origem**|O deslocamento do caractere inicial na linha do arquivo de origem em que a instrução se inicia.|
|**Final do Caractere de Origem**|O deslocamento do caractere inicial na linha do arquivo de origem em que a instrução termina.|
|**Arquivo de Origem**|O nome do arquivo de origem que contém a instrução da função.|
|**Início da Linha de Origem**|O número de linha no arquivo de origem na qual a instrução se inicia.|
|**Final da Linha de Origem**|O número da linha no arquivo de origem na qual a instrução termina.|

## <a name="see-also"></a>Confira também
- [Como: Personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md)
- [Exibição de linhas](../profiling/lines-view.md)
- [Exibição de linhas-amostragem](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Exibição de linhas](../profiling/lines-view-sampling-data.md)
