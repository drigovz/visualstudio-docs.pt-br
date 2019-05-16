---
title: Visão geral do modelo de automação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e17164976062ec916074c6210be6ae42e8ea1d03
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699498"
---
# <a name="automation-model-overview"></a>Visão geral do modelo de automação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O modelo de automação consiste em um conjunto de objetos em relação ao qual você pode gravar um suplemento do Visual Studio ou a extensão. Um suplemento é um aplicativo que pode manipular o ambiente do Visual Studio e automatizar tarefas comuns. Uma extensão do Visual Studio pode criar componentes personalizados do Visual Studio ou adicionar a funcionalidade dos componentes padrão, como o editor de texto.  
  
## <a name="objects-in-the-automation-model"></a>Objetos no modelo de automação  
 O modelo de automação consiste em grupos de objetos que controlam as principais facetas do ambiente comum. O exemplo a seguir é um diagrama que mostra o amplo conjunto de objetos que compõem o modelo de automação.  
  
 ![Gráfico de objeto de automação do Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Objetos de automação do Visual Studio  
  
 Para obter mais informações, consulte [estendendo o ambiente do Visual Studio](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 O ambiente fornece um modelo para diferentes áreas funcionais. Por exemplo, há um modelo de código para vários elementos que você pode encontrar no código. Há um modelo de documento para vários elementos de documento. Uma área, área de projeto, é de interesse específico a provedores de VSPackage. Você provavelmente desejará contribuir para o modelo de automação da mesma forma como seus novos tipos de projeto [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] contribuem para o modelo de automação. Se o processo é descrito na [fornecer automação a VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Locais onde você pode considerar como estender o modelo de automação do ambiente:  
  
- Projeto  
  
- Documento  
  
- Código  
  
- Build  
  
  Para obter mais informações sobre a automação, consulte [automação e extensibilidade do Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Este documento e os documentos que ela fornece links para ajudá-lo a tomar decisões sobre como você deve fornecer automação para o VSPackage.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Criar um suplemento](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
