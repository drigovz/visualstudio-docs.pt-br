---
title: Criar um relatório de comparação do Profiler (linha de comando)
description: Use VSPerfReport.exe da linha de comando para comparar os resultados de dois arquivos de dados do criador de perfil. A comparação mostra as diferenças entre as sessões de criação de perfil.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e647d467dcbc397fe261c2ea83f6fa9ab1bba7b6
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800392"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>Como criar um relatório de comparação de criador de perfil por meio de um prompt de comando
Você pode gerar um relatório de Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que compara os dados de desempenho de dois arquivos de dados de criação de perfil (.*vsp* ou .*vsps*). O relatório mostra as diferenças, as regressões de desempenho e as melhorias que ocorreram de uma sessão de criação de perfil para a outra. Os valores no relatório apresentam o delta ou alteração, da linha de base do primeiro arquivo que você especificar. Esse delta é calculado determinando a diferença entre o valor antigo, que é o valor de linha de base e o valor do resultado da nova análise. As comparações de dados do criador de perfil podem ser baseadas nas funções no código, nos módulos no aplicativo, nas linhas, nos IPs (ponteiros de instrução) e nos tipos.

 Para listar os identificadores dos campos e categorias de comparação, digite a seguinte linha de comando:

 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*

 Use a sintaxe a seguir para criar o relatório de comparação:

 **VSPerfReport/diff** `VspFileName1` *VspFileName2* [ **/** `Options` ]  

 Você pode adicionar opções da tabela a seguir para a linha de comando **VSPerfReport /diff**.

|Opção|Descrição|
|------------|-----------------|
|**DiffThreshold:**[*Value*]|Ignore a diferença se ela estiver abaixo desse valor de limite de percentual. Além disso, novos dados com valores abaixo desse limite não aparecerão.|
|**DiffTable:** *TableName*|Use esta tabela para comparar arquivos. Por padrão, a tabela de funções é usada. Especifique o identificador que está listado em **VSPerfReport /querydifftables**.|
|**DiffColumn:** *ColumnName*|Use essa coluna para comparar valores. Por padrão, a coluna de porcentagem de amostras exclusivas é usada. Especifique o identificador que está listado em **VSPerfReport /querydifftables**.|
