---
title: Suporte para edições do Visual Studio para visualização e o SDK de modelagem
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 127b45ae6a0ab28d7f83ee41449d7846858ee4a9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591899"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>Edições do Visual Studio compatíveis com o SDK de Visualização e Modelagem

A seguir estão as listas das edições do Visual Studio com suporte com [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] nos ambientes de criação e implantação. Para obter mais informações sobre essas edições, consulte o Microsoft Visual Studio [Developer Center](https://visualstudio.microsoft.com/).

## <a name="authoring-edition"></a>Edição de Criação

Para definir uma DSL, é necessário ter instalados os seguintes componentes:

|||
|-|-|
|{1&gt;Visual Studio&lt;1}|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|SDK do Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|SDK de Visualização e Modelagem do Visual Studio|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Edições de Implantação

o [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] dá suporte às seguintes configurações para implantar as linguagens específicas de domínio que você cria:

- Visual Studio Enterprise

- Visual Studio Professional

- Pacote redistribuível do Visual Studio Shell (modo integrado) pacote redistribuível

- Pacote redistribuível Visual Studio Shell (modo isolado) pacote redistribuível

> [!NOTE]
> Para tornar uma DSL capaz de executar em um produto de Shell, você deve definir o campo **com suporte do vs Edition** no manifesto de extensão. Para obter mais informações, confira [Implantando soluções de linguagem específica de domínio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="see-also"></a>Consulte também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
