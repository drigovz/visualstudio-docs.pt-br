---
title: Salvando e Exportando Dados de Ferramentas de Desempenho | Microsoft Docs
description: Saiba como você pode salvar exibições filtradas ou não filtradas de arquivos de dados de criação de perfil (. vsp) como arquivos de relatório analisado (. vsps).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b340abd81cef7183c2ba25af58ae432d8c80e6a
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720145"
---
# <a name="save-and-export-performance-tools-data"></a>Salvar e exportar dados de ferramentas de desempenho
Este artigo descreve como salvar e exportar arquivos de dados de desempenho.

## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a>Como salvar arquivos de dados de desempenho como arquivos de relatório analisados
 É possível salvar exibições filtradas ou sem filtro de arquivos de dados de criação de perfil (.*vsp*) como arquivos de relatório analisados (.*vsps*). Um arquivo de relatório analisado pode ser exibido na janela de exibição de relatório e é significativamente menor do que o original. arquivo *VSP* . No entanto, você não pode aplicar um filtro aos dados de um. arquivo *vsps* . Você pode criar um arquivo de relatório analisado do Gerenciador de Desempenho sem abrir o arquivo no ambiente de desenvolvimento integrado (IDE), ou pode abrir e filtrar o. *VSP* e, em seguida, salve os resultados.

#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Salvar um relatório de desempenho analisado do Gerenciador de Desempenho

1. Em **Relatórios**, clique com o botão direito do mouse no arquivo de dados de criação de perfil a ser analisado e, em seguida, clique em **Salvar Analisados**.

2. Na caixa de diálogo **Salvar Dados Analisados**, especifique o diretório e digite o nome de arquivo.

3. Clique em **Salvar.**

#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Salvar um relatório de desempenho analisado da janela Exibição de Relatório

1. Abra os dados de criação de perfil (.*VSP*) no arquivo na janela de exibição de relatório.

2. (Opcional) Aplique um filtro aos dados. Para obter mais informações, consulte [filtro de exibição de relatório de desempenho](../profiling/performance-report-view-filter.md).

3. Clique em **Salvar Analisados** na barra de ferramentas de janela Exibição de Relatório.

4. Na caixa de diálogo **Salvar Dados Analisados**, especifique o diretório e digite o nome de arquivo.

5. Clique em **Salvar.**

## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Como exportar relatórios de ferramentas de criação de perfil para um arquivo .xml ou .csv
 Você pode exportar uma ou mais exibições de relatório de um. arquivo *VSP* ou a. o arquivo de dados de criação de perfil *vsps* como um arquivo XML ou delimitado por vírgula. É possível filtrar os dados na janela Exibição de Relatório antes de exportar ou exportar exibições de relatório de todo o arquivo de dados na janela **Gerenciador de Desempenho**.

> [!NOTE]
> Também é possível copiar e colar linhas selecionadas da janela Exibição de Relatório como valores separados por tabulação.

#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Exportar relatórios de desempenho da janela Gerenciador de Desempenho

1. No **Gerenciador de Desempenho**, selecione o relatório e, em seguida, clique com o botão direito do mouse e selecione **Exportar**.

     A caixa de diálogo **Exportar Relatório** aparecerá.

2. Selecione as exibições de relatório que deseja exportar.

3. Em **Inserir prefixo no relatório**, especifique o prefixo que deseja adicionar ao nome do relatório.

4. Em **Local de Relatório Exportado**, especifique o diretório.

5. Em **Formato de relatório exportado**, selecione (delimitado por vírgula) (\*.csv\) ou Dados XML (\*.xml\).

6. Clique em **Exportar**.

     Cada exibição de relatório é salva em um arquivo separado chamado \<prefix> _ \<report view name> .\<csv&#124;xml>

#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Exportar relatórios de desempenho da janela Exibição de Relatório

1. Abra o. arquivo *VSP* na janela de exibição de relatório.

2. (Opcional) Aplique um filtro aos dados. Para obter mais informações, consulte [filtro de exibição de relatório de desempenho](../profiling/performance-report-view-filter.md).

3. Clique em **Exportar Relatório** na barra de ferramentas de janela Exibição de Relatório.

4. Selecione as exibições de relatório que deseja exportar.

5. Em **Inserir prefixo no relatório**, especifique o prefixo que deseja adicionar ao nome do relatório.

6. Em **Local de Relatório Exportado**, especifique o diretório.

7. Em **formato de relatório exportado**, selecione (delimitado por vírgula) ( \* . csv) ou dados XML ( \* . xml).

8. Clique em **Exportar**.

     Cada exibição de relatório é salva em um arquivo separado chamado \<prefix> _ \<report view name> .\<csv&#124;xml>

## <a name="see-also"></a>Confira também
- [Performance Explorer](../profiling/performance-explorer.md)
- [Analisar dados de ferramentas de desempenho](../profiling/analyzing-performance-tools-data.md)
- [Comparar arquivos de dados de desempenho](../profiling/comparing-performance-data-files.md)
- [VSPerfReport](../profiling/vsperfreport.md)
