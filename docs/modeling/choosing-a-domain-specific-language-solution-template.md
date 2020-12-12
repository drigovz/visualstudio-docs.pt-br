---
title: Escolhendo um modelo de solução de linguagem específica do domínio
description: Saiba como criar uma solução de linguagem específica de domínio escolhendo um dos modelos de solução que estão disponíveis no assistente do Domain-Specific Language designer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2e0c96c93e3583a7d2877a5f4f7bd70561b650b
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363530"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Escolhendo um modelo de solução de linguagem específica do domínio
Para criar uma solução de linguagem específica de domínio, escolha um dos modelos de solução que estão disponíveis no assistente do Domain-Specific Language designer. Ao escolher o modelo que mais se assemelha ao idioma que você deseja criar, você pode minimizar as modificações que precisa fazer na solução inicial.

 Os modelos de solução a seguir estão disponíveis no assistente do Domain-Specific Language designer.

|Modelo|Recursos|Descrição|
|-|-|-|
|Diagramas de classe|-Formas de compartimento<br />-Herança de classe<br />-Herança de relação<br />-Herança de forma<br />-Propriedades da relação|Use este modelo de solução se a linguagem específica do domínio incluir entidades e relações que tenham Propriedades. Este modelo cria uma linguagem específica de domínio que se assemelha a diagramas de classe UML. As entidades principais são classes e interfaces, juntamente com relações de associação, generalização e implementação. Uma classe ou interface aparece como uma caixa que contém uma lista de atributos.|
|Diagramas de componente|-Portas|Use este modelo de solução se a linguagem específica do domínio incluir componentes, ou seja, partes de um sistema de software. Este modelo cria uma linguagem específica de domínio que se assemelha a diagramas de componente UML. As entidades principais são componentes e portas, que aparecem como pequenas formas fora dos componentes.|
|Diagramas de fluxo de tarefas|-Formas de imagem e geometria<br />-   *Raias*|Use este modelo de solução se a linguagem específica do domínio incluir fluxos de trabalho, Estados ou sequências. Este modelo cria uma linguagem específica de domínio que se assemelha a diagramas de atividade UML. A entidade principal é uma atividade, e a relação principal é uma transição entre atividades. O modelo inclui vários outros elementos, como estado de início, estado final e uma barra de sincronização.|
|Linguagem mínima|-Uma classe e forma<br />-Uma relação e um conector|Use este modelo de solução se a linguagem específica do domínio não se assemelhar aos outros modelos. Este modelo cria uma linguagem específica de domínio que tem duas classes e uma relação, que são representadas na caixa de **ferramentas** como **Box** e **linha**. A classe e a relação têm, cada uma, uma propriedade de cadeia de caracteres de exemplo.|
|Designer do WinForm mínimo|-Um modelo pequeno.<br />-Um formulário do Windows que exibe o modelo.|Use este modelo se desejar criar um aplicativo no qual uma DSL está associada a um formulário do Windows, em vez de um designer gráfico.<br /><br /> O formulário que atua como a interface do usuário para o idioma está na pasta Dsl\UI.<br /><br /> Você deve compilar o projeto antes de abrir o designer de formulário.<br /><br /> Para obter mais informações, consulte [criando uma linguagem de Domain-Specific de Forms-Based do Windows](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Designer de WPF mínimo|-Um modelo pequeno<br />-Um Windows Presentation Foundation interface do usuário que exibe o modelo|Use este modelo se desejar criar um aplicativo no qual uma DSL está associada a uma interface do usuário do WPF, em vez de um designer gráfico.<br /><br /> O designer da interface do usuário está na pasta Dsl\UI.<br /><br /> Você deve compilar o projeto antes de abrir o designer de interface do usuário.<br /><br /> Para obter mais informações, consulte [criando uma linguagem de Domain-Specific de WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Biblioteca de DSL|-Uma biblioteca mínima|Use este modelo se desejar criar uma definição de DSL parcial que possa ser importada para outras definições de DSL.|

## <a name="see-also"></a>Veja também

- [Visão geral das Ferramentas de Linguagem Específica do Domínio](../modeling/overview-of-domain-specific-language-tools.md)
