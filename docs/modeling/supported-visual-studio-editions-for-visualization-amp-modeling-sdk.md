---
title: Edições do Visual Studio com suporte para o SDK de visualização e modelagem
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efe452f059d7184e1f7c87fddd6bdc6c213ece8a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983726"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Edições do Visual Studio compatíveis com o SDK de Visualização e Modelagem

A seguir estão as listas das edições do Visual Studio com suporte com [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] nos ambientes de criação e implantação. Para obter mais informações sobre essas edições, consulte o Microsoft Visual Studio [Developer Center](https://visualstudio.microsoft.com/).

## <a name="authoring-edition"></a>Edição de Criação

Para definir uma DSL, é necessário ter instalados os seguintes componentes:

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|SDK do Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|SDK de Visualização e Modelagem do Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edições de Implantação

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] oferece suporte às seguintes configurações para implantação das linguagens específicas do domínio que foram compiladas:

- Visual Studio Enterprise

- Visual Studio Professional

- Pacote redistribuível do pacote redistribuível do shell do Visual Studio (modo integrado)

- Pacote redistribuível Visual Studio Shell (modo isolado) pacote redistribuível

> [!NOTE]
> Para tornar uma DSL capaz de executar em um produto de Shell, você deve definir o campo **com suporte do vs Edition** no manifesto de extensão. Para obter mais informações, confira [Implantando soluções de linguagem específica de domínio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Consulte também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)