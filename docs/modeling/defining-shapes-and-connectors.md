---
title: Definindo formas e conectores
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a24e447e5ec0b65635f7184bd0ae19b305edfdf8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068139"
---
# <a name="define-shapes-and-connectors"></a>Definir formas e conectores

Há diversos tipos básicos de formas possíveis de serem usados para exibir informações em um diagrama em uma linguagem específica do domínio (DSL).

## <a name="shapeTypes"></a> Tipos básicos de formas e conectores

Um diagrama DSL mostra uma coleção de *formas* interconectadas por linhas ou *conectores*. Geralmente, mas não sempre:

- As formas são representações visíveis dos elementos de modelo.

- Os conectores representam as relações de referência.

- O diagrama representa a instância da raiz do modelo.

- Relações de incorporações entre os elementos de modelo são mostradas por confinamento. Por exemplo, os elementos que representam portas de componentes são incorporados no componente.

Esses padrões não são impostos, mas têm melhor suporte. Quando você projetar uma DSL, tenha em mente que o design das relações de incorporação deve ser influenciado por como você deseja apresentar o modelo na tela. Por outro lado, as relações de referência devem refletir os conceitos de seu domínio dos negócios.

Os seguintes tipos de formas estão disponíveis:

|Tipo de forma|Descrição|
|-|-|
|Forma geométrica|Forma retangular ou elíptica de propósito geral. É possível exibir o texto e os decoradores de ícones em posições específicas relativas aos limites da forma. Você também pode aninhar formas dentro das formas geométricas.|
|Forma do compartimento|Retângulo contendo um cabeçalho e compartimentos, com uma classe UML. Cada compartimento pode conter uma lista de linhas de texto.<br /><br /> As linhas geralmente representam elementos incorporados sob o elemento representado pela forma. Por exemplo, criar uma DSL a partir de um modelo de solução de Diagramas de Classe.|
|Forma da imagem|Forma que exibe uma imagem.|
|Forma da porta|Um pequeno retângulo projetado para anexar o esboço de outra forma. Geralmente usado em modelos do componente.<br /><br /> O elemento de modelo representado por uma porta normalmente é incorporado sob o elemento representado pela forma pai. Por exemplo, criar uma DSL usando o modelo de solução de Componentes.<br /><br /> Por padrão, uma forma de porta pode deslizar ao longo das laterais de seu pai. É possível definir uma Regra de Associação para restringi-la a uma determinada posição.<br /><br /> Fazendo uma forma de porta muito pequena e transparente, é possível usá-la para fornecer um ponto de conexão fixo na superfície da sua forma pai.|
|Raias|Partição de raias de um diagrama em segmentos horizontais ou verticais. A raia sempre permanece abaixo de outras formas no diagrama.<br /><br /> Geralmente, os elementos de modelo da raia são criados na raiz do modelo e outros elementos são criados neles. Por exemplo, criar uma DSL a partir de um modelo de solução de Fluxo de Tarefa.|
|Conectores|As linhas desenhadas entre as formas normalmente representam relações de referência. É possível ajustar opções para tornar um conector reto ou retilíneo e para ter diferentes tipos de seta.|

## <a name="shape-inheritance"></a>Herança da forma

Uma forma pode ser herdeira de outra forma. No entanto, as formas devem ser do mesmo tipo. Por exemplo, somente uma forma geométrica pode ser herdeira de uma forma geométrica. Formas herdadas possuem os compartimentos e decoradores de sua forma de base. Os conectores podem ser herdeiros dos conectores.