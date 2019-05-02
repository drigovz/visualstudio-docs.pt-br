---
title: Criando e usando políticas do Check-In de análise de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 274aa497e004ddafee9a56b028f3001bb8deb630
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437065"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Criando e usando políticas de check-in de análise do código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você usa o controle de versão do Team Foundation (TFVC), você pode criar uma política de check-in do análise código para o .NET Framework e projetos de código nativos (C/C++) em um projeto de equipe. Você pode usar a política de check-in do análise código para controlar e melhorar a qualidade do código que é verificado na base de código.  
  
 A política é aprovada quando a compilação local está atualizada e análise de código foi executada nos arquivos de origem mais recentes. No mínimo, as regras de análise de código que estão habilitadas no código do projeto devem conter as mesmas regras que aquelas que são definidos na política de check-in do projeto team. As regras que foram especificadas como erros nas configurações do projeto de equipe também devem ser especificadas como erros no código do projeto  
  
> [!IMPORTANT]
> Políticas do check-in de análise de código não podem ser aplicadas a projetos de site da web. Elas podem ser aplicadas a projetos de aplicativos web.  
  
 Criar código de políticas de check-in de análise usando as configurações de projeto de equipe do [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Políticas de check-in são especificadas e impostas para um projeto de equipe, mas as execuções de análise de código são configuradas e executadas para projetos de código individuais nos computadores de desenvolvimento local. Esta seção descreve como especificar políticas análise de código check-in para um projeto de equipe e como implementar políticas de análise de código personalizado para código gerenciado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Criar ou atualizar as políticas do Check-in de análise de código padrão](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Explica as etapas que você pode usar para definir e modificar uma política de análise de código para um projeto de equipe.  
  
 [Implementando políticas de check-in personalizadas para código gerenciado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Explica as etapas que você usa para criar uma regra personalizada definida para a política de check-in de um projeto de equipe e sincronizar os projetos de código do projeto de equipe com a política de check-in.  
  
 [Compatibilidade da versão para políticas de check-in de análise de código](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Explica os problemas de compatibilidade de check-in de análise de código entre versões do [!INCLUDE[vstsLong](../includes/vstslong-md.md)].  
  
 [Como: Personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Explica como adicionar palavras e tokens para o dicionário que é referenciado em regras de nomenclatura de análise de código.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Definir e impor restrições de qualidade](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Melhorando a qualidade do código com políticas de check-in do projeto de equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
