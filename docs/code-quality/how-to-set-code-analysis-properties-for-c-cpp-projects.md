---
title: 'Como: Definir propriedades de análise de código para projetos C/C++'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 80dfd4901fdaaeff064ba18d80bfe3f69e08116c
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53739880"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Como: Definir propriedades de análise de código para projetos C/C++
Você pode configurar as regras que a ferramenta de análise de código usa para analisar o código em cada configuração de seu projeto. Além disso, você pode direcionar a análise de código para suprimir avisos do código que foi gerado e adicionado ao seu projeto por uma ferramenta de terceiros.

## <a name="code-analysis-property-page"></a>Página de propriedades de análise de código
 O **análise de código** página de propriedades contém todas as definições de configuração de análise de código para um projeto. Para abrir a página de propriedades de análise de código para um projeto no **Gerenciador de soluções**, clique com botão direito no projeto e, em seguida, clique em **propriedades**. Em seguida, expanda **propriedades de configuração** e selecione o **análise de código** guia.

## <a name="project-configuration-and-platform"></a>Plataforma e configuração de projeto
 O **Configuration** lista e **plataforma** lista permite que você aplique as configurações de análise de código diferente para combinações de configuração e plataforma de projeto diferente. Por exemplo, você pode direcionar compilações de análise de código para aplicar um conjunto de regras ao seu projeto para depuração e cria um conjunto diferente de versão.

## <a name="enabling-code-analysis"></a>Habilitar análise de código
 Você pode decidir se deseja habilitar a análise de código para seu projeto, selecionando **habilitar o código de análise para C/C++ no Build**. Em combinação com o **configuração** lista, você poderia, por exemplo, decidir desativar análise de código para compilações de depuração e habilite-o para a versão se baseia.

 Se seu projeto contém o código gerenciado, você pode decidir se deseja habilitar ou desabilitar análise de código, selecionando **habilitar a análise de código no Build**.

 Análise de código foi projetada para ajudá-lo a melhorar a qualidade do seu código e evitar armadilhas comuns. Portanto, considere cuidadosamente se deseja desabilitar a análise de código. É melhor desabilitar conjuntos de regra ou regras individuais que você não deseja aplicadas ao seu projeto.

## <a name="generated-code"></a>Código gerado
 Os desenvolvedores frequentemente usam ferramentas para ajudar a desenvolver aplicativos rapidamente. Essas ferramentas podem gerar código que é adicionado ao projeto. Você talvez queira ver as violações de regra que detecta de análise de código no código gerado. No entanto, talvez você não queira vê-los se você não deseja manter o código.

 O **Suprimir resultados do código gerado pelo** caixa de seleção a **geral** página de propriedades permite que você escolha se você deseja ver avisos da análise de código do código gerenciado que é gerado por uma ferramenta de terceiros .

## <a name="rule-sets"></a>Conjuntos de regras
 Se seu projeto contém o código gerenciado, você pode selecionar as regras para aplicar em uma análise de código, selecionando uma conjunto de regras do **executar este conjunto de regras** lista.

## <a name="see-also"></a>Consulte também
 [Analisando a qualidade do código gerenciado](../code-quality/code-analysis-for-managed-code-overview.md) [análise de código para avisos do C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)