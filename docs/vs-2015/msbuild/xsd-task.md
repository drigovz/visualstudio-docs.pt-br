---
title: Tarefa XSD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2c8e38959e9835ee26f283c59128749239178307
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778718"
---
# <a name="xsd-task"></a>Tarefa XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Encapsula a ferramenta de definição de esquema XML (xsd.exe), a qual gera arquivos de classe ou de esquema com base em uma origem.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa **XSD**.  
  
-   **AdditionalOptions**  
  
     Parâmetro **String** opcional.  
  
     Uma lista de opções, conforme especificado na linha de comando. Por exemplo, "*/option1 /option2 /option#*". Use esse parâmetro para especificar opções não representadas por nenhum outro parâmetro da tarefa **XSD**.  
  
-   **GenerateFromSchema**  
  
     Parâmetro **String** opcional.  
  
     Especifica os tipos gerados com base no esquema especificado.  
  
     Especifique um dos valores a seguir, cada um dos quais correspondente a uma opção XSD.  
  
    -   **classes** - **/classes**  
  
    -   **dataset** - **/dataset**  
  
-   **Linguagem**  
  
     Parâmetro **String** opcional.  
  
     Especifica a linguagem de programação a ser usada para o código gerado.  
  
     Escolha **CS** (C#, que é o padrão), **VB** (Visual Basic) ou **JS** (JScript). Você também pode especificar um nome totalmente qualificado para uma classe que implementa `System.CodeDom.Compiler.CodeDomProvider Class`  
  
-   **Namespace**  
  
     Parâmetro **String** opcional.  
  
     Especifica o namespace de tempo de execução para os tipos gerados.  
  
-   **Sources**  
  
     Parâmetro `ITaskItem[]` obrigatório.  
  
     Define uma matriz de itens de arquivo de origem do MSBuild que pode ser consumida e emitida por tarefas.  
  
-   **SuppressStartupBanner**  
  
     Parâmetro **Boolean** opcional.  
  
     Se `true`, impedirá a exibição da mensagem de direitos autorais e de número de versão quando a tarefa for iniciada.  
  
-   **TrackerLogDirectory**  
  
     Parâmetro **String** opcional.  
  
     Especifica o diretório do log de rastreamento.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
