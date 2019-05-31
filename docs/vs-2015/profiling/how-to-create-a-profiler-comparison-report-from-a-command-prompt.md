---
title: Como criar um relatório de comparação de criador de perfil por meio de um prompt de comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8c6dabbae5f2d3758aebe0562f99767ee6993d80
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756733"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Como criar um relatório de comparação de criador de perfil a partir de um prompt de comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode gerar um relatório de Ferramentas de criação de perfil de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que compara os dados de desempenho de dois arquivos de dados de criação de perfil (.VSP /ou .VSPS). O relatório mostra as diferenças, as regressões de desempenho e as melhorias que ocorreram de uma sessão de criação de perfil para a outra. Os valores no relatório apresentam o delta ou alteração, da linha de base do primeiro arquivo que você especificar. Esse delta é calculado determinando a diferença entre o valor antigo, que é o valor de linha de base e o valor do resultado da nova análise. As comparações de dados do criador de perfil podem ser baseadas nas funções no código, nos módulos no aplicativo, nas linhas, nos IPs (ponteiros de instrução) e nos tipos.  
  
 Para listar os identificadores dos campos e categorias de comparação, digite a seguinte linha de comando:  
  
 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*  
  
 Use a sintaxe a seguir para criar o relatório de comparação:  
  
 **VSPerfReport /diff**  `VspFileName1` *VspFileName2* [ **/** `Options`]  
  
 Você pode adicionar opções da tabela a seguir para a linha de comando **VSPerfReport /diff**.  
  
|Opção|Descrição|  
|------------|-----------------|  
|**DiffThreshold:** [*Value*]|Ignore a diferença se ela estiver abaixo desse valor de limite de percentual. Além disso, novos dados com valores abaixo desse limite não aparecerão.|  
|**DiffTable:** *TableName*|Use esta tabela para comparar arquivos. Por padrão, a tabela de funções é usada. Especifique o identificador que está listado em **VSPerfReport /querydifftables**.|  
|**DiffColumn:** *ColumnName*|Use essa coluna para comparar valores. Por padrão, a coluna de porcentagem de amostras exclusivas é usada. Especifique o identificador que está listado em **VSPerfReport /querydifftables**.|
