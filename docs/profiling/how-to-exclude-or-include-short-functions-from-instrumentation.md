---
title: Excluir ou incluir funções curtas de instrumentação
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8f9601a39e755c1a3886f7049abd592d793fb4b
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261342"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Como: Excluir ou incluir funções curtas de instrumentação
Por padrão, as ferramentas de Criação de Perfil excluem *Pequenas Funções* da instrumentação. As pequenas funções são funções curtas que não fazem nenhuma chamada de função. A exclusão dessas pequenas funções fornece menor sobrecarga devido à instrumentação e, portanto, velocidade de instrumentação aprimorada. A exclusão de funções pequenas também reduz o tamanho do arquivo (.*vsp*) de dados de criação de perfil de desempenho e o tempo necessário para análise. Se as pequenas funções forem excluídas, o tempo gasto nas pequenas funções contará em relação ao tempo de exclusão e inclusão de suas funções pai. As pequenas funções podem ser excluídas ou incluídas na instrumentação, conforme descrito no procedimento a seguir.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Para excluir ou incluir funções curtas na instrumentação

1. No **Gerenciador de Desempenho**, selecione **Sessão de Desempenho** e, em seguida, clique com o botão direito do mouse em **Propriedades**.

     A caixa de diálogo **Páginas de Propriedades** é exibida.

2. Nas **Páginas de Propriedades**, clique nas propriedades de **Instrumentação**.

3. Para excluir funções curtas da instrumentação, selecione **Excluir funções curtas da Instrumentação**. Essa é a configuração padrão.

     - ou -

     Para incluir funções curtas na instrumentação, desmarque **Excluir funções curtas da Instrumentação**.

4. Clique em **OK**.

## <a name="see-also"></a>Consulte também
- [Controlar a coleta de dados](../profiling/controlling-data-collection.md)
- [Propriedades da sessão de desempenho](../profiling/performance-session-properties.md)