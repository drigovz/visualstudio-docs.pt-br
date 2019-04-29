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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 220ceab29cb2b9bc1b117a98326d22c3c546a162
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548487"
---
# <a name="the-dsltexttransform-command"></a>O comando DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd é um script que chama TextTransform.exe e executa-o com opções comuns. Você pode usar DslTextTransformation.cmd para automatizar uma compilação noturna de seu [!INCLUDE[dsl](../includes/dsl-md.md)] projetos. Para obter mais informações, consulte [gerando arquivos com o utilitário TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd está localizado no seguinte diretório:  
  
 **\<Caminho de instalação do SDK do Visual Studio > \VisualStudioIntegration\Tools\Bin**  
  
 Você pode especificar os argumentos a seguir como entrada para DslTextTransform.cmd:  
  
- O diretório de saída do projeto de modelo de domínio.  
  
- O diretório de saída do projeto de definição de designer.  
  
- O local do arquivo de modelo de texto.  
  
  DslTextTransform.cmd processa o arquivo de modelo de texto especificado usando os processadores de diretriz padrão e assemblies. Se você criar processadores de diretriz personalizados, você pode criar seu próprio arquivo de lote que chama TextTransform.exe. Nesse arquivo em lotes, você pode especificar seus assemblies e os processadores de diretriz personalizados associados.
