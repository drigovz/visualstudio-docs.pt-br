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
ms.openlocfilehash: 227c2871f68545c9f9fe5fa1ea3ceee827ccdc6a
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917301"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>SDK das edições do Visual Studio para visualização &amp; modelagem com suporte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Seguem listas das edições do Visual Studio que têm suporte com [!INCLUDE[dsl](../includes/dsl-md.md)] nos ambientes de criação e implantação. Para obter mais informações sobre essas edições, consulte o [centro de desenvolvedores](https://msdn.microsoft.com/vstudio/products/)do Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="authoring-edition"></a>Edição de Criação
 Para definir uma DSL, é necessário ter instalados os seguintes componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[SDK do Visual Studio](../extensibility/visual-studio-sdk.md)|
|{1&gt;{2&gt;SDK de Visualização e Modelagem do Visual Studio&lt;2}&lt;1}|[Download do SDK de modelagem](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>Edições de Implantação
 [!INCLUDE[dsl](../includes/dsl-md.md)] oferece suporte às seguintes configurações para implantação das linguagens específicas do domínio que foram compiladas:

- Visual Studio Enterprise

- Visual Studio Professional

- Pacote redistribuível do Visual Studio Shell (modo integrado) pacote redistribuível

- Pacote redistribuível Visual Studio Shell (modo isolado) pacote redistribuível

> [!NOTE]
> Para tornar uma DSL capaz de executar em um produto Shell, você deve definir a **suporte para a edição do VS** campo no manifesto de extensão. Para obter mais informações, confira [Implantando soluções de linguagem específica de domínio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Veja também
 [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
