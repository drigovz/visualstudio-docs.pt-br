---
title: O comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a303fc3ddb880402e3f998b2360122f6f056b757
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605940"
---
# <a name="the-dsltexttransform-command"></a>O comando DslTextTransform
DslTextTransform. cmd é um script que chama TextTransform. exe e o executa com opções comuns. Você pode usar o DslTextTransformation. cmd para automatizar uma compilação noturna de seus projetos de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Para obter mais informações, consulte [gerando arquivos com o utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 O DslTextTransform. cmd está localizado no seguinte diretório:

 **Caminho de instalação do \<Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**

 Você pode especificar os seguintes argumentos como entrada para DslTextTransform. cmd:

- O diretório de saída do projeto de modelo de domínio.

- O diretório de saída do projeto de definição de designer.

- O local do arquivo de modelo de texto.

  DslTextTransform. cmd processa o arquivo de modelo de texto especificado usando os processadores de diretiva padrão e os assemblies. Se você criar processadores de diretiva personalizados, poderá criar seu próprio arquivo em lotes que chama TextTransform. exe. Nesse arquivo em lotes, você pode especificar seus assemblies e os processadores de diretiva personalizada associados.