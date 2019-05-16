---
title: Erros do aplicativo de análise do código
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1af00ebc2f6fdc1bc32a5a6784b88068d4e3ffb2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693379"
---
# <a name="code-analysis-application-errors"></a>Erros do aplicativo de análise do código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Esta seção é uma referência das mensagens de erro que são gerados pela ferramenta de análise de código gerenciado. Para obter ajuda para uma mensagem de erro específica, digite o número de erro na **procure** caixa no índice.

## <a name="in-this-section"></a>Nesta seção

|||
|-|-|
|[CA0001](ca0001.md)|Uma exceção foi gerada dentro da ferramenta de análise de código gerenciado que não indica uma condição de erro esperado.|
|[CA0051](ca0051.md)|Nenhuma regra foi selecionada.|
|[CA0052](ca0052.md)|Nenhum destino foi selecionado para analisar.|
|[CA0053](ca0053.md)|Não foi possível carregar o assembly de regras.|
|[CA0054](ca0054.md)|Um assembly de regra personalizada tem os recursos XML inválidos.|
|[CA0055](ca0055.md)|Não foi possível carregar o arquivo:\<caminho >|
|[CA0056](ca0056.md)|Um arquivo de projeto tem uma versão incorreta do que a ferramenta de análise.|
|[CA0057](ca0057.md)|Violações não podem ser mapeadas para o conjunto atual de destinos e as regras.|
|[CA0058](ca0058.md)|Não é possível carregar assemblies referenciados.|
|[CA0059](ca0059.md)|Erro de opção de linha de comando.|
|[CA0060](ca0060.md)|Não é possível carregar assemblies referenciados indiretamente.|
|[CA0061](ca0061.md)|A regra '*RuleId*' não pôde ser encontrado.|
|[CA0062](ca0062.md)|A regra '*RuleId*'referenciada no conjunto de regras'*RuleSetName*' não pôde ser encontrado.|
|[CA0063](ca0063.md)|Falha ao carregar o arquivo de conjunto de regras ou um de seus arquivos de conjunto de regras dependentes.|
|[CA0064](ca0064.md)|Nenhuma análise foi executada porque o conjunto de regras especificado não contém quaisquer regras FxCop.|
|[CA0065](ca0065.md)|Construção de metadados sem suporte: Tipo '*TypeName*'contém uma propriedade e um campo com o mesmo nome'*PropertyFieldName*'|
|[CA0066](ca0066.md)|O valor '*VersionID*' fornecido para o **/targetframeworkversion** não é uma versão reconhecida.|
|[CA0067](ca0067.md)|Diretório não encontrado.|
|[CA0068](ca0068.md)|Depurar informações não foi possível encontrar assembly de destino *'AssemblyName'*.|
|[CA0069](ca0069.md)|Usando a plataforma alternativa. *FrameworkVersion1* não pôde ser encontrado. Usando o *FrameworkVersion2* em vez disso. Para obter melhores resultados de análise Verifique se que o .NET Framework correto está instalado.|
|[CA0070](ca0070.md)|Não é possível carregar o assembly ou tipo devido a permissões de segurança.|
|[CA0501](ca0501.md)|Não é possível ler o relatório de saída.|
|[CA0502](ca0502.md)|Idioma sem suporte.|
|[CA0503](ca0503.md)|A propriedade foi preterida. Use a propriedade superceding|
|[CA0504](ca0504.md)|Diretório de regra foi ignorado porque não existe|
|[CA0505](ca0505.md)|A propriedade foi preterida. Use a propriedade superceding|
|[Erros de FxCopCmd](fxcopcmd-errors.md)|Erros de análise de código gerenciado.|

## <a name="related-sections"></a>Seções relacionadas

- [Diretrizes para escrever código seguro](https://msdn.microsoft.com/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [Analisando a qualidade do código gerenciado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Recursos para solucionar problemas de erros em ferramentas de gerenciamento de ciclo de vida do aplicativo](https://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)