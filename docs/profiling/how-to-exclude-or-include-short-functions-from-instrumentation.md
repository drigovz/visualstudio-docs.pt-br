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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: de6d6325b1e518146768798c773754c091861aa8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775908"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Como excluir ou incluir funções curtas da instrumentação
Por padrão, as ferramentas de Criação de Perfil excluem *Pequenas Funções* da instrumentação. As pequenas funções são funções curtas que não fazem nenhuma chamada de função. A exclusão dessas pequenas funções fornece menor sobrecarga devido à instrumentação e, portanto, velocidade de instrumentação aprimorada. A exclusão de pequenas funções também reduz o arquivo de dados de perfil de desempenho (.* vsp*) tamanho e o tempo necessário para análise. Se as pequenas funções forem excluídas, o tempo gasto nas pequenas funções contará em relação ao tempo de exclusão e inclusão de suas funções pai. As pequenas funções podem ser excluídas ou incluídas na instrumentação, conforme descrito no procedimento a seguir.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Para excluir ou incluir funções curtas na instrumentação

1. No **Gerenciador de Desempenho**, selecione **Sessão de Desempenho** e, em seguida, clique com o botão direito do mouse em **Propriedades**.

     A caixa de diálogo **Páginas da Propriedade** é exibida.

2. Nas **Páginas de Propriedades**, clique nas propriedades de **Instrumentação**.

3. Para excluir funções curtas da instrumentação, selecione **Excluir funções curtas da Instrumentação**. Essa é a configuração padrão.

     -ou-

     Para incluir funções curtas na instrumentação, desmarque **Excluir funções curtas da Instrumentação**.

4. Clique em **OK**.

## <a name="see-also"></a>Confira também
- [Controle a coleta de dados](../profiling/controlling-data-collection.md)
- [Propriedades da sessão de desempenho](../profiling/performance-session-properties.md)
