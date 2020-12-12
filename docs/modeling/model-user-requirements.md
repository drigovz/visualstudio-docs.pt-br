---
title: Requisitos de usuário do modelo
description: Saiba como o Visual Studio ajuda você a entender, discutir e comunicar as necessidades dos usuários por meio de diagramas de desenho sobre suas atividades.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40418b2d188ac5482a12dd4ffdddd221bf5d2f97
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361957"
---
# <a name="model-user-requirements"></a>Requisitos de usuário do modelo

O Visual Studio ajuda você a entender, discutir e comunicar as necessidades dos usuários desenhando diagramas sobre suas atividades e a parte que seu sistema desempenha para ajudá-los a atingir suas metas. Um modelo de requisitos é um conjunto desses diagramas, cada um deles concentra-se em um aspecto diferente das necessidades dos usuários. Para ver uma demonstração em vídeo, consulte: [modelando o domínio de negócios](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain).

Para ver quais versões do Visual Studio oferecem suporte a cada tipo de modelo, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Um modelo de requisitos ajuda você a:

- Concentre-se no comportamento externo do sistema, separadamente de seu design interno.

- Descreva as necessidades dos usuários e dos participantes com muito menos ambigüidade do que você pode em linguagem natural.

- Defina um glossário consistente de termos que podem ser usados por usuários, desenvolvedores e testadores.

- Reduza lacunas e inconsistências nos requisitos.

- Reduza o trabalho necessário para responder às alterações de requisitos.

- Planeje a ordem na qual os recursos serão desenvolvidos.

- Use os modelos como base para testes do sistema, fazendo uma relação clara entre os testes e os requisitos. Quando os requisitos mudam, essa relação ajuda a atualizar os testes corretamente. Isso garante que o sistema atenda aos novos requisitos.

Um modelo de requisitos fornece maior benefício se você usá-lo para enfocar discussões com os usuários ou seus representantes e revisitá-lo no início de cada iteração. Você não precisa concluí-lo detalhadamente antes de escrever código. Um aplicativo parcialmente funcional, mesmo que seja muito simplificado, geralmente forma a base mais stimulating para a discussão dos requisitos com os usuários. O modelo é uma maneira eficaz de resumir os resultados dessas discussões. Para obter mais informações, consulte [usar modelos em seu processo de desenvolvimento](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> Durante esses tópicos, "System" significa o sistema ou o aplicativo que você está desenvolvendo. Pode ser uma grande coleção de muitos componentes de software e hardware; ou um único aplicativo; ou um componente de software dentro de um sistema maior. Em todos os casos, o modelo de requisitos descreve o comportamento que é visível de fora do seu sistema, seja por meio de uma interface de usuário ou API.

## <a name="common-tasks"></a>Tarefas comuns

Você pode criar várias exibições diferentes dos requisitos dos usuários.  Cada exibição fornece um tipo específico de informação.  Quando você cria essas exibições, é melhor movê-las com frequência de uma para outra. Você pode iniciar em qualquer modo de exibição.

|Diagrama ou documento|O que ele descreve em um modelo de requisitos|Seção|
|-|-|-|
|Diagrama de classe conceitual|Glossário de tipos que são usados para descrever os requisitos; os tipos visíveis na interface do sistema.||
|Documentos adicionais ou itens de trabalho|Critérios de desempenho, segurança, usabilidade e confiabilidade.|[Descrevendo os requisitos de qualidade de serviço](#QoSRequirements)|
|Documentos adicionais ou itens de trabalho|Restrições e regras não específicas de um caso de uso específico|[Mostrando regras de negócio](#BusinessRules)|

Observe que a maioria dos tipos de diagramas pode ser usada para outras finalidades. Para obter uma visão geral dos tipos de diagrama, consulte [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md).

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Mostrando regras de negócio

Uma regra de negócio é um requisito que não está associado a um caso de uso específico e deve ser observado em todo o sistema.

Muitas regras de negócio são restrições sobre as relações entre as classes conceituais. Você pode escrever essas *regras de negócio estáticos* como comentários associados às classes relevantes em um diagrama de classe conceitual. Por exemplo:

![Regra no comentário anexada à classe Order.](../modeling/media/uml_reqmcd2.png)

*As regras de negócio dinâmicas* restringem as sequências de eventos permitidas. Por exemplo, você usa um diagrama de sequência ou atividade para mostrar que um usuário deve fazer logon antes de executar outras operações em seu sistema.

No entanto, muitas regras dinâmicas podem ser mais eficientes e genericamente declaradas substituindo-as por regras estáticas. Por exemplo, você pode adicionar um atributo booliano "conectado" a uma classe no modelo de classe conceitual. Você adicionaria logon como a pré-condição do caso de uso de log e a adicionaria como uma pré-condição da maioria dos outros casos de uso. Essa abordagem permite evitar a definição de todas as combinações possíveis de sequências de eventos. Também é mais flexível quando você precisa adicionar novos casos de uso ao modelo.

Observe que a escolha aqui é sobre como você define os requisitos e que isso é independente de como você implementa os requisitos no código do programa.

Os tópicos a seguir fornecem mais informações:

|Para saber mais|Ler|
|-|-|
|Como desenvolver código que siga as regras de negócio|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Descrevendo os requisitos de qualidade de serviço

Há várias categorias de requisitos de qualidade de serviço. Eles incluem o seguinte:

- Desempenho

- Segurança

- Usabilidade

- Confiabilidade

- Robustez

Você pode incluir alguns desses requisitos nas descrições de casos de uso específicos. Outros requisitos não são específicos para casos de uso e são escritos com mais eficiência em um documento separado. Quando possível, é útil aderir ao vocabulário definido pelo modelo de requisitos. No exemplo a seguir, observe que as palavras principais usadas no requisito são os títulos de atores, casos de uso e classes nas ilustrações anteriores:

Se um restaurante excluir um item de menu enquanto um cliente estiver solicitando uma refeição, qualquer item de pedido que se refere a esse item de menu será exibido em vermelho.

Consulte [modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md) para saber como desenvolver código que atenda aos requisitos de qualidade de serviço.

## <a name="see-also"></a>Veja também

- [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)
- [Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)
