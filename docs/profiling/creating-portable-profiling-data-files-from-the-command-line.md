---
title: Linha de comando de criação de perfil – criar arquivos de dados portáteis
description: Para facilitar o compartilhamento de dados de criação de perfil, use a ferramenta de linha de comando VSPerfReport.exe para inserir os símbolos para uma criação de perfil no arquivo. vsp.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 258ed7d22114cba1d934a70c7bbef39364482464
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955938"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Criar arquivos de dados de criação de perfil móveis por meio da linha de comando
Para facilitar o compartilhamento de dados de criação de perfil, use a ferramenta de linha de comando [VSPerfReport](../profiling/vsperfreport.md) para inserir os símbolos de uma execução de criação de perfil no arquivo .*vsp*.

 Crie também um arquivo de dados de criação de perfil pré-analisado (.*vsps*) que é menor e mais rápido para ser carregado no IDE.

> [!NOTE]
> Verifique se os arquivos de símbolo (.*pdb*) estão disponíveis para **VSPerfReport**. Para obter mais informações, consulte [como especificar locais de arquivo de símbolo na linha de comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Para obter informações sobre o caminho para **VSReport**, confira [Especificar o caminho para as ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Os dados de criação de perfil em um arquivo .*vsps* não podem ser filtrados.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Para inserir os símbolos de uma execução de criação de perfil em um arquivo de dados de criação de perfil (.*vsp*)

- Em uma janela de prompt de comando, digite o seguinte comando:

   \<Path><strong>\<</strong>Arquivo VSPerfReport VSP> **/PackSymbols**

   Por padrão, o arquivo .*vsps* é nomeado com o nome base do arquivo .*vsp*. Você pode especificar um nome alternativo usando a opção **Saída**.

### <a name="to-create-a-summary-profiling-data-file"></a>Para criar um arquivo de dados de criação de perfil de resumo

- Em uma janela de prompt de comando, digite o seguinte comando:

   \<Path><strong>\<</strong>Arquivo VSPerfReport VSP> **/SummaryFile** [**/output:** \<File Name> ]

   Por padrão, o arquivo .*vsps* é nomeado com o nome base do arquivo .*vsp*. Você pode especificar um nome alternativo usando a opção **Saída**.
