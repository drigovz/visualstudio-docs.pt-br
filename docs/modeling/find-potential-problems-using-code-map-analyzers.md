---
title: Encontrar possíveis problemas usando analisadores de mapa de códigos
description: Saiba como você pode executar analisadores em mapas de código para ajudá-lo a identificar o código que pode ser excessivamente complexo ou que pode precisar de aperfeiçoamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77e5d8f6241f6f1978f24b9ebb5ad49aa9f24331
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934982"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Encontrar possíveis problemas usando analisadores de mapa de códigos

Execute analisadores em mapas de código para ajudá-lo a identificar o código que pode ser excessivamente complexo ou que pode precisar de melhoria. Por exemplo, você pode usar esses analisadores:

|**Para encontrar o código que tem**|**Examine essas áreas para ver se**|
|-|-|
|Loops ou dependências circulares|Você pode simplificá-los e considerar se pode interromper esses ciclos.|
|Excesso de dependências|Eles estão executando muitas funções ou para determinar o impacto da alteração dessas áreas. Um mapa de código bem formado mostrará um número mínimo de dependências. Para tornar o código mais fácil de manter, alterar, testar e reutilizar, considere se você pode refatorar essas áreas para que elas sejam definidas com mais clareza ou se você pode mesclar o código que executa funções semelhantes.|
|Sem dependências|Eles são necessários ou se você deve remover esse código.|

## <a name="analyze-code-maps"></a>Analisar mapas de código

Na barra de ferramentas do mapa , escolha  >  **analisadores** de layout e, em seguida, o analisador que você deseja executar:

|**Analyz**|**Para identificar os nós que**|
|-|-|
|**Analisador de referências circulares**|Ter dependências circulares entre si. **Observação:**  As dependências circulares que estão no grupo **genéricos** não são mostradas no mapa quando você expande o grupo.|
|**Localizar analisador de hubs**|Estão nos 25% principais de nós altamente conectados<br /><br /> **Para ocultar todos os outros nós no mapa**<br /><br /> -Abra o menu de atalho para o mapa, escolha **avançado**, **selecionar**, **ocultar não selecionado**.<br />     O mapa oculta os nós não selecionados e o analisador identifica novos nós como hubs.|
|**Analisador de nós não referenciados**|Não há referências de nenhum outro nó. **Cuidado:**  Verifique cada um desses casos antes de presumir que o código não seja usado. Determinadas dependências, como dependências XAML e dependências em tempo de execução, não podem ser encontradas estaticamente no código.|

Os analisadores de mapa de código continuarão a ser executados depois que você os aplicar. Se você alterar o mapa, todos os analisadores aplicados reprocessarão automaticamente o mapa atualizado. Para interromper a execução de um analisador, na barra de ferramentas do mapa, escolha  >  **analisadores** de layout. Desative o analisador selecionado.

> [!TIP]
> Se você tiver um mapa muito grande, a execução de um analisador poderá causar uma exceção de memória insuficiente. Se isso ocorrer, edite o mapa para reduzir seu escopo ou gere um menor e, em seguida, execute o analisador.

## <a name="see-also"></a>Confira também

- [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)
- [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
