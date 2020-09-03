---
title: O comando DslTextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658457"
---
# <a name="the-dsltexttransform-command"></a>O comando DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform. cmd é um script que chama TextTransform.exe e o executa com opções comuns. Você pode usar o DslTextTransformation. cmd para automatizar uma compilação noturna de seus [!INCLUDE[dsl](../includes/dsl-md.md)] projetos. Para obter mais informações, consulte [gerando arquivos com o utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 O DslTextTransform. cmd está localizado no seguinte diretório:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Você pode especificar os seguintes argumentos como entrada para DslTextTransform. cmd:

- O diretório de saída do projeto de modelo de domínio.

- O diretório de saída do projeto de definição de designer.

- O local do arquivo de modelo de texto.

  DslTextTransform. cmd processa o arquivo de modelo de texto especificado usando os processadores de diretiva padrão e os assemblies. Se você criar processadores de diretiva personalizados, poderá criar seu próprio arquivo em lotes que chama TextTransform.exe. Nesse arquivo em lotes, você pode especificar seus assemblies e os processadores de diretiva personalizada associados.
