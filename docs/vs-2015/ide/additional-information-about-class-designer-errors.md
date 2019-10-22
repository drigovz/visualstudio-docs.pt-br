---
title: Informações adicionais sobre erros do Designer de Classe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7500782a1d935c08ae95e26764c9476c63f36660
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620386"
---
# <a name="additional-information-about-class-designer-errors"></a>Informações adicionais sobre erros do Designer de Classe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Designer de Classe não controla o local dos arquivos de origem, de forma que modificar a estrutura do projeto ou mover os arquivos de origem no projeto pode fazer com que o Designer de Classe perca o controle do tipo (especialmente o tipo de origem de um typedef, classes base ou tipos de associação). É possível receber um erro como **O Designer de Classe não pode exibir este tipo**. Se você fizer isso, arraste o código-fonte realocado ou modificado para o diagrama de classe, para exibi-lo novamente.

 Você pode obter ajuda com outros erros e avisos nos seguintes recursos:

 [Trabalhar com código C++ Visual (Designer de classe)](../ide/working-with-visual-cpp-code-class-designer.md) inclui informações de solução de problemas C++ sobre como exibir em um diagrama de classe.

 O [Fórum do Designer de Classe do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160754) fornece um fórum para perguntas sobre o Designer de Classe.

## <a name="see-also"></a>Veja também
 [Projetando e exibindo classes e tipos](../ide/designing-and-viewing-classes-and-types.md)
