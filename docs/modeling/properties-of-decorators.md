---
title: Propriedades de decoradores
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3374c07cac01104354b2ce41abddbeabbec0a373
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75566131"
---
# <a name="properties-of-decorators"></a>Propriedades de decoradores
Os decoradores são ícones, texto ou divisas de expandir/recolher que podem aparecer em formas ou conectores no diagrama. As tabelas a seguir mostram as propriedades para os três tipos de decorador. Algumas das propriedades aparecem apenas em decoradores de forma ou somente em decoradores de conector.

 Para obter mais informações, consulte [como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem específica de domínio](../modeling/customizing-and-extending-a-domain-specific-language.md).

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

## <a name="see-also"></a>Confira também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
