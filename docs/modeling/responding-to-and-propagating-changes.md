---
title: Respondendo a alterações e propagando-as
description: Saiba que, quando um elemento é criado, excluído ou atualizado, você pode escrever um código que propaga a alteração para outras partes do modelo ou para recursos externos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a6066a40ea09698bec6caba38d5d55aa8b269e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937934"
---
# <a name="respond-to-and-propagate-changes"></a>Responder e propagar alterações

Quando um elemento é criado, excluído ou atualizado, você pode escrever um código que propaga a alteração para outras partes do modelo ou para recursos externos, como arquivos, bancos de dados ou outros componentes.

## <a name="reference"></a>Referência

Como diretriz, considere estas técnicas na seguinte ordem:

|Técnica|Cenários|Para obter mais informações|
|-|-|-|
|Defina uma propriedade de domínio calculada.|Uma propriedade de domínio cujo valor é calculado de outras propriedades no modelo. Por exemplo, um preço que é a soma dos preços dos elementos relacionados.|[Propriedades calculadas e de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Defina uma propriedade de domínio de armazenamento personalizada.|Uma propriedade de domínio armazenada em outras partes do modelo ou externamente. Por exemplo, você pode analisar uma cadeia de caracteres de expressão em uma árvore no modelo.|[Propriedades calculadas e de armazenamento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Substituir manipuladores de alteração, como OnValueChanging e OnDelete|Mantenha diferentes elementos em sincronia e mantenha os valores externos em sincronia com o modelo.<br /><br /> Restringir valores a intervalos definidos.<br /><br /> Chamado imediatamente antes e depois do valor da propriedade e outras alterações. Você pode encerrar a alteração lançando uma exceção.|[Manipuladores de alterações nos valores da propriedade de domínio](../modeling/domain-property-value-change-handlers.md)|
|Regras|Você pode definir regras que são enfileiradas para execução logo antes do final de uma transação na qual ocorreu uma alteração. Eles não são executados em desfazer ou refazer. Use-os para manter uma parte da loja em sincronia com outra.|[Regras propagam alterações dentro do modelo](../modeling/rules-propagate-changes-within-the-model.md)|
|Armazenar eventos|O repositório de modelagem fornece notificações de eventos como adicionar ou excluir um elemento ou link ou alterar o valor de uma propriedade. O evento também é executado em desfazer e refazer. Use armazenar eventos para atualizar valores que não estão no repositório.|[Manipuladores de eventos propagam alterações fora do modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Eventos .NET|As formas têm manipuladores de eventos que respondem a cliques do mouse e a outros gestos. Você precisa se registrar para esses eventos para cada objeto. Normalmente, o registro é feito em uma substituição de InitializeInstanceResources e deve ser feito para cada elemento.<br /><br /> Esses eventos geralmente ocorrem fora de uma transação.|[Como interceptar um clique em uma forma ou um decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Regras de limites|Uma regra de limites é usada especificamente para restringir os limites de uma forma.|[BoundsRules restringem o local e o tamanho de uma forma](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|Regras de seleção|As regras de seleção restringem especificamente o que o usuário pode selecionar.|[Como acessar e restringir a seleção atual](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Indique os Estados dos elementos do modelo usando recursos de formas e conectores, como sombra, pontas de seta, cor e larguras de linha e estilo.|[Atualizando formas e conectores para refletir o modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Comparar regras e armazenar eventos

Os notificadores, as regras e os eventos de alteração são executados quando ocorrem alterações em um modelo.

Normalmente, as regras são aplicadas na transação final em que a alteração ocorreu e os eventos são aplicados depois que as alterações em uma transação são confirmadas.

Use armazenar eventos para sincronizar o modelo com objetos fora da loja e regras para manter a consistência dentro da loja.

- **Criando regras personalizadas** Você cria uma regra personalizada como uma classe derivada de uma regra abstrata. Você também deve notificar a estrutura sobre a regra personalizada. Para obter mais informações, consulte [regras propagar alterações no modelo](../modeling/rules-propagate-changes-within-the-model.md).

- **Inscrevendo-se em eventos** Antes de poder assinar um evento, crie um manipulador de eventos e um delegado. Em seguida, use a <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> propriedade para assinar o evento. Para obter mais informações, consulte [manipuladores de eventos propagar alterações fora do modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Desfazendo alterações** Quando você desfaz uma transação, os eventos são gerados, mas as regras não são aplicadas. Se uma regra alterar um valor e você desfazer essa alteração, o valor será redefinido para o valor original durante a ação de desfazer. Quando um evento é gerado, você deve alterar manualmente o valor de volta para seu valor original. Para saber mais sobre transações e desfazer, consulte [como: usar transações para atualizar o modelo](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Passando argumentos de evento para regras e eventos** Os eventos e as regras passam um `EventArgs` parâmetro que tem informações sobre como o modelo foi alterado.

## <a name="see-also"></a>Confira também

- [Como interceptar um clique em uma forma ou um decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Escrevendo código para personalizar um idioma Domain-Specific](../modeling/writing-code-to-customise-a-domain-specific-language.md)