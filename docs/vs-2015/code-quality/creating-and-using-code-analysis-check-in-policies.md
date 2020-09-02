---
title: Criando e usando políticas de check-in de análise de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667706"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Criando e usando políticas de check-in de análise do código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao usar o Controle de Versão do Team Foundation (TFVC), você pode criar uma política de check-in de análise de código para os projetos de código .NET Framework e nativo (C/C++) em um projeto de equipe. Você pode usar a política de check-in de análise de código para controlar e melhorar a qualidade do código que é verificado na base de código.

 A política passa quando a compilação local está atualizada e a análise de código foi executada nos arquivos de origem mais recentes. No mínimo, as regras de análise de código que estão habilitadas no projeto de código devem conter as mesmas regras que as definidas na política de check-in do projeto de equipe. As regras que foram especificadas como erros nas configurações do projeto de equipe também devem ser especificadas como erros no projeto de código

> [!IMPORTANT]
> As políticas de check-in de análise de código não podem ser aplicadas a projetos de site. Eles podem ser aplicados a projetos de aplicativos Web.

 Você cria políticas de check-in de análise de código usando as configurações do projeto de equipe do [!INCLUDE[esprscc](../includes/esprscc-md.md)] . As políticas de check-in são especificadas e impostas para um projeto de equipe, mas as execuções de análise de código são configuradas e executadas para projetos de código individuais em computadores de desenvolvimento locais. Esta seção descreve como especificar políticas de check-in de análise de código para um projeto de equipe e como implementar políticas personalizadas de análise de código para código gerenciado.

## <a name="in-this-section"></a>Nesta seção
 [Como: criar ou atualizar políticas de check-in de análise de código padrão](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md) Explica as etapas que você usa para definir e modificar uma política de análise de código para um projeto de equipe.

 [Implementando políticas de check-in personalizadas para código gerenciado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md) Explica as etapas que você usa para criar um conjunto de regras personalizadas para a política de check-in de um projeto de equipe e sincronizar os projetos de código do projeto de equipe com a política de check-in.

 [Compatibilidade de versão para políticas de check-in de análise de código](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md) Explica os problemas de compatibilidade de verificação de análise de código entre versões do [!INCLUDE[vstsLong](../includes/vstslong-md.md)] .

 [Como: personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md) Explica como adicionar palavras e tokens ao dicionário referenciado nas regras de nomenclatura da análise de código.

## <a name="related-sections"></a>Seções relacionadas
 [Definição e aplicação de restrições de qualidade](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [Melhorando a qualidade do código com políticas de check-in do projeto de equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
