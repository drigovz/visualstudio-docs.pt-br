---
title: Os VSPackages e a estrutura de pacote gerenciado | Microsoft Docs
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
ms.openlocfilehash: 7f8d5da0d246cb6b0faa8b424f8039697686cd2a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925525"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Os VSPackages e a estrutura de pacote gerenciado
Você pode reduzir o tempo de desenvolvimento com a criação de um VSPackage com o pacote gerenciado classes do framework (MPF) em vez de por meio de classes de interoperabilidade COM.  
  
 Há duas maneiras de criar um VSPackage gerenciado:  
  
-   Use o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelo de projeto de pacote  
  
     Para obter mais informações, confira [Passo a passo: Criação de um comando de Menu usando o modelo de pacote do Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
-   Compilar o VSPackage sem o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelo de projeto de pacote  
  
     Por exemplo, você pode copiar um exemplo de VSPackage e alterar os GUIDs e os nomes. Você pode encontrar exemplos na seção VSX [Galeria de códigos](http://code.msdn.microsoft.com/vsx/).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Classes da estrutura de pacote gerenciado](../misc/managed-package-framework-classes.md)  
 Descreve e lista os namespaces de classe MPF e arquivos DLL.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Passo a passo: Criação de um comando de Menu usando o modelo de pacote do Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Explica como criar um VSPackage gerenciado.  
  
 [VSPackages gerenciados](../misc/managed-vspackages.md)  
 Apresenta os aspectos de VSPackages que se aplicam ao código gerenciado.