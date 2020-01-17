---
title: O comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32c01401eda8fb1bbe2bdcfc2950a51b968e98b7
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114907"
---
# <a name="the-dsltexttransform-command"></a>O comando DslTextTransform
DslTextTransform. cmd é um script que chama TextTransform. exe e o executa com opções comuns. Você pode usar o DslTextTransformation. cmd para automatizar uma compilação noturna de seus projetos de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Para obter mais informações, consulte [gerando arquivos com o utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 O DslTextTransform. cmd está localizado no seguinte diretório:

 **\<caminho de instalação do SDK do Visual Studio > \VisualStudioIntegration\Tools\Bin**

 Você pode especificar os seguintes argumentos como entrada para DslTextTransform. cmd:

- O diretório de saída do projeto de modelo de domínio.

- O diretório de saída do projeto de definição de designer.

- O local do arquivo de modelo de texto.

  DslTextTransform. cmd processa o arquivo de modelo de texto especificado usando os processadores de diretiva padrão e os assemblies. Se você criar processadores de diretiva personalizados, poderá criar seu próprio arquivo em lotes que chama TextTransform. exe. Nesse arquivo em lotes, você pode especificar seus assemblies e os processadores de diretiva personalizada associados.
