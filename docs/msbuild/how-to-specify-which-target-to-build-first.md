---
title: Como especificar o destino a ser compilado primeiro | Microsoft Docs
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
ms.openlocfilehash: e008e3181cd7c633179f35e7639265a2495fafe2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633792"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Como especificar o destino a ser compilado primeiro

Um arquivo de projeto pode conter um ou mais elementos `Target` que definem como o projeto é compilado. O mecanismo Microsoft Build Engine (MSBuild) constrói o primeiro projeto encontrado e quaisquer `DefaultTargets` dependências, a menos que o arquivo do projeto contenha um atributo, um `InitialTargets` atributo ou um alvo seja especificado na linha de comando usando o switch de **destino.**
## <a name="use-the-initialtargets-attribute"></a>Usar o atributo InitialTargets

 O atributo `InitialTargets` do elemento `Project` especifica um destino que será executado primeiro, mesmo se os destinos forem especificados na linha de comando ou no atributo `DefaultTargets`.
O atributo `InitialTargets` do elemento `Project` especifica um destino que será executado primeiro, mesmo se os destinos forem especificados na linha de comando ou no atributo `DefaultTargets`.

#### <a name="to-specify-one-initial-target"></a>Para especificar um destino inicial

- Especifique o destino padrão no atributo `InitialTargets` do elemento `Project`. Por exemplo: 

   `<Project InitialTargets="Clean">`

  Você pode especificar mais de um destino inicial no atributo `InitialTargets` ao listar os destinos em ordem e usar um ponto e vírgula para separar cada destino. Os destinos na lista serão executados sequencialmente.

#### <a name="to-specify-more-than-one-initial-target"></a>Para especificar mais de um destino inicial

- Liste os destinos iniciais, separados por ponto e vírgula, no atributo `InitialTargets` do elemento `Project`. Por exemplo, para executar o destino `Clean` e, em seguida, o destino `Compile`, digite:

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Usar o atributo DefaultTargets

 O atributo `DefaultTargets` do elemento `Project` especifica qual destino ou quais destinos serão compilados se um destino não for especificado explicitamente na linha de comando. Se os alvos forem `InitialTargets` especificados tanto nos atributos quanto `DefaultTargets` nos atributos e nenhum destino `InitialTargets` for especificado na linha de `DefaultTargets` comando, o MSBuild será executado os alvos especificados no atributo seguido pelos alvos especificados no atributo.

#### <a name="to-specify-one-default-target"></a>Para especificar um destino padrão

- Especifique o destino padrão no atributo `DefaultTargets` do elemento `Project`. Por exemplo: 

   `<Project DefaultTargets="Compile">`

  Você pode especificar mais de um destino padrão no atributo `DefaultTargets` ao listar os destinos em ordem e usar um ponto e vírgula para separar cada destino. Os destinos na lista serão executados sequencialmente.

#### <a name="to-specify-more-than-one-default-target"></a>Para especificar mais de um destino padrão

- Liste os destinos padrão, separados por ponto e vírgula, no atributo `DefaultTargets` do elemento `Project`. Por exemplo, para executar o destino `Clean` e, em seguida, o destino `Compile`, digite:

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Usar a opção -target

 Se um destino padrão não for definido no arquivo do projeto ou se você não quiser usar esse destino padrão, você pode usar o **destino do** switch de linha de comando para especificar um alvo diferente. Os alvos ou alvos especificados com o switch **-target** são executados em vez dos alvos especificados pelo atributo. `DefaultTargets` Os destinos especificados no atributo `InitialTargets` são sempre executados primeiro.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Para usar primeiro um destino diferente do destino padrão

- Especifique o alvo como o primeiro alvo usando o interruptor de linha de comando **-target.** Por exemplo: 

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Para usar primeiro vários destinos que sejam diferentes dos destinos padrão

- Liste os alvos, separados por ponto e vírgula ou vírgulas, usando o interruptor de linha de comando **-target.** Por exemplo: 

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Confira também

- [MSBuild](../msbuild/msbuild.md)
- [Destinos](../msbuild/msbuild-targets.md)
- [Como: Limpar uma compilação](../msbuild/how-to-clean-a-build.md)
