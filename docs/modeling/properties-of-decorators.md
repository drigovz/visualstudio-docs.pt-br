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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e29dcda43fdbb7b60567ff0aa0627b41ca3ca299
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873782"
---
# <a name="properties-of-decorators"></a>Propriedades de decoradores
Os decoradores são ícones, texto ou divisas de expandir/recolher que podem aparecer em formas ou conectores no diagrama. As tabelas a seguir mostram as propriedades para os três tipos de decorador. Algumas das propriedades aparecem apenas em decoradores de forma ou somente em decoradores de conector.

 Para obter mais informações, consulte [como definir um idioma de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Para obter mais informações sobre como usar essas propriedades, consulte [Personalizando e estendendo uma linguagem de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Expandir/recolher decorador

|Propriedade|Descrição|Padrão|
|-|-|-|
|DisplayName|O nome do decorador que será exibido no designer gerado.|Expandir recolher decorador|
|Nome|O nome do decorador.|ExpandCollapseDecorator|
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
|Nome|O nome do decorador.|IconDecorator|
|Observações|Observações informais que estão associadas ao decorador.|\<none>|
|As|O deslocamento horizontal, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|VerticalOffset|O deslocamento vertical, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|OffsetFromShape|O deslocamento do decorador a partir da forma, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|Posição|A posição padrão do decorador.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Propriedade|Descrição|Padrão|
|-|-|-|
|DefaultText|O texto padrão a ser exibido.|Rótulo|
|DisplayName|O nome do decorador a ser exibido no designer gerado.|Rótulo|
|FontSize|O tamanho da fonte para o texto que é exibido no decorador.|8|
|FontStyle|O estilo da fonte para o texto que é exibido no decorador.|Regular|
|Nome|O nome do decorador.|Rótulo|
|Observações|Observações informais que estão associadas ao decorador.|\<none>|
|As|O deslocamento horizontal, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|VerticalOffset|O deslocamento vertical, em relação à posição padrão do decorador, em polegadas. (Somente nas formas.)|0|
|OffsetFromLine|O deslocamento do decorador da linha, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|OffsetFromShape|O deslocamento do decorador a partir da forma, em relação à sua posição padrão, em polegadas. (Somente em conectores.)|0|
|Posição|A posição padrão do decorador.|TargetBottom|

## <a name="see-also"></a>Confira também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](/previous-versions/bb126564(v=vs.100))