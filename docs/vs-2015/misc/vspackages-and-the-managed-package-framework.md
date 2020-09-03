---
title: VSPackages e a estrutura de pacote gerenciada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 84fb41bfc80415535ca41d6b1a8c9dcf47124c7a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298231"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Os VSPackages e a estrutura de pacote gerenciado
Você pode reduzir o tempo de desenvolvimento criando um VSPackage com as classes do MPF (Managed Package Framework) em vez de usar classes de interoperabilidade COM.  
  
 Há duas maneiras de criar um VSPackage gerenciado:  
  
- Usar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelo de projeto de pacote  
  
     Para obter mais informações, consulte [Walkthrough: Criando um comando de menu usando o modelo de pacote do Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Criar seu VSPackage sem o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelo de projeto de pacote  
  
     Por exemplo, você pode copiar um exemplo de VSPackage e alterar os GUIDs e os nomes. 
  
## <a name="in-this-section"></a>Nesta seção  
 [Classes da estrutura de pacote gerenciado](../misc/managed-package-framework-classes.md)  
 Descreve e lista os namespaces e arquivos DLL da classe MPF.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Walkthrough: Criando um comando de menu usando o modelo de pacote do Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Explica como criar um VSPackage gerenciado.  
  
 [VSPackages gerenciados](../misc/managed-vspackages.md)  
 Apresenta aspectos de VSPackages que se aplicam ao código gerenciado.