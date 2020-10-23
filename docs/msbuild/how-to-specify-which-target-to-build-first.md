---
title: Como especificar o destino a ser compilado primeiro | Microsoft Docs
description: Saiba mais sobre como especificar destinos iniciais ou destinos padrão para compilar primeiro em arquivos de projeto do MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9ce8f17e70344445f95e8b4742838e40a92fe88
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436184"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Como especificar o destino a ser compilado primeiro

Um arquivo de projeto pode conter um ou mais elementos `Target` que definem como o projeto é compilado. O mecanismo de Microsoft Build Engine (MSBuild) cria o primeiro destino encontrado e quaisquer dependências, a menos que o arquivo de projeto contenha um `DefaultTargets` atributo, um `InitialTargets` atributo ou um destino seja especificado na linha de comando usando a opção **-target** .
## <a name="use-the-initialtargets-attribute"></a>Usar o atributo InitialTargets

O atributo `InitialTargets` do elemento `Project` especifica um destino que será executado primeiro, mesmo se os destinos forem especificados na linha de comando ou no atributo `DefaultTargets`.

#### <a name="to-specify-one-initial-target"></a>Para especificar um destino inicial

- Especifique o destino padrão no atributo `InitialTargets` do elemento `Project`. Por exemplo:

   `<Project InitialTargets="Clean">`

  Você pode especificar mais de um destino inicial no atributo `InitialTargets` ao listar os destinos em ordem e usar um ponto e vírgula para separar cada destino. Os destinos na lista serão executados sequencialmente.

#### <a name="to-specify-more-than-one-initial-target"></a>Para especificar mais de um destino inicial

- Liste os destinos iniciais, separados por ponto e vírgula, no atributo `InitialTargets` do elemento `Project`. Por exemplo, para executar o destino `Clean` e, em seguida, o destino `Compile`, digite:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Usar o atributo DefaultTargets

 O atributo `DefaultTargets` do elemento `Project` especifica qual destino ou quais destinos serão compilados se um destino não for especificado explicitamente na linha de comando. Se os destinos forem especificados nos `InitialTargets` atributos e `DefaultTargets` e nenhum destino for especificado na linha de comando, o MSBuild executará os destinos especificados no `InitialTargets` atributo seguido pelos destinos especificados no `DefaultTargets` atributo.

#### <a name="to-specify-one-default-target"></a>Para especificar um destino padrão

- Especifique o destino padrão no atributo `DefaultTargets` do elemento `Project`. Por exemplo:

   `<Project DefaultTargets="Compile">`

  Você pode especificar mais de um destino padrão no atributo `DefaultTargets` ao listar os destinos em ordem e usar um ponto e vírgula para separar cada destino. Os destinos na lista serão executados sequencialmente.

#### <a name="to-specify-more-than-one-default-target"></a>Para especificar mais de um destino padrão

- Liste os destinos padrão, separados por ponto e vírgula, no atributo `DefaultTargets` do elemento `Project`. Por exemplo, para executar o destino `Clean` e, em seguida, o destino `Compile`, digite:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Usar a opção -target

 Se um destino padrão não estiver definido no arquivo de projeto ou se você não quiser usar esse destino padrão, poderá usar a opção de linha de comando **-target** para especificar um destino diferente. O destino ou destinos especificados com a opção **-target** são executados em vez dos destinos especificados pelo `DefaultTargets` atributo. Os destinos especificados no atributo `InitialTargets` são sempre executados primeiro.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Para usar primeiro um destino diferente do destino padrão

- Especifique o destino como o primeiro destino usando a opção de linha de comando **-target** . Por exemplo:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Para usar primeiro vários destinos que sejam diferentes dos destinos padrão

- Liste os destinos, separados por ponto e vírgula, usando a opção de linha de comando **-target** . Por exemplo:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Confira também

- [MSBuild](../msbuild/msbuild.md)
- [Destinos](../msbuild/msbuild-targets.md)
- [Como limpar uma compilação](../msbuild/how-to-clean-a-build.md)
