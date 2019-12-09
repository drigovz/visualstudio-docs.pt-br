---
title: Edições do Visual Studio com suporte para visualização e SDK de modelagem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b81aaba14acc2c050a770e810c57e99ee43c2ab3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298156"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>SDK das edições do Visual Studio para visualização &amp; modelagem com suporte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A seguir estão as listas das edições do Visual Studio com suporte com [!INCLUDE[dsl](../includes/dsl-md.md)] nos ambientes de criação e implantação. Para obter mais informações sobre essas edições, consulte o [centro de desenvolvedores](https://go.microsoft.com/fwlink/?LinkId=75628)do Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="authoring-edition"></a>Edição de Criação
 Para definir uma DSL, é necessário ter instalados os seguintes componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|SDK do Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|SDK de Visualização e Modelagem do Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

## <a name="deployment-editions"></a>Edições de Implantação
 o [!INCLUDE[dsl](../includes/dsl-md.md)] dá suporte às seguintes configurações para implantar as linguagens específicas de domínio que você cria:

- Visual Studio Enterprise

- Visual Studio Professional

- Pacote redistribuível do Visual Studio Shell (modo integrado) pacote redistribuível

- Pacote redistribuível Visual Studio Shell (modo isolado) pacote redistribuível

> [!NOTE]
> Para tornar uma DSL capaz de executar em um produto de Shell, você deve definir o campo **com suporte do vs Edition** no manifesto de extensão. Para obter mais informações, confira [Implantando soluções de linguagem específica de domínio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Consulte também
 [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
