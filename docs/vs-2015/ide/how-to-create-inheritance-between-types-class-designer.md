---
title: Como criar herança entre tipos (Designer de Classe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba27b32cc322da2e14cec86b878a7dd42dae0039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668101"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Como criar herança entre tipos (Designer de Classe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para criar uma relação de herança entre dois tipos em um diagrama de classes usando o Designer de Classe, conecte o tipo de base ao seu tipo ou tipos derivados. Você pode ter uma relação de herança entre duas classes, entre uma classe e uma interface ou entre duas interfaces.

### <a name="to-create-an-inheritance-between-types"></a>Para criar uma herança entre tipos

1. No seu projeto localizado no Gerenciador de Soluções, abra um arquivo de diagrama de classes (.cd).

     Se você não possuir um diagrama de classes, crie um. Consulte [Como adicionar diagramas de classe a projetos (Designer de Classe)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

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

## <a name="see-also"></a>Consulte Também
 [Inheritance](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea) [Noções básicas de herança](https://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5) [de herança como exibir a herança entre tipos (Designer de Classe)](../ide/how-to-view-inheritance-between-types-class-designer.md) [Visual C++ classes no designer de classe](../ide/visual-cpp-classes-in-class-designer.md)
