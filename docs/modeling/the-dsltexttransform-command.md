---
title: O comando DslTextTransform
description: Saiba que o DslTextTransform. cmd é um script que chama TextTransform.exe e o executa com opções comuns.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74f87f735f5ad6864082046327bc852d5d43fdb6
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362711"
---
# <a name="the-dsltexttransform-command"></a>O comando DslTextTransform
DslTextTransform. cmd é um script que chama TextTransform.exe e o executa com opções comuns. Você pode usar o DslTextTransformation. cmd para automatizar uma compilação noturna de seus [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projetos. Para obter mais informações, consulte [gerando arquivos com o utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 O DslTextTransform. cmd está localizado no seguinte diretório:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Você pode especificar os seguintes argumentos como entrada para DslTextTransform. cmd:

- O diretório de saída do projeto de modelo de domínio.

- O diretório de saída do projeto de definição de designer.

- O local do arquivo de modelo de texto.

  DslTextTransform. cmd processa o arquivo de modelo de texto especificado usando os processadores de diretiva padrão e os assemblies. Se você criar processadores de diretiva personalizados, poderá criar seu próprio arquivo em lotes que chama TextTransform.exe. Nesse arquivo em lotes, você pode especificar seus assemblies e os processadores de diretiva personalizada associados.
