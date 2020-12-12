---
title: Propriedades de decoradores
description: Saiba que os decoradores são ícones, texto ou divisas de expandir/recolher que podem aparecer em formas ou conectores no diagrama.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef863d0d3dab394c2ca427a27d039c19e5921a51
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360827"
---
# <a name="properties-of-decorators"></a>Propriedades de decoradores
Os decoradores são ícones, texto ou divisas de expandir/recolher que podem aparecer em formas ou conectores no diagrama. As tabelas a seguir mostram as propriedades para os três tipos de decorador. Algumas das propriedades aparecem apenas em decoradores de forma ou somente em decoradores de conector.

 Para obter mais informações, consulte [como definir um idioma de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Expandir/recolher decorador

|Propriedade|Descrição|Padrão|
|-|-|-|
|DisplayName|O nome do decorador que será exibido no designer gerado.|Expandir recolher decorador|
|Name|O nome do decorador.|ExpandCollapseDecorator|
|Observações|Observações informais que estão associadas a este decorador.|\<none>|
|As|O deslocamento horizontal, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|VerticalOffset|O deslocamento vertical, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|OffsetFromShape|O deslocamento do decorador a partir da forma, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|Posição|A posição padrão do decorador.|SourceTop|

## <a name="icon-decorator"></a>Decorador de ícone

|Propriedade|Descrição|Padrão|
|-|-|-|
|DefaultIcon|O caminho do arquivo de ícone ou de imagem a ser exibido.|\<none>|
|DisplayName|O nome do decorador a ser exibido no designer gerado.|Decorador de ícone|
|Name|O nome do decorador.|IconDecorator|
|Observações|Observações informais que estão associadas ao decorador.|\<none>|
|As|O deslocamento horizontal, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|VerticalOffset|O deslocamento vertical, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|OffsetFromShape|O deslocamento do decorador a partir da forma, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|Posição|A posição padrão do decorador.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Propriedade|Descrição|Padrão|
|-|-|-|
|DefaultText|O texto padrão a ser exibido.|Rotular|
|DisplayName|O nome do decorador a ser exibido no designer gerado.|Rotular|
|FontSize|O tamanho da fonte para o texto que é exibido no decorador.|8|
|FontStyle|O estilo da fonte para o texto que é exibido no decorador.|Regular|
|Name|O nome do decorador.|Rotular|
|Observações|Observações informais que estão associadas ao decorador.|\<none>|
|As|O deslocamento horizontal, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|VerticalOffset|O deslocamento vertical, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|OffsetFromShape|O deslocamento do decorador a partir da forma, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|Posição|A posição padrão do decorador.|TargetBottom|

## <a name="see-also"></a>Veja também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](/previous-versions/bb126564(v=vs.100))