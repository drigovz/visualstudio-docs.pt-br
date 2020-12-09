---
title: Criar herança entre tipos
description: Saiba como criar uma relação de herança entre dois tipos em um diagrama de classe usando Designer de Classe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 064ae443c264187e7666b7aaabde27d6705388a4
ms.sourcegitcommit: 60e5a8a7ee91854356797d05f3b502572c4a4884
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933473"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Como criar herança entre tipos no Designer de Classe

Para criar uma relação de herança entre dois tipos em um diagrama de classe usando **Designer de classe**, conecte o tipo base com seu tipo ou tipos derivados. Você pode ter uma relação de herança entre duas classes, entre uma classe e uma interface ou entre duas interfaces.

## <a name="to-create-an-inheritance-between-types"></a>Para criar uma herança entre tipos

1. Em seu projeto no **Gerenciador de soluções**, abra um arquivo de diagrama de classe (. CD).

     Se você não possuir um diagrama de classes, crie um. Consulte [como: Adicionar diagramas de classe a projetos](how-to-add-class-diagrams-to-projects.md).

2. Na **Caixa de Ferramentas**, no **Designer de Classe**, clique em **Herança**.

3. No diagrama de classes, desenhe uma linha de herança entre os tipos que você deseja, começando de:

    - Uma classe derivada para uma classe base

    - Uma classe de implementação para uma interface implementada

    - Uma interface em extensão para uma interface estendida

4. Se desejar, quando você tiver um tipo derivado de um tipo genérico, clique na linha de herança. Na janela **Propriedades**, defina a propriedade **Argumentos de Tipo** para corresponder ao tipo que você deseja para o tipo genérico.

    > [!NOTE]
    > Se uma classe abstrata pai contiver pelo menos um membro abstrato, todos os membros abstratos serão implementados como classes de herança não abstratas.
    >
    >  Embora você possa visualizar os tipos genéricos existentes, não é possível criar novos tipos genéricos. Você também não pode alterar os parâmetros de tipos genéricos existentes.

## <a name="see-also"></a>Confira também

- [Herança](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Como exibir herança entre tipos](how-to-view-inheritance-between-types.md)
- [Classes do Visual C++ no Designer de Classe](visual-cpp-classes.md)
