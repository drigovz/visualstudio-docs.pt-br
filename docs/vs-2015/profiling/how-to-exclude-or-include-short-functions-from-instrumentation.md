---
title: Como excluir ou incluir funções curtas na instrumentação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8bb49e650f2395bac8a3b5eb1d0f52e2e168731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146115"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Como excluir ou incluir funções curtas a partir da instrumentação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por padrão, as ferramentas de Criação de Perfil excluem *Pequenas Funções* da instrumentação. As pequenas funções são funções curtas que não fazem nenhuma chamada de função. A exclusão dessas pequenas funções fornece menor sobrecarga devido à instrumentação e, portanto, velocidade de instrumentação aprimorada. A exclusão de pequenas funções também reduz o tamanho de arquivo de dados de criação de perfil (.vsp) do desempenho e reduz o tempo necessário para a análise. Se as pequenas funções forem excluídas, o tempo gasto nas pequenas funções contará em relação ao tempo de exclusão e inclusão de suas funções pai. As pequenas funções podem ser excluídas ou incluídas na instrumentação, conforme descrito no procedimento a seguir.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Para excluir ou incluir funções curtas na instrumentação  
  
1. No **Gerenciador de Desempenho**, selecione **Sessão de Desempenho** e, em seguida, clique com o botão direito do mouse em **Propriedades**.  
  
     A caixa de diálogo **Páginas da Propriedade** é exibida.  
  
2. Nas **Páginas de Propriedades**, clique nas propriedades de **Instrumentação**.  
  
3. Para excluir funções curtas da instrumentação, selecione **Excluir funções curtas da Instrumentação**. Essa é a configuração padrão.  
  
     - ou -  
  
     Para incluir funções curtas na instrumentação, desmarque **Excluir funções curtas da Instrumentação**.  
  
4. Clique em **OK**.  
  
## <a name="see-also"></a>Consulte Também  
 [Controlando a coleta de dados](../profiling/controlling-data-collection.md)   
 [Propriedades da sessão de desempenho](../profiling/performance-session-properties.md)
