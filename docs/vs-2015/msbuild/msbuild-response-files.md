---
title: Arquivos de resposta do MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1ce11edac37368b9c4993a87a8c2b3e734b7862
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649609"
---
# <a name="msbuild-response-files"></a>Arquivos de resposta do MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Arquivos de resposta (.rsp) são arquivos de texto que contêm as opções de linha de comando MSBuild.exe. Cada opção pode estar em uma linha separada ou todas as opções podem estar em uma linha. As linhas de comentários são precedidas por um símbolo **#**. A opção **@** é usada para passar a outro arquivo de resposta para o MSBuild.exe.  
  
 O arquivo de resposta automática é um arquivo .rsp especial que o MSBuild.exe usa automaticamente ao criar um projeto. Esse arquivo, o MSBuild.rsp, deve estar no mesmo diretório que MSBuild.exe, caso contrário, ele não será localizado. Você pode editar esse arquivo para especificar opções de linha de comando padrão para MSBuild.exe. Por exemplo, caso use o mesmo agente de log sempre que compilar um projeto, você pode adicionar a opção **/logger** para MSBuild.rsp, e o MSBuild.exe usará o agente de log sempre que um projeto for compilado.  
  
## <a name="see-also"></a>Consulte também  
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)
