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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699498"
---
# <a name="automation-model-overview"></a>Visão geral do modelo de automação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O modelo de automação consiste em um conjunto de objetos em que é possível escrever um suplemento ou uma extensão do Visual Studio. Um suplemento é um aplicativo que pode manipular o ambiente do Visual Studio e automatizar tarefas comuns. Uma extensão do Visual Studio pode criar componentes personalizados do Visual Studio ou adicionar à funcionalidade de componentes padrão, como o editor de texto.  
  
## <a name="objects-in-the-automation-model"></a>Objetos no modelo de automação  
 O modelo de automação consiste em grupos de objetos relacionados que controlam as principais facetas do ambiente comum. Veja a seguir um diagrama que mostra o amplo conjunto de objetos que compõem o modelo de automação.  
  
 ![Gráfico de objeto de automação do Visual Studio](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Objetos de automação do Visual Studio  
  
 Para obter mais informações, consulte [estendendo o ambiente do Visual Studio](https://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 O ambiente fornece um modelo para diferentes áreas funcionais. Por exemplo, há um modelo de código para vários elementos que você pode encontrar no código. Há um modelo de documento para vários elementos de documento. Uma área, a área do projeto, é de interesse particular para os provedores de VSPackage. Você provavelmente desejará que seus novos tipos de projeto contribuam para o modelo de automação da mesma forma que [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] e [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] contribuem para o modelo de automação. Esse processo é descrito em [fornecendo automação para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Locais onde você pode considerar a extensão do modelo de automação do ambiente:  
  
- Projeto  
  
- Document  
  
- Código  
  
- Build  
  
  Para obter mais informações sobre automação, consulte [automação e extensibilidade para o Visual Studio](https://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6). Este documento e os documentos aos quais ele fornece links, ajudam você a tomar decisões sobre como você deve fornecer automação para seu VSPackage.  
  
## <a name="see-also"></a>Consulte Também  
 [Como criar um suplemento](https://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
