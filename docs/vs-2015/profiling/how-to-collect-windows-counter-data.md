---
title: 'Como: Coletar dados do contador do Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2c3e4a9cffd81561af39cef5eb88f4a7745b2dad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54753410"
---
# <a name="how-to-collect-windows-counter-data"></a>Como: Coletar dados de contador do Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os contadores do Windows são contadores de desempenho do sistema que podem ser coletados em intervalos definidos durante a criação de perfil. Na exibição de Marcas do relatório das Ferramentas de Criação de Perfil, uma linha é rotulada **AutoMark** para cada intervalo de coleta. A linha contém colunas que descrevem os valores do contador de desempenho nesse intervalo. Para restringir a análise para um período de tempo entre duas marcas específicas, selecione as marcas, clique com o botão direito do mouse e, em seguida, selecione **Filtrar por** ->  **Marcas** no menu de atalho.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos da Windows Store também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Para coletar dados do contador do Windows  
  
1.  No Gerenciador de Desempenho, clique com botão direito do mouse na sessão para a qual você deseja configurar os contadores do Windows e selecione **Propriedades**.  
  
2.  Nas **Páginas de Propriedades**, clique em **Contadores do Windows**.  
  
3.  Selecione a caixa de seleção **Coletar Contadores do Windows**.  
  
4.  Na caixa de texto **Intervalo de coleta (ms)**, digite um intervalo de tempo.  
  
5.  Selecione uma categoria da lista suspensa **Categoria de Contador**.  
  
6.  Selecione uma instância da lista suspensa de **Instância**.  
  
7.  Selecione os contadores que você deseja usar ao analisar seu aplicativo.  
  
8.  Clique em **Aplicar.**  
  
## <a name="see-also"></a>Consulte também  
 [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)   
 [Propriedades da sessão de desempenho](../profiling/performance-session-properties.md)   
 [Contadores da CPU e do Windows](../profiling/cpu-and-windows-counters.md)
