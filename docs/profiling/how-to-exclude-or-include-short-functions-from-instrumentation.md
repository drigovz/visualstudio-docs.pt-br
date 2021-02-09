---
title: Excluir ou incluir funções curtas de instrumentação
description: Por padrão, funções curtas que não chamam outras funções são excluídas da instrumentação para reduzir a sobrecarga. Saiba como incluí-los ou excluí-los.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9e4cdaf4262f136eb52b9eda7aef5aac831162c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873639"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Como excluir ou incluir funções curtas da instrumentação
Por padrão, as ferramentas de Criação de Perfil excluem *Pequenas Funções* da instrumentação. As pequenas funções são funções curtas que não fazem nenhuma chamada de função. A exclusão dessas pequenas funções fornece menor sobrecarga devido à instrumentação e, portanto, velocidade de instrumentação aprimorada. A exclusão de funções pequenas também reduz o arquivo de dados de criação de perfil de desempenho (.*VSP*) e o tempo necessário para a análise. Se as pequenas funções forem excluídas, o tempo gasto nas pequenas funções contará em relação ao tempo de exclusão e inclusão de suas funções pai. As pequenas funções podem ser excluídas ou incluídas na instrumentação, conforme descrito no procedimento a seguir.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Para excluir ou incluir funções curtas na instrumentação

1. No **Gerenciador de Desempenho**, selecione **Sessão de Desempenho** e, em seguida, clique com o botão direito do mouse em **Propriedades**.

     A caixa de diálogo **Páginas da Propriedade** é exibida.

2. Nas **Páginas de Propriedades**, clique nas propriedades de **Instrumentação**.

3. Para excluir funções curtas da instrumentação, selecione **Excluir funções curtas da Instrumentação**. Essa é a configuração padrão.

     -ou-

     Para incluir funções curtas na instrumentação, desmarque **Excluir funções curtas da Instrumentação**.

4. Clique em **OK**.

## <a name="see-also"></a>Confira também
- [Controlar a coleta de dados](../profiling/controlling-data-collection.md)
- [Propriedades da sessão de desempenho](../profiling/performance-session-properties.md)
