---
title: SDK de Modelagem para Visual Studio - linguagens específicas ao domínio
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b955dc6f79c689ca30d8d9876d0888b14127490
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476525"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>SDK de Modelagem para Visual Studio - linguagens específicas ao domínio

Usando o SDK de modelagem para Visual Studio, você pode criar ferramentas de desenvolvimento baseado em modelo avançadas que podem ser integradas ao Visual Studio. Da mesma forma, você pode criar uma ou mais definições de modelo e integrá-las em um conjunto de ferramentas.

No centro do MSDK está a definição de um modelo que você cria para representar conceitos em sua área de negócios. Você pode cercar o modelo com uma variedade de ferramentas, como uma exibição diagramática, a capacidade de gerar o código e outros artefatos, comandos para transformar o modelo e a capacidade de interagir com o código e outros objetos no Visual Studio. À medida que o modelo é desenvolvido, você pode combiná-lo com outros modelos e ferramentas para formar um conjunto de ferramentas avançadas centradas em seu desenvolvimento.

O MSDK permite desenvolver rapidamente um modelo na forma de uma linguagem específica do domínio (DSL). Você começa ao usar um editor especializado para definir um esquema ou sintaxe abstrata junto com uma notação gráfica. Dessa definição, o VMSDK gera:

- Uma implementação de modelo com uma API fortemente tipada executada em um repositório baseado em transação.

- Um gerenciador baseado em árvore.

- Um editor gráfico no qual os usuários podem exibir o modelo ou partes dele que você definir.

- Métodos de serialização que salvam seus modelos em XML legível.

- Recursos para gerar código de programa e outros artefatos usando modelagem de texto.

Você pode personalizar e estender todos esses recursos. Suas extensões são integradas de tal forma que você ainda pode atualizar a definição de DSL e gerar novamente os recursos sem perder suas extensões.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Postagens de blogs relacionadas](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)