---
title: O comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5f0eceeb4253460c17a52ebb8ec4082b9a743c70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963797"
---
# <a name="the-dsltexttransform-command"></a>O comando DslTextTransform
DslTextTransform.cmd é um script que chama TextTransform.exe e executa-o com opções comuns. Você pode usar DslTextTransformation.cmd para automatizar uma compilação noturna de seu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] projetos. Para obter mais informações, consulte [gerando arquivos com o utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd está localizado no seguinte diretório:

 **\<Caminho de instalação do SDK do Visual Studio > \VisualStudioIntegration\Tools\Bin**

 Você pode especificar os argumentos a seguir como entrada para DslTextTransform.cmd:

- O diretório de saída do projeto de modelo de domínio.

- O diretório de saída do projeto de definição de designer.

- O local do arquivo de modelo de texto.

  DslTextTransform.cmd processa o arquivo de modelo de texto especificado usando os processadores de diretriz padrão e assemblies. Se você criar processadores de diretriz personalizados, você pode criar seu próprio arquivo de lote que chama TextTransform.exe. Nesse arquivo em lotes, você pode especificar seus assemblies e os processadores de diretriz personalizados associados.