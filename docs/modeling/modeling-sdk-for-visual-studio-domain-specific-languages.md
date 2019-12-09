---
title: SDK de Modelagem para Visual Studio - linguagens específicas ao domínio
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9e58de3737acaae01939eb2e29242e02888235d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658391"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>SDK de Modelagem para Visual Studio - linguagens específicas ao domínio

Usando o SDK de modelagem para o Visual Studio, você pode criar poderosas ferramentas de desenvolvimento com base em modelos que podem ser integradas ao Visual Studio. Da mesma forma, você pode criar uma ou mais definições de modelo e integrá-las em um conjunto de ferramentas.

No centro do MSDK está a definição de um modelo que você cria para representar conceitos em sua área de negócios. Você pode colocar o modelo com uma variedade de ferramentas, como uma exibição diagramáticas, a capacidade de gerar código e outros artefatos, comandos para transformar o modelo e a capacidade de interagir com código e outros objetos no Visual Studio. À medida que o modelo é desenvolvido, você pode combiná-lo com outros modelos e ferramentas para formar um conjunto de ferramentas avançadas centradas em seu desenvolvimento.

O MSDK permite desenvolver rapidamente um modelo na forma de uma linguagem específica do domínio (DSL). Você começa ao usar um editor especializado para definir um esquema ou sintaxe abstrata junto com uma notação gráfica. Dessa definição, o VMSDK gera:

- Uma implementação de modelo com uma API fortemente tipada executada em um repositório baseado em transação.

- Um gerenciador baseado em árvore.

- Um editor gráfico no qual os usuários podem exibir o modelo ou partes dele que você definir.

- Métodos de serialização que salvam seus modelos em XML legível.

- Recursos para gerar código de programa e outros artefatos usando modelagem de texto.

Você pode personalizar e estender todos esses recursos. Suas extensões são integradas de tal forma que você ainda pode atualizar a definição de DSL e gerar novamente os recursos sem perder suas extensões.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Postagens de blog relacionadas](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)